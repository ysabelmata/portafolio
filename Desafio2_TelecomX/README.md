# Proyecto Telecom X - Parte 2: Análisis y Predicción de Churn

## Propósito del proyecto

El objetivo principal de este proyecto es **predecir el churn (cancelación) de clientes** de la empresa ficticia Telecom X, utilizando datos históricos de clientes y sus características. Se busca identificar patrones y variables clave que influyen en la cancelación para diseñar estrategias de retención efectivas.

---

## Estructura del proyecto

```
TelecomX_Parte2/
│
├── data/
│   └── telecomx_clean.csv       # Datos tratados y limpios
│
├── notebooks/
│   └── TelecomX_Parte2.ipynb    # Cuaderno principal con análisis, modelado y visualizaciones
│
├── visuals/
│   ├── Matriz_Correlacion.png
│   ├── Boxplot_Tenure_Churn.png
│   ├── Boxplot_TotalCharges_Churn.png
│   ├── Scatter_Tenure_TotalCharges_Churn.png
│   ├── Top10_Coefficients_LogisticRegression.png
│   └── Top10_Importance_RandomForest.png
│
└── README.md
```

---

## Preparación de los datos

### 1. Clasificación de variables

- **Categóricas:** `customer.gender`, `customer.Partner`, `customer.Dependents`, `phone.PhoneService`, `phone.MultipleLines`, `internet.InternetService`, `internet.OnlineSecurity`, `internet.OnlineBackup`, `internet.DeviceProtection`, `internet.TechSupport`, `internet.StreamingTV`, `internet.StreamingMovies`, `account.Contract`, `account.PaperlessBilling`, `account.PaymentMethod`.

- **Numéricas:** `customer.tenure`, `account.Charges.Monthly`, `account.Charges.Total`, `customer.SeniorCitizen`.

### 2. Tratamiento de datos

- **Imputación de valores faltantes:** columna `account.Charges.Total` imputada con la media.
- **Codificación de variables categóricas:** One-Hot Encoding para variables categóricas.
- **Normalización / Estandarización:** aplicada solo a variables numéricas para modelos sensibles a la escala (Regresión Logística y KNN).

### 3. Separación de datos

- Dataset dividido en entrenamiento (70%) y prueba (30%).

---

## Modelización

### Modelos utilizados

1. **Regresión Logística:** sensible a la escala, permite interpretar coeficientes de cada variable.
2. **Random Forest:** modelo basado en árboles, robusto y no sensible a la escala, evalúa la importancia de cada variable.

### Justificación

- Regresión Logística para interpretar relaciones lineales.
- Random Forest para alto desempeño y detección de interacciones no lineales.

---

## Exploración de datos (EDA)

- **Matriz de correlación:** relaciones entre variables numéricas y `Churn_Yes`.
- **Boxplots:** `customer.tenure` y `account.Charges.Total` vs Churn.
- **Scatter plot:** `tenure` vs `account.Charges.Total` según Churn.
- **Top 10 variables:** coeficientes de Regresión Logística y Random Forest.

**Insights:**

- Mayor antigüedad → menor churn.
- Gasto total alto → mayor probabilidad de churn.
- Fibra óptica y streaming → riesgo de churn más alto.
- Métodos de pago digitales y facturación sin papel → leve aumento en probabilidad de churn.

---

## Resultados de los modelos

- **Regresión Logística:** Exactitud 77,5%, F1-score 78,1%.
- **Random Forest:** Exactitud 90,5%, F1-score 90,7%, Recall 95%.
- **Conclusión:** Random Forest es más confiable para detectar clientes con riesgo de churn.

---

## Estrategias de retención

1. Clientes con alto gasto total → descuentos y beneficios personalizados.
2. Clientes con servicios de fibra óptica y streaming → promociones y contenido exclusivo.
3. Clientes nuevos o con baja antigüedad → programas de bienvenida y seguimiento.
4. Métodos de pago digitales → mejorar experiencia y recordatorios.

---

## Instrucciones para ejecutar el cuaderno

1. Clonar o descargar el proyecto.
2. Instalar librerías:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

3. Cargar datos tratados:

```python
import pandas as pd
df = pd.read_csv('data/telecomx_clean.csv')
```

4. Ejecutar `notebooks/TelecomX_Parte2.ipynb` paso a paso.
5. Los gráficos se generan y guardan en `visuals/`.

---

## Conclusión

El proyecto identifica las variables más relevantes para el churn y propone estrategias de retención basadas en datos, permitiendo decisiones informadas para reducir cancelaciones en Telecom X.

