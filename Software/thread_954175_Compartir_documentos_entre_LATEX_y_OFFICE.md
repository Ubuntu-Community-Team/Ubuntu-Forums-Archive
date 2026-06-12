---
title: "Compartir documentos entre LATEX y OFFICE"
date: 2008-10-20
forum: Software
---

### Post by GGsalas on 2008-10-20
Hola, he probado el programa LyX y, a pesar de mi inexperiencia en LATEX, pude crear un documento con varias imágenes muy fácil y rápido, además con una estécica excelente y con la ventaja que si quiero modificar algo el documento no se rompe.

En fin, estoy muy contento con mi descubrimiento pero tengo el inconveniente que no puedo copartir los documentos cn nadie ¿alguien conoce alguna manera? La primera opcion es exportar a OOfice, pero si exporta al de microsoft me ahorro un paso.

Gracias, saludos.

---

### Post by juanman on 2008-10-21
Es muy groso el lyx, cada vez lo uso mas para TPs. Potente y mas liviano q el OOo...
Podes convertirlo a RTF, q es un formato q lo puede leer el MS Word, Wordpad y el OOo Writer... Para q te aparezca entre los archivos a exportar, tenes q:
- instalar el paquete latex2rtf;
- despues ir a Herramientas -> Reconfigurar
- Reiniciar Lyx
- Te va a aparecer el Rich Text Format en Archivo -> Exportar

No se q tan buena será la conversión y cuan compatible será el RTF. Por lo poco q lo probé, anda bien, incluso con imagenes...
Fijate en el man de latex2rtf q tiene unas cuantas opciones, q se las podes agregar en Herramientas -> Preferencias -> Convertidores...

Si es un documento para solo lectura, creo q lo mas recomendable es q lo exportes a PDF...

Mas info:
[http://wiki.lyx.org/Tips/ExportingRichTextFormatWithLaTeX2rtf](http://wiki.lyx.org/Tips/ExportingRichTextFormatWithLaTeX2rtf)
[http://wiki.lyx.org/FAQ/Compatibility#toc2](http://wiki.lyx.org/FAQ/Compatibility#toc2)

---

### Post by guisheca on 2008-10-21
A lyx lo conocí hace poco también, es lo mas groso que vi para hacer los informes de laboratorio de la facu.

---

### Post by GGsalas on 2008-10-21
> **juanman said:**
> Podes convertirlo a RTF, q es un formato q lo puede leer el MS Word, Wordpad y el OOo Writer... Para q te aparezca entre los archivos a exportar, tenes q:
- instalar el paquete latex2rtf;
- despues ir a Herramientas -> Reconfigurar
- Reiniciar Lyx
- Te va a aparecer el Rich Text Format en Archivo -> Exportar


Gracias Juanman, funciona, aunque es muy lento y las imágenes aparecen distosionadas. Mi problema es compartir información con otras personas, si trabajo sobre un texto solo no tengo ese problema. Es una lastima que no existe una interacción mayor entre estos programas, al menos entre Latex y el formato estándar de OpenOffice.

---

