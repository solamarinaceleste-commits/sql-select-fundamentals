## Preguntas Teóricas y Documentación

### 1. ¿Por qué es mala práctica usar `SELECT *` en producción?
Utilizar `SELECT *` en entornos de producción genera inconvenientes serios por las siguientes razones:

* **Rendimiento e impacto en red:** Trae todas las columnas de la tabla, consumiendo memoria, CPU e ingente ancho de banda innecesariamente, lo que vuelve lentas las consultas en bases de datos con millones de registros.
* **Mantenibilidad y rotura de aplicaciones:** Si la estructura de la tabla cambia en el futuro (se agrega, elimina o reordena una columna), la aplicación o reporte que consume la consulta puede romper sus mapeos de datos automáticamente.
* **Seguridad y privacidad:** Trae datos sensibles que el usuario final o reporte no necesita ver (por ejemplo, claves, correos o datos personales).

### 2. ¿Por qué son importantes los alias para un stakeholder no técnico?
Los alias (`AS`) permiten traducir los nombres técnicos de la base de datos a un lenguaje amigable y comprensible para cualquier área del negocio.

* **Ejemplo concreto:**
  Sin alias, el reporte muestra un encabezado como `total_amount`, el cual es técnico e inglés.
  Al aplicar el alias:
  ```sql
  SELECT total_amount AS monto_total_ventas_usd FROM sales;


