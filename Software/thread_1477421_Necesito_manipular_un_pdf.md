---
title: "Necesito manipular un pdf"
date: 2010-05-08
forum: Software
---

### Post by DrKenobi on 2010-05-08
Hola!

Estoy estudiando desde un pdf y necesito algun programa que me permita resaltar, agregar notas y cosas utiles a la hora de estuiar. ¿Conocen a alguno bueno?

Graxias

---

### Post by guillermolisi on 2010-05-08
PDF Editor ? No se si es bueno pero a mi me ha servido para editar ciertos PDFs (sin clave).

---

### Post by DrKenobi on 2010-05-08
Estoy probando el PDF Editor, pero no me convence mucho...

---

### Post by juancarlospaco on 2010-05-08
*OpenOffice ?*
Tiene un plug-in para eso...

---

### Post by DrKenobi on 2010-05-10
> **juancarlospaco said:**
> *OpenOffice ?*
Tiene un plug-in para eso...

Estuve viendo el [plug-in]("http://extensions.services.openoffice.org/en/project/pdfimport") para Open Office.
Tiene un problema, que no puede importar PDF's linearizados (o algo asi, esta en ingles la pagina).

Despues de generar mi pdf con un plug-in de firefox (si lo imprimis como un archivo ese pdf no lo puede importar OOo), pude importar el pdf.

Ahora el problema es que OOo importa los PDF al programa de dibujo, que no tiene una funcion para resaltar texto, y el modo en que inserta los comentarios no es muy bueno.

Lo que voy a hacer en breve es intentar importar el texto al Writer y agregar comenatios, subrayar y resaltar desde ahi.

---

### Post by alfplayer on 2010-05-10
> **DrKenobi said:**
> Estoy estudiando desde un pdf y necesito algun programa que me permita resaltar, agregar notas y cosas utiles a la hora de estuiar. ¿Conocen a alguno bueno?

No se puede hacer con Adobe Reader?

---

### Post by DrKenobi on 2010-05-10
> **alfplayer said:**
> No se puede hacer con Adobe Reader?

Se puede, pero para poder activar el menu con comentarios, subrayar, resaltar, etc. me pide que esten habilitados los derechos del documento ("document rights are enabled", espero haberlo traducido bien). Aunque yo cree el pdf, no encuentro la forma de habilitar esto y sigo sin poder usar el Adobe Reader completamente! bua bua bua jaja

---

### Post by alfplayer on 2010-05-10
Esta característica se la conoce como anotaciones. Okular (de KDE) puede hacerlo hace años. Las anotaciones persisten si se abren con Okular en la misma computadora, aunque según comentarios en la web, no se pueden graban en el archivo PDF.

Recién lo probé, y el soporte para anotaciones parece estar muy bien logrado.

---

### Post by alfplayer on 2010-05-10
Los llamados "derechos de documento" son definidos al crearse el archivo PDF, y no habría una forma simple y gratuita de habilitar para hacer las anotaciones.

---

### Post by DrKenobi on 2010-05-10
> **alfplayer said:**
> Esta característica se la conoce como anotaciones. Okular (de KDE) puede hacerlo hace años. Las anotaciones persisten si se abren con Okular en la misma computadora, aunque según comentarios en la web, no se pueden graban en el archivo PDF.

Recién lo probé, y el soporte para anotaciones parece estar muy bien logrado.

alfplayer, gracias por el dato. Yo tengo un disco de tan solo 4GB y el Okular me usaria 300MB aprox., asi que mejor lo dejo para mas adelante. No me queda mucho espacio. Debe necesitar tantos MB porque yo uso Gnome y el Okular usa KDE, me parece.

---

### Post by alfplayer on 2010-05-10
> **DrKenobi said:**
> alfplayer, gracias por el dato. Yo tengo un disco de tan solo 4GB y el Okular me usaria 300MB aprox., asi que mejor lo dejo para mas adelante. No me queda mucho espacio. Debe necesitar tantos MB porque yo uso Gnome y el Okular usa KDE, me parece.

Sí, es probable que esa sea la causa.

También podés probar otro llamado Xournal que leí que también tiene esta capacidad, convirtiendo al PDF a formato de imagen.

---

### Post by DrKenobi on 2010-05-10
> **alfplayer said:**
> Sí, es probable que esa sea la causa.

