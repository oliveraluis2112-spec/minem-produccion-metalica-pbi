# Reporte Ejecutivo de Producción Metálica - MINEM (2021 - 2026)

**Autor:** Luis Enrique Olivera García  
**Rol:** Analista de Datos / Business Intelligence  

---

## Resumen Ejecutivo
El presente proyecto consiste en el desarrollo e implementación de una solución integral de inteligencia de negocios en Power BI para el análisis estratégico y monitoreo de la producción metálica en el Perú. La solución toma como origen de información los registros oficiales del Ministerio de Energía y Minas (MINEM) correspondientes al periodo 2021-2026.

El objetivo del reporte es proporcionar a ejecutivos y analistas del sector minero una herramienta interactiva de alto impacto para la evaluación de volúmenes de extracción, análisis de variaciones interanuales ($YoY$) y mensuales, caracterización de métodos de procesamiento, distribución geográfica regional y la concentración de mercado por titular minero.

---

## Módulos y Pestañas del Reporte

### 1. Dashboard (Overview Ejecutivo)
Vista principal diseñada para la supervisión macro de los indicadores de producción nacional.
* **Tarjetas KPI Consolidadas**: Indicadores de producción acumulada en Toneladas Métricas Finas (TMF) para Hierro (Fe), Cobre (Cu), Plata (Ag) y Oro (Au), comparados frente al mismo periodo del año anterior ($YoY$).
* **Tendencia Anual de Producción**: Evolución histórica del volumen total extraído durante el periodo 2021-2026.
* **Desglose por Proceso**: Distribución del volumen según el método extractivo utilizado (Flotación, Gravimetría y Lixiviación).
* **Participación por Mineral**: Porcentaje de representación de los principales minerales extraídos en el volumen total.
* **Distribución Geográfica y Representatividad**: Mapa regional interactivo por departamentos y matriz resumida con volúmenes por titular minero.

### 2. Analytics (Análisis de Variaciones)
Módulo analítico especializado en la evaluación de tendencias, estacionalidad y variaciones intermensuales.
* **Métricas Comparativas ($YoY$)**: Análisis de variación porcentual acumulada respecto al periodo anterior para cada mineral.
* **Curva de Producción Mes a Mes**: Comparativa temporal del volumen de producción actual frente al año anterior (*LY - Last Year*).
* **Gráfico Cascada de Variación Mensual**: Diagrama de variaciones porcentuales intermensuales para la identificación de desviaciones en la extracción.
* **Evolución por Mineral**: Desglose dinámico de la participación de los minerales a lo largo de la línea temporal.

### 3. Titulares (Análisis por Empresas Mineras)
Módulo orientado a la evaluación de la concentración del mercado y el desempeño individual de las empresas operadoras.
* **Indicadores Principales de Mercado**:
  * **Líder en Producción**: Identificación del principal productor nacional (ej. Shougang Hierro Perú S.A.A.).
  * **Mayor Crecimiento**: Empresa con mayor incremento porcentual en producción respecto al año anterior (ej. Sierra Minera Caraz S.A.C.).
  * **Titulares Activos**: Registro total de empresas mineras operativas bajo los filtros seleccionados.
* **Crecimiento y Variación por Titular**: Matriz de producción actual ($TMF$) frente a la producción del año anterior ($LY$) y su porcentaje de variación ($\% \text{Var } YoY$).
* **Evolución Mensual por Mineral**: Comportamiento temporal de las líneas de producción por tipo de mineral (Hierro, Cobre, Zinc, Plomo, Estaño).

---

## UI/UX y Sistema de Diseño (Bento Grid)

La interfaz visual fue concebida y maquetada previamente en Figma, aplicando el paradigma de diseño **Bento Grid** para lograr una densidad de información limpia, estructurada y modular.

### Especificaciones del Tema JSON (`src/theme-minem.json`)
El reporte implementa la paleta institucional `MINEM_Bento_Executive_Slate`:
* **Paleta de Colores**:
  * Fondo Primario / Encabezados: Dark Navy (`#0F172A`)
  * Acento Cobre / Destacados: Naranja Cobre (`#D97736`)
  * Fondo General de Lienzo: Slate Claro (`#F8FAFC`)
  * Indicadores de Variación: Verde (`#059669`), Azul (`#2563EB`), Ámbar (`#D97706`)
* **Propiedades Visuales**:
  * Tarjetas contenedoras con bordes de radio suave (`radius: 12`) y sombra personalizada (`dropShadow`).
  * Jerarquía tipográfica estandarizada en la familia `Segoe UI`.

---

## Arquitectura de Datos y Métodos

* **Fuente de Datos**: Registros abiertos oficiales del Ministerio de Energía y Minas (MINEM) del Perú (2021-2026).
* **Transformación y Limpieza (Power Query)**:
  * Desdinamización y estructuración de series temporales.
  * Normalización de métricas de volumen a Toneladas Métricas Finas (TMF).
  * Estandarización de catálogo de titulares mineros, unidades y departamentos.
* **Modelado y Consultas DAX**:
  * Lógica de inteligencia de tiempo (*Time Intelligence*) para comparativas interanuales ($YoY$) e intermensuales ($MoM$).
  * Medidas dinámicas para la identificación del líder de producción y titulares activos.

---

## Estructura del Repositorio

```text
minem-produccion-metalica-pbi/
│
├── assets/                      # Capturas de pantalla para documentación
│   ├── preview-dashboard.png    # Captura de la vista Dashboard
│   ├── preview-analytics.png    # Captura de la vista Analytics
│   └── preview-titulares.png    # Captura de la vista Titulares
│
├── figma/                       # Lienzos de diseño maquetados en Figma
│   ├── canvas-dashboard.png
│   ├── canvas-analytics.png
│   └── canvas-titulares.png
│
├── src/                         # Archivos fuente del reporte
│   ├── theme-minem.json         # Tema personalizado en formato JSON
│   └── produccion_metalica.pbix # Archivo de proyecto Power BI
│
├── data/                        # Datasets procesados
│   └── Produccion_Metalica_Consolidado_2021_2026.csv
│
└── README.md                    # Documentación técnica del proyecto
