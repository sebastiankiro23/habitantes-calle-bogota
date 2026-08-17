# Habitabilidad en Calle en Bogotá: Causas y Proyección 2024-2048

Proyecto de análisis de datos que estudia el fenómeno de la habitabilidad en calle en Bogotá, Colombia: sus causas principales, patrones de consumo de sustancias, distribución geográfica por localidad, y una proyección estadística a 24 años del total de personas en esta situación.

## 📊 Dashboard

El dashboard interactivo se construyó en Power BI e incluye 5 páginas:
- **Resumen**: KPIs clave (totales, variación, causa principal, demografía)
- **Crecimiento y Proyección**: serie histórica 1997-2024 y dos escenarios de proyección a 2048
- **Causas**: comparación de las causas de inicio y persistencia en calle, 2017 vs 2024
- **Consumo de Sustancias**: ranking de sustancias más consumidas
- **Localidades**: mapa geográfico de concentración por localidad de Bogotá

## 🗂️ Fuentes de datos

Todos los datos provienen de fuentes oficiales públicas:

- **Censo de Habitantes de Calle (CHC) 2017** — DANE. [Microdatos](https://microdatos.dane.gov.co/index.php/catalog/548/)
- **Censo de Habitantes de Calle (CHC) 2024** — Alcaldía de Bogotá / Secretaría Distrital de Integración Social. [Datos Abiertos Bogotá](https://datosabiertos.bogota.gov.co/dataset/bases-de-microdatos-del-viii-censo-de-ciudadanos-habitantes-de-calle-2024)
- **Serie histórica 1997-2024** — Ficha Metodológica CHC 2024, Secretaría Distrital de Integración Social

> **Nota metodológica:** se descartó un archivo inicialmente identificado como "CHC 2021" tras confirmar que correspondía a otros municipios de Colombia, no a Bogotá.

## 🛠️ Estructura del proyecto

```
├── notebooks/              # Notebooks de Jupyter con la limpieza de datos
│   ├── limpieza_2017.ipynb
│   └── limpieza_2024.ipynb
├── data_clean/              # Datos limpios, listos para Power BI
│   ├── CHC_2017_limpio.csv
│   ├── CHC_2024_limpio.csv
│   ├── historico_1997_2024.csv
│   ├── proyeccion_2007_2048.csv
│   ├── consumo_2017.csv
│   ├── consumo_2024.csv
│   ├── mapa_localidades_2024.csv
│   └── kpis_wide.csv
├── dashboard/                # Archivo de Power BI
│   └── HabitantesCalle_Bogota.pbix
├── .gitignore
└── README.md
```

> Los datos crudos originales (`Data.raw/`) no se incluyen en este repositorio por su peso; pueden descargarse directamente de las fuentes oficiales enlazadas arriba.

## 🔍 Metodología de la proyección

Se ajustaron dos modelos sobre la serie histórica 2007-2024 (4 puntos: 2007, 2011, 2017, 2024):

| Modelo | R² | Proyección 2048 |
|---|---|---|
| Regresión lineal | 0.8248 | 13.004 personas |
| Regresión polinomial (grado 2) | 0.8418 | 9.865 personas |

Dado que la diferencia de ajuste (R²) entre ambos modelos es mínima, se presentan **ambos escenarios** en el dashboard en lugar de una sola cifra, para reflejar honestamente la incertidumbre de proyectar 24 años con solo 4 puntos de datos históricos.

## 📌 Hallazgos principales

- El total de habitantes de calle en Bogotá aumentó de 9.538 (2017) a 10.478 (2024), un incremento del 9,9%.
- La causa principal de inicio cambió entre censos: en 2017 predominaba el **consumo de sustancias psicoactivas** (28,6%); en 2024 predominan los **conflictos de convivencia o violencia familiar** (32-38,9%).
- El **basuco** y el **cigarrillo** son las sustancias de consumo más frecuente entre la población censada.
- **Los Mártires** y **Santa Fe** concentran la mayor cantidad de casos, aunque su participación relativa disminuyó frente a censos anteriores, sugiriendo una dispersión hacia otras localidades.

## 🧰 Herramientas utilizadas

- Python (pandas, numpy, matplotlib)
- Jupyter Notebook
- Power BI Desktop

## ✍️ Autor

Sebastián — [agrega aquí tu nombre completo o usuario si quieres]

---
*Este proyecto tiene fines educativos y de análisis de datos abiertos. No sustituye los reportes oficiales de la Secretaría Distrital de Integración Social ni del DANE.*
