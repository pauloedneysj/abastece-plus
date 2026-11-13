# ⛽ Abastece+

**Compare gasolina e etanol e descubra o abastecimento mais econômico para o seu veículo.**

O **Abastece+** é um simulador de combustível gratuito, responsivo e desenvolvido com HTML, CSS e JavaScript. Ele calcula o custo por quilômetro, a autonomia estimada e os litros abastecidos com base nos preços e no consumo do veículo — sem exigir cadastro ou conexão com a internet.

**Versão:** `1.1.0` · **Autor:** Paulo Edney

## ✨ Funcionalidades

- **Comparação de combustíveis:** gasolina e etanol, com recomendação baseada no custo por quilômetro.
- **Abastecimento por orçamento:** simule R$ 100, R$ 150, R$ 200 ou um valor personalizado.
- **Tanque cheio:** calcule quanto custa completar a capacidade cadastrada (partindo de tanque vazio).
- **Autonomia estimada:** veja a distância aproximada para cidade, estrada ou percurso misto.
- **Mistura de combustíveis:** ajuste a proporção entre gasolina e etanol e compare estimativas.
- **Consumo personalizável:** informe as médias reais de km/l do seu carro para obter resultados mais próximos da sua rotina.
- **Seleção de veículos:** catálogo preparado para receber novos modelos por meio de um dropdown.
- **Interface responsiva:** adaptada para celular e computador, com funcionamento offline.

## 🚙 Veículo inicial

O catálogo inclui, por padrão, o **Volkswagen T-Cross 2024 1.0 TSI (200 TSI)**, com tanque de referência de **52 litros**. Preços e médias de consumo podem ser ajustados na interface. Os dados de consumo são estimativas e podem variar conforme as condições de uso.

## 🚀 Como executar

### Versão em arquivo único

Abra `abastece-plus-v1.1.0.html` no navegador. O arquivo reúne HTML, CSS e JavaScript e funciona offline.

### Versão com código-fonte organizado

Na estrutura de desenvolvimento, abra `index.html` no navegador, mantendo as pastas `css/` e `js/` no mesmo diretório. Não é necessário instalar dependências para usar o simulador.

## 🗂️ Estrutura do projeto

Na versão organizada do código-fonte:

```text
abastece-/
├── index.html                  # Página principal
├── css/
│   └── styles.css              # Estilos e responsividade
├── js/
│   ├── config.js               # Metadados e catálogo de veículos
│   ├── calculator.js           # Lógica dos cálculos
│   └── app.js                  # Interações e atualização da interface
├── scripts/
│   └── build.py                # Geração do HTML único
├── tests/
│   └── calculator.test.js      # Testes automatizados
├── .github/
│   └── workflows/
│       └── deploy.yml          # Testes e deploy no GitHub Pages
├── CHANGELOG.md               # Histórico de versões
└── README.md
```

> **Nota:** se você ainda colocou somente o arquivo `abastece-plus-v1.1.0.html` no repositório, os diretórios acima são a estrutura da **versão organizada**, disponível separadamente, e só aparecerão no GitHub após você adicioná-los.

## ➕ Como cadastrar novos veículos

Na versão organizada, cadastre os novos modelos no catálogo `VEHICLES`, em `js/config.js`. Cada veículo possui um identificador único, marca, modelo, ano, versão, capacidade do tanque e médias de consumo por combustível e tipo de percurso.

Exemplo **ilustrativo** (valores fictícios, não usar como especificação de um carro real):

```js
{
  id: 'marca-modelo-2027-1-0',
  brand: 'Marca',
  model: 'Modelo',
  year: 2027,
  variant: '1.0 Flex',
  tankLiters: 45,
  fuelType: 'flex',
  consumption: {
    gasoline: { city: 12, road: 14 },
    ethanol: { city: 8, road: 10 }
  },
  consumptionNote: 'Informar origem dos dados.'
}
```

A interface passa a listar os veículos cadastrados, sem necessidade de reescrever o cálculo. Antes de cadastrar um veículo real, valide os dados no manual do proprietário ou no PBE Veicular/Inmetro.

## 🧮 Como funciona a comparação

O cálculo central considera o **custo para percorrer 100 km**:

```text
Custo por 100 km = (preço por litro ÷ consumo em km/l) × 100
```

Quanto menor o custo, mais econômico é o combustível **nas condições informadas**. A autonomia corresponde aos litros calculados multiplicados pelo consumo estimado. Para percursos mistos, a versão atual considera 60% da distância em cidade e 40% em estrada.

A simulação de mistura usa uma aproximação do rendimento por proporção de volume; não representa necessariamente o comportamento real do motor. O consumo efetivo depende de trânsito, ar-condicionado, relevo, carga e estilo de condução.

## 🧪 Testes e build

Na versão organizada, com **Node.js 18+** e **Python 3** disponíveis:

```bash
node --test tests/calculator.test.js
python3 scripts/build.py
```

O build gera `dist/abastece-plus.html`, que pode ser distribuído como um arquivo único.

## 🌐 Publicação no GitHub Pages

O workflow `.github/workflows/deploy.yml` da versão organizada executa os testes, gera o HTML standalone e publica no GitHub Pages após um push na branch `main`.

1. Envie todos os arquivos da versão organizada para o repositório.
2. No GitHub, entre em **Settings → Pages**.
3. Em **Build and deployment → Source**, selecione **GitHub Actions**.
4. Acompanhe a execução pela aba **Actions**.

Após um deploy bem-sucedido, o endereço esperado deste repositório é:

**https://pauloedneysj.github.io/abastece-/**

## 🏷️ Versionamento

O projeto segue o modelo **Semantic Versioning** (`MAJOR.MINOR.PATCH`):

- **MAJOR:** mudanças incompatíveis.
- **MINOR:** novas funcionalidades compatíveis.
- **PATCH:** correções e pequenos ajustes.

A versão em uso é **1.1.0**. As mudanças futuras podem ser documentadas em `CHANGELOG.md`.

## 👨‍💻 Autor

**Paulo Edney**  
GitHub: [@pauloedneysj](https://github.com/pauloedneysj)

---

*Abastece+ é um simulador informativo. Os resultados são estimativas, não uma garantia de consumo real.*
