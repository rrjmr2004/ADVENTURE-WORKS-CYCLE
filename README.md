# ADVENTURE-WORKS-CYCLE
# 🚴‍♂️ Análisis de Datos - **Adventure Works Cycles** con Power BI

> **Visualizando el rendimiento de AWC con Power BI**  
> 📊 Proyecto desarrollado en el marco del Bootcamp de Data Analytics - Cohorte DAFT-12

---

## 👤 Autor

- **Nombre:** Roman Matheus  
- 📧 **Correo:** [roman.matheus.uni@gmail.com](mailto:roman.matheus.uni@gmail.com)  
- 📆 **Fecha de entrega:** 20/03/2025  

---

## 🏢 Descripción del Proyecto

Adventure Works Cycles (AWC) es una empresa multinacional que fabrica y distribuye bicicletas, piezas y accesorios en mercados de América del Norte, Europa y Asia.  
Con más de **500 empleados**, la empresa busca mejorar su toma de decisiones mediante un informe de **Power BI** que analice:

- 🛒 Ventas
- 💰 Costos
- 📈 Rentabilidad

Este tablero facilita la comprensión de los factores clave del negocio para tomar **decisiones estratégicas basadas en datos**.

---

## ⚙️ Desarrollo del Proyecto

### 1. 🔌 Conexión y Transformación de Datos (Power Query)

Se conectaron las siguientes tablas de `AdventureWorksDW2019`:

- `DimCustomer` (Clientes)  
- `DimProduct` (Productos)  
- `DimDate` (Fechas)  
- `FactInternetSales` (Ventas por Internet)  

**Transformaciones clave:**

- 📅 *Normalización de fechas:* formatos consistentes, columnas "Mes" y "Trimestre".
- 🧹 *Limpieza de clientes:* se eliminaron duplicados e inconsistencias.
- 🧱 *Optimización de ventas:* eliminación de columnas innecesarias, creación de PK `IdInternetSales`.

### 2. 🔗 Modelado de Datos

Relaciones creadas:

- `FactInternetSales[CustomerKey]` 🔁 `DimCustomer[CustomerKey]`  
- `FactInternetSales[ProductKey]` 🔁 `DimProduct[ProductKey]`  
- `FactInternetSales[OrderDateKey]` 🔁 `DimDate[DateKey]`  

---

## 🧮 Medidas DAX Principales

| 📌 Medida | 🔍 Descripción |
|----------|----------------|
| **Artículos Vendidos** | `SUM(FactInternetSales[OrderQuantity])` |
| **Clientes Únicos** | `DISTINCTCOUNT(DimCustomer[CustomerKey])` |
| **Cantidad de Operaciones** | `COUNT(FactInternetSales[IdInternetSales])` |
| **COGS** (Costo de Productos) | `SUM(FactInternetSales[TotalProductCost])` |
| **COGS + Envíos** | `SUMX(FactInternetSales, TotalProductCost + Freight)` |
| **Ingresos (Ventas)** | `SUM(FactInternetSales[SalesAmount])` |
| **Utilidad Bruta** | `Ingresos - COGS` |
| **Utilidad Neta** | `Ingresos - COGS - Impuestos - Envíos` |

### ⏱️ Medidas de Tiempo (vs. Año Anterior)

- **Ingresos LY**: `CALCULATE([Ingresos], SAMEPERIODLASTYEAR(...))`  
- **Utilidad Neta LY**: `CALCULATE([Utilidad Neta], SAMEPERIODLASTYEAR(...))`  
- **Artículos Vendidos LY**, **COGS LY**, etc.

### 📉 Medidas de Variación y Porcentuales

- **Variación Ingreso %**: `DIVIDE([Variación Ingreso], [Ingresos LY])`
- **COGS %**: `DIVIDE([COGS], [Ingresos])`
- **Margen Bruto %**: `DIVIDE([Utilidad Bruta], [Ingresos])`

---

## 🎛️ Parámetros y Segmentadores

- 🎚️ **Menú de Intervalos**: Rango dinámico para descuentos.  
- 📅 **Intervalos LY**: Comparación con el año anterior.

---

## 📄 Descripción de Páginas del Dashboard

### 📍 Página Principal
> Vista general del desempeño de la empresa

- KPIs de ingresos, utilidad, costos  
- Filtros por año, categoría y país  
- Gráficos de tendencias y análisis regional  

### 📈 Análisis de Ventas

- Matriz por cliente y categoría  
- Comparación de productos  
- Tendencias año a año  

### 💸 Costos y Rentabilidad

- Margen por producto  
- Relación COGS/Ingresos  
- Rentabilidad por trimestre  

### 🇺🇸 Dashboard USA

> Detalle por estado en EE.UU.

- KPIs regionales  
- Mapa interactivo  
- Comparación de estados  

### 🧾 Análisis de Rentabilidad

- Rentabilidad por estado  
- Relación ingresos/COGS  
- Análisis por categoría  

---

## 🔍 Principales Hallazgos (Insights)

1. 💰 **Altos ingresos, pero también altos costos (COGS)**
   - Ingresos: $9.39M | COGS: $5.49M (58%)  
   - Margen neto: **31.04%**

2. 🌎 **Rentabilidad desigual por estado**
   - Mejores: Kentucky, Montana, Missouri  
   - Peores: Mississippi, Massachusetts  

3. 👕 **Categoría más vendida: Ropa (61.14%)**

4. 📆 **Picos de ventas: Junio y Diciembre**

5. 🧪 **Rentabilidad variable por producto**
   - Algunos generan muchos ingresos pero baja utilidad

---

## 🧭 Recomendaciones Futuras

- 🔍 Analizar causas de baja rentabilidad por estado  
- 📅 Optimizar campañas en meses clave (junio/diciembre)  
- 🛠️ Ajustar precios en productos poco rentables  
- 🤖 Aplicar **Machine Learning** para predicción de demanda  
- 🗺️ Expandir hacia estados con baja participación  

---

## ✨ Conclusión

Este análisis con Power BI para AWC revela **áreas de mejora clave** en rentabilidad, distribución de costos y estacionalidad. El tablero permite tomar decisiones estratégicas con base en datos reales y estructurados.

---

## 🤔 Reflexión Personal

> Este proyecto ha sido una experiencia enriquecedora donde consolidé mis conocimientos en ETL, modelado de datos, visualización y DAX. Me permitió aplicar todo lo aprendido de forma práctica y orientada al negocio.

---

## 🧷 Recursos

📁 Dataset: [AdventureWorksDW2019](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure)  
🔗 Power BI: [Descargar Power BI Desktop](https://powerbi.microsoft.com/)  

---

## 🧠 Tecnologías Utilizadas

- 🟨 Power BI  
- 📊 DAX (Data Analysis Expressions)  
- 📁 Power Query  

---

## 📌 Licencia

Este proyecto es de uso académico y personal bajo la Licencia MIT.

---

