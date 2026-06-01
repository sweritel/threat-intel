# Threat Intelligence

# Análisis de Campaña de Cloaking (Threat Intelligence)

## 📌 Descripción del Proyecto

Este repositorio documenta mi proceso de investigación sobre una campaña de **cloaking** activa que suplanta a una agencia de modelos legítima. Como estudiante de desarrollo de software, mi objetivo fue analizar cómo los atacantes manipulan las cabeceras HTTP para evadir sistemas de seguridad y redirigir tráfico malicioso.

## 🔍 Hallazgos Principales

* **Técnica de evasión:** El servidor analiza el encabezado `User-Agent` del visitante. Muestra contenido aparentemente legítimo a determinados rastreadores o verificadores, mientras que los usuarios reales son redirigidos hacia redes de afiliación sospechosas.
* **Infraestructura:** La campaña opera desde infraestructura asociada con **Friendhosting LTD** (Sofía, Bulgaria), junto con una red de dominios relacionados identificados mediante técnicas de *Reverse IP Lookup*.
* **Impacto:** Se observó clonación técnica de marca, incluyendo recursos estáticos, estilos visuales y configuraciones de seguimiento para incrementar la credibilidad frente a potenciales víctimas.

## 🛠️ Metodología de Análisis

Para identificar el comportamiento de cloaking, se realizaron pruebas mediante `curl` desde terminal.

### 1. Detección de comportamiento para bots

```bash
curl -I "http://videoinst.store/v?cid=let3613"
```

**Resultado:** Respuesta `301 Moved Permanently`, indicando una redirección automática.

### 2. Simulación de usuario móvil (iPhone)

```bash
curl -L -A "Mozilla/5.0 (iPhone; CPU iPhone OS 16_0 like Mac OS X)" "https://videoinst.store/v?cid=let3613"
```

**Resultado:** Se obtuvo contenido diferente al observado en la prueba anterior, evidenciando un comportamiento dependiente del `User-Agent`.

## 📊 Indicadores Observados

* Uso de redirecciones condicionales.
* Variación del contenido entregado según el cliente HTTP.
* Posible utilización de infraestructura compartida con múltiples dominios relacionados.
* Empleo de técnicas de clonación visual para aumentar la confianza del usuario.

## 📢 Divulgación Responsable

Como parte de una práctica de investigación responsable, se notificó la actividad observada a las entidades correspondientes:

* Reportes enviados a los departamentos de abuso de los proveedores de alojamiento identificados.
* Reporte presentado a servicios de reputación y navegación segura para su evaluación.
* Registro de los indicadores observados en plataformas de análisis de malware y amenazas.

## ⚠️ Descargo de Responsabilidad

Este repositorio tiene fines exclusivamente educativos y de investigación en ciberseguridad. No contiene herramientas de explotación ni instrucciones destinadas a facilitar actividades maliciosas. El objetivo es documentar técnicas de evasión observadas en campañas reales y promover la concienciación sobre amenazas digitales.
