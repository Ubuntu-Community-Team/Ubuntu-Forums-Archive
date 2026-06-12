---
title: "[SOLVED] Problemas con Eclipse"
date: 2008-11-05
forum: Software
---

### Post by rodolfojavier1982 on 2008-11-05
Hola a todos, les comento...
Tengo un problema con eclipse, para empezar, no me aparecia la ventana de la consola dentro del IDE Eclipse, luego la pude activar aunque de manera manual, ahora hay codigo que hice con Eclipse Ganymede y aca lo ejecuta mal, por ejemplo unas ventanas basicas, como que no las maneja bien (Cuando quiero cerrarla me dice "La ventana tal no esta respondiendo Al forzar a esta aplicacion a cerrarse, perdera cualquier cmambio que no haya guardado"), aclaro que esto no me pasaba ni en WinXP ni en OpenSuse11 para descartar errores de codificado.
Tengo entendido que la que baje desde Aplicaciones->Añadir y quitar
es una version de Ubuntu y no la que esta en la pagina oficial de Eclipse. 
Esto es asi?
Puedo bajar la de la pagina oficial o voy a tener problemas?
Debo desinstalar la de Ubuntu o debo dejarla aparte?

Bueno, disculpen si son muy basicas, es que hace 5 dias que tengo Ubuntu (8.10)

Agradecere cualquier respuesta.

Saludos.:confused:

---

### Post by faktorqm on 2008-11-05
¿la consola que buscas no esta en "window -> show view -> console"?

con respecto a los errores deberias asegurarte de que tenes todas las bilibotecas bien instaladas (esto es, instaladas y en un path correcto para que eclipse lo encuentre). Salu2!!

---

### Post by rodolfojavier1982 on 2008-11-06
Ya lo pude solucionar, con un poco de google y mucho pensar, bastante... 

Si, la consola la pude visualizar desde el Eclipse, pero tenia que activarla a manopla y no venia por defecto, el problema era con la ejecucion de ventanas hechas con librerias como javax.swing.*

El tema era que cuando descargue el Eclipse desde Aplicaciones->Añadir y quitar...
Me bajaba el eclipse que fue modificado con gente de Ubuntu y me instalaba el jre 1.5 de ellos, aparte de que el eclipse era el 3.2 (viejo) y no el 3.4 (el ultimo).
Tuve que bajar el 3.4 (Ganymede) de la pagina oficial de eclipse y bajar el JRE de Sun desde Aplicaciones->Instalar o quitar...
 
En fin bastante enquilombado, hice un "How To" para Dummies, je je.

Les paso el enlace, es un archivo de texto odt.

En si, es todo lo que hice, si lo quieren chusmear...


[http://2wibhg.bay.livefilestore.com/y1p00j5v9RHRB9F3ly6umMbVUUQM2kYyhusJQOFaKMGXPMJJJwKsF8Xbflk3rOhHEmK-WP1sb7J5D3wfLcN3mlMMg/IMPORTANTE%20ECLIPSE%20EN%20UBUNTU%20ULT.zip?download](http://2wibhg.bay.livefilestore.com/y1p00j5v9RHRB9F3ly6umMbVUUQM2kYyhusJQOFaKMGXPMJJJwKsF8Xbflk3rOhHEmK-WP1sb7J5D3wfLcN3mlMMg/IMPORTANTE%20ECLIPSE%20EN%20UBUNTU%20ULT.zip?download)

> **faktorqm said:**
> ¿la consola que buscas no esta en "window -> show view -> console"?

con respecto a los errores deberias asegurarte de que tenes todas las bilibotecas bien instaladas (esto es, instaladas y en un path correcto para que eclipse lo encuentre). Salu2!!

---

### Post by davidchuco on 2008-11-25
Hola! Pues yo tengo un problema similar. Cuando uso lo de crear ventanitas (swing) con su JFrame y todo eso, se me abre una ventana sin nada, y parece como bloqueado ya que no puedo cerrarla.

Por el contrario, el mismo programa lo pruebo en windows con eclipse también, y no hay ningún tipo de problema.

Pasos que he seguido:

Me he metido en la página _http://www.eclipse.org/downloads/ y he descargado la versión EclipseClassic, la de 151 MG para Linux 32.

Lo he descomprimido y colocado la carpeta en /usr/sbin. Ejecuto el programa y todo parece perfecto. Los programas que trabajaban únicamente con consola, funcionan perfectamente.

Asi que voy a los repositorios de ubuntu, he instalo sun-java5-jre.

Y ahora ejecuto el programa como Java Applicattion, y sucede lo dicho.

Uso ubuntu 8.10 por si a alguien le sirve.

Alguna sugerencia? 1 saludo y gracias.

---

### Post by vk-cdg on 2008-11-26
Me da un error al tratar de descomprimir el archivo.

---

### Post by rodolfojavier1982 on 2008-11-26
> **davidchuco said:**
> Hola! Pues yo tengo un problema similar. Cuando uso lo de crear ventanitas (swing) con su JFrame y todo eso, se me abre una ventana sin nada, y parece como bloqueado ya que no puedo cerrarla.

Por el contrario, el mismo programa lo pruebo en windows con eclipse también, y no hay ningún tipo de problema.

Pasos que he seguido:

Me he metido en la página _http://www.eclipse.org/downloads/ y he descargado la versión EclipseClassic, la de 151 MG para Linux 32.

Lo he descomprimido y colocado la carpeta en /usr/sbin. Ejecuto el programa y todo parece perfecto. Los programas que trabajaban únicamente con consola, funcionan perfectamente.

Asi que voy a los repositorios de ubuntu, he instalo sun-java5-jre.

Y ahora ejecuto el programa como Java Applicattion, y sucede lo dicho.

Uso ubuntu 8.10 por si a alguien le sirve.

Alguna sugerencia? 1 saludo y gracias.

Tres cosas
1- Yo uso java 6 (1.6 para compilar).
2- El archivo de eclipse que bajé es el 
    eclipse-SDK-3.4.1-linux-gtk.tar.gz
   Solo se descomprime y se ejecuta el bin para correrlo, no se instala con make ni make config...
3- Seteaste desde eclipse que te tome el compilador de sun 1.6? 
(el 1.5 en tu caso).
   Fijate que en el link que puse en el 2º mensaje explica bastante claro como cambiar el compilador que va a usar eclipse.

Para el otro chico, no se si se referia al archi que enlace arriba pero volvi a bajar el archivo que mande y no me tira ningun error.

Saludos.

---

### Post by vk-cdg on 2008-11-26
Mil gracias, debe haber sido mi conexion del laburo que lo bajó corrupto. Lo bajo nuevamente desde casa.

---

### Post by davidchuco on 2008-11-28
Buah que bien!!! Nose porque razón ahora si que va. Se ve que lo descomprimia en directorio restringido o algo daba algun problema... Cosa que no entiendo porque no tiene lógica dado que la consola iba y todo eso. Muchas gracias por las ayudas y las imágenes que colgaste ;)

---

### Post by rodolfojavier1982 on 2008-11-28
> **davidchuco said:**
> Buah que bien!!! Nose porque razón ahora si que va. Se ve que lo descomprimia en directorio restringido o algo daba algun problema... Cosa que no entiendo porque no tiene lógica dado que la consola iba y todo eso. Muchas gracias por las ayudas y las imágenes que colgaste ;)

Que bueno que te haya servido el tuto que hice.
Si tienen algun otra pregunta sobre el eclipse, haganla y tratare de responderla o sino alguno siempre puede aportar sus conocimientos.
Saludos.

---

