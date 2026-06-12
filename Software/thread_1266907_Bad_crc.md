---
title: "Bad crc"
date: 2009-09-15
forum: Software
---

### Post by nestor_stura on 2009-09-15
Estimados todos,
Logré instalar Joomla en local, para poder hacer pruebas en mi página web, sin modificar la que está en el servidor. 
Para bajarla hice un backup completo del sitio con Joomlapack y lo descargué.
Según las instrucciones el siguiente paso es extraer los archivos que descargué (.zip) en mi pc.

Hete aquí que cuando trato de extraerlo con File Roller (v.2.26.1) me da un error BAD CRC para cada archivo (supongo)
El tema es que cuando voy a ver los archivos, ahí están, lo que no sé es si están bien, si están completos, etc.

Alguien sabe por qué o como se soluciona o si simplemente no le presto atencion a los errores.

muchas gracias.

---

### Post by Hei Ku on 2009-09-15
Seguro que es un .zip y no un tar.gz? Me suena raro que use ese formato de compresion.

Los errores de CRC no son para pasar por alto. Es una señal que el archivo esta probablemente todo roto o en otro formato.

---

### Post by nestor_stura on 2009-09-17
> **Hei Ku said:**
> Seguro que es un .zip y no un tar.gz? Me suena raro que use ese formato de compresion.

Los errores de CRC no son para pasar por alto. Es una señal que el archivo esta probablemente todo roto o en otro formato.


Si, correcto, es un .zip. lamentablemente la herramienta de backup, que es la que uso para descargar mi sitio, no pregunta en que formato lo quiero comprimir.

¿Hay alguna forma de convertir .zip a .tar?

Gracias

---

### Post by Hei Ku on 2009-09-17
El problema no esta ahi sino en que ya el zip que genera esta roto.
Por que no probas con otra herramienta?

---