También podés probar otro llamado Xournal que leí que también tiene esta capacidad, convirtiendo al PDF a formato de imagen.

alfplayer, Xournal esta muy bueno! Es simple, corre muy rapido y tiene lo necesario! El tema de los comentarios no me convence mucho, pero tampoco puedo pedir tooodo. Yo buscaba algo tipo Post-it's.

Te dejo una captura de pantalla pa que veas como ya estoy usandolo! Gracias!

Si alguien tiene algun otro dato, estoy abierto a seguir probando!

---

### Post by alfplayer on 2010-05-10
Otra idea es probar instalar okular usando solo los paquetes necesarios, para saber si asi es posible reducir el espacio, por ejemplo sin instalar paquetes recomendados (con apt-get y aptitude usando *--no-install-recommends*), o dejando instalados solo los paquetes que se usen. Nunca lo hize pero creo que es posible.

También se podría compilar okular con un conjunto mínimo de librerías, pero esto no es fácil para el novato.

---

### Post by DrKenobi on 2010-05-11
> **alfplayer said:**
> Otra idea es probar instalar okular usando solo los paquetes necesarios, para saber si asi es posible reducir el espacio, por ejemplo sin instalar paquetes recomendados (con apt-get y aptitude usando *--no-install-recommends*), o dejando instalados solo los paquetes que se usen. Nunca lo hize pero creo que es posible.

También se podría compilar okular con un conjunto mínimo de librerías, pero esto no es fácil para el novato.

Me fije y siguen siendo un monton de paquetes... Me quedo usando Xournal.

Mil gracias por la ayuda!

---

### Post by alfplayer on 2010-05-11
Al trabajar con una imagen, se pierde algo muy importante, que es la capacidad de trabajar con texto, por ejemplo, seleccionarlo, copiarlo y hacer búsquedas.

---

### Post by DrKenobi on 2010-05-11
alfplayer, es verdad lo que decis... me haces dudar :confused: je

Si me resulta muy incomodo voy a hacer lo que me dijiste en un post anterior.
Voy a ver si me molesta mucho o no el trabajar con una imagen. :confused:

---

### Post by alfplayer on 2010-05-11
Si es una Eee Pc u otras netbook se puede ampliar fácilmente la capacidad con un pendrive.

---

### Post by DrKenobi on 2010-05-11
> **alfplayer said:**
> Si es una Eee Pc u otras netbook se puede ampliar fácilmente la capacidad con un pendrive.

Te referis a mi PC? Es una notebook, pero se me rompio el disco rigido, y tengo instalado 10-04 en un pendrive de 4GB (es una reliquia ja). Ya no le puedo poner otro pendrive, no me entran dos ala vez! (por un tema de espacio fisico). Igual no me quejo, anda casi 10 puntos!

---

### Post by alfplayer on 2010-05-11
Se puede usar un pendrive de más capacidad. Por ejemplo, uno de 8 GB cuesta 90 pesos, de 16 GB aprox. el doble.

---

### Post by DrKenobi on 2010-05-11
> **alfplayer said:**
> Se puede usar un pendrive de más capacidad. Por ejemplo, uno de 8 GB cuesta 90 pesos, de 16 GB aprox. el doble.

Si es verdad, pero estoy ahorrando hasta el ultimo centavo para dentro poco (ojala dias) comprarme un nueva laptop. Ya me falta muy poco!

Pero tenes rezon, en un de 16GB andaria re-bien!

---

### Post by DrKenobi on 2010-05-13
alfplayer, al final tenias razon, el no poder manejar el texto y estudiar con una imagen es bastante malo.

Como yo lo que queria es estudiar cosas principalmente de internet, que yo salvaba como pdf y despues leia, lo que hice ahora es usar Diigo.com

Por ahora el servicio este me gusta y mucho. Puedo resaltar y agregar notas, y al mismo tiempo puedo copiar y pegar, los links funcionan y, lo mejor, como el articulo esta en ingles puedo usar la extension diccionario en el google chromium (con un doble click te abre un globito con la definicion, excelente! :P).

Ah! Ademas Diigo tiene extensiones tanto para Firefox como para Chromium. Estoy muy contento. Ademas asi si la pagina se actualiza, porque es una wiki, mi articulo se actualiza tambien. (espero que esto no me juege en contra y me desfase todo :confused:)

---

