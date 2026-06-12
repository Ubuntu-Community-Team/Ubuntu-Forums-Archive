---
title: "Extraer texto de un archivo PDF"
date: 2009-07-29
forum: Software
---

### Post by jorval on 2009-07-29
Hola amigos. ¿Cómo puedo extraer texto, una o dos páginas, de un documento PDF que tiene más de 600 páginas. Bajé PDFedit pero no entiendo como funciona. Alguna indicación para un método más fácil. Desde ya muy agradecido.

---

### Post by Hei Ku on 2009-07-29
Podés probar con Okular, que es muy bueno.
Ojo que quizas en realidad esté todo como imagen. En ese caso no hay manera de copiar y pegar, salvo que lo pases primero por un OCR.

---

### Post by pablo.s on 2009-07-29
Yo he utilizado con éxito
una utilidad que se llama
pdftotext que viene incluida
en el paquete poppler-utils.
Saludos.

---

### Post by guillermolisi on 2009-07-29
Acabo de encontrar algo al respecto en [este link]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-03/msg00478.html") a una lista de e-mail sobre Debian donde sugieren usar una utilidad incluida en el paquete **xpdf-utils**, llamada **pdftotext**, que parece funcionar bien si el documento se genero por algun editor de texto. Si fue creado a partir de un papel digitalizado, parece que no sirve y ahi recomiendan aplicar un OCR.

En el mismo thread alguien sugiere usar Koffice que parece puede importar PDFs.
Otro dice que con GhostScript tambien se podria, particularmente los digitalizados o mixtos con imagenes.

---

### Post by jorval on 2009-07-29
Muchas gracias por vuestras respuestas. Dos grandes dudas:
1.- ¿Cómo sé si el archivo PDF es imagen/digitalizado? y 
2.- Busqué en Synaptic y tengo instalado el paquete poppler-utils que contiene pdftotext. Pero lo busqué en aplicaciones y no lo encontré para poder abrir el pdf con pdftotext?
Gracias nuevamente.

---

### Post by pablo.s on 2009-07-29
> **jorval said:**
> Muchas gracias por vuestras respuestas. Dos grandes dudas:
1.- ¿Cómo sé si el archivo PDF es imagen/digitalizado? y 

Si puedes seleccionar el texto
para copiar y pegar, es que NO
es imagen.

> **jorval said:**
> 2.- Busqué en Synaptic y tengo instalado el paquete poppler-utils que contiene pdftotext. Pero lo busqué en aplicaciones y no lo encontré para poder abrir el pdf con pdftotext?
Gracias nuevamente.

Se usa asi: (en una terminal)

```
pdftotext nombredelPDF.pdf
```

---

### Post by aledruetta on 2009-07-29
Hay un complemento de OpenOffice que te permite abrir los PDF con la aplicación Draw. Ahí hacés lo que querés con el PDF, es muy práctico. Se llama "Sun PDF Import Extension" y la instalás en Herramientas-->Administrador de extensiones-->obtener más extensiones aquí.

Espero que te sirva,
Alejandro.

---

### Post by jorval on 2009-07-29
Pablo.s. Muchas gracias por tus indicaciones. El archivo lo puedo seleccionar solo con "seleccionar todo" pero no por partes con el mouse. 
Puse la orden en la terminal y me dice Error, que el archivo no puede ser abierto. Verefiqué el archivo y yo, el propietario del archivo, tengo los permisos de lectura y escritura.

Aledruetta. Gracias por tu información. La encontré y mañana la probaré. Saludos.

---

### Post by jorval on 2009-07-30
Mala suerte, de todos modos muchas gracias por la ayuda, algo aprendí.
El archivo pdf del que deseo extraer texto es de esos que son imágenes, no se puede selecionar, lo comprobé con otros archivos pdf
Respecto a SUN pdf...funciona con OOo 3.0 y yo aun tengo 2.4
Asunto terminado y ¿solucionado? Para mi sí.

---

### Post by guillermolisi on 2009-07-30
> **jorval said:**
> Mala suerte, de todos modos muchas gracias por la ayuda, algo aprendí.
El archivo pdf del que deseo extraer texto es de esos que son imágenes, no se puede selecionar, lo comprobé con otros archivos pdf
Respecto a SUN pdf...funciona con OOo 3.0 y yo aun tengo 2.4
Asunto terminado y ¿solucionado? Para mi sí.
Proba con el OO 3 y de acuerdo a lo que resulte vemos si lo marcamos como solucionado o lo dejamos un tiempo mas por si hay algun otro aporte.

Un OCR no te serviria, dado que es todo imagen ?

---

### Post by jorval on 2009-07-30
Guillermolisi. Aun no voy a cambiar a OOo 3 lo haré cuando actualice la versión de Ubuntu a la ¿10.04? OCR (Optical character recognition) no tenía idea que existían, veré de qué se trata, los mantendré informados. Gracias nuevamente.

---

