---
title: "[AYUDA] Codificación no válida en archivos mp3"
date: 2010-06-16
forum: Software
---

### Post by leonardomdq on 2010-06-16
Me viene pasando desde que instale Lucid un problema con los archivos mp3  que algunos me los reconoce como "Codificación no válida", estube googleando pero no encuentro una solución.
Espero que alguno pueda orientarme para solucionarlo. 
Desde ya muchas gracias.


[[IMG]http://img99.imageshack.us/img99/8342/pantallazocau.png[/IMG]]("http://img143.imageshack.us/img143/8030/pantallazoob.png")

---

### Post by ketzelleshelle on 2010-06-16
Genial, venía a postear exactamente lo mismo.
El Banshee directamente no reconoce los archivos con codificación no válida. Intenté cambiarle las eñes (ya que eran esos los que tenían problemas) pero parece ser un problema de raíz...

---

### Post by leonardomdq on 2010-06-16
> **ketzelleshelle said:**
> Genial, venía a postear exactamente lo mismo.
El Banshee directamente no reconoce los archivos con codificación no válida. Intenté cambiarle las eñes (ya que eran esos los que tenían problemas) pero parece ser un problema de raíz...
Uso MPD Sonata y tampoco me los reconoce los archivos de codificación no válida, los renombre pero igual, al parecer son las "ñ" y los tildes. Los paquetes de idiomas los tengo instalados nose que puede ser, quizas sea un bug.
Esperemos que alguien puede ayudarnos.

---

### Post by camilitox on 2010-10-25
El problema es con los simbolos raros.. acentos, eñes,etc lo que tienen que hacer es renombrar uno por uno los archivos y corregir los &#65533;  tambien borrar lo que viene despues de la extension .mp3 es decir "(codificación no válida)"

si tienen una coleccion larga de mp3 es una tarea tediosa .... pero funciona... si alguien sabe crear un script que borre los simbolos raros y  la frase (codificación no válida), seria bueno que lo postee.
Saludos

---

### Post by EGKaltenmeier on 2011-07-18
Buenas, espero que me puedan ayudar a pesar del tiempo que ha pasado sin actividad en este thread. Yo tengo el mismo problema, y probablemente sea un tema de compatibilidad con Windows. El punto es que a mí ni me generaba mayores dolores de cabeza, porque renombraba los archivos y quitaba el excedente, y listo.

Sin embargo, ayer cometí un error. Quería renombrar un archivo, y en lugar de apretar la tecla del menú desplegable, y luego la "R", me confundí con Windows y apreté la "M", lo cual envió el archivo a la Papelera.

Inmediatamente me dí cuenta del error, y fui a la Papelera para restaurar el archivo, y seguir. El problema apareció acá: la Papelera me aparece con archivos en el ícono del Launcher, pero al acceder a ella tarda en responder un buen rato y luego de eso, no me indica archivo alguno. Como si estuviera vacía, que puedo asegurar no es el caso.

¿El archivo con "codificación no válida" puede haber generado ese problema? ¿Cómo lo resuelvo para recuperar el archivo eliminado en forma accidental y el funcionamiento normal de la Papelera?

Gracias, saludos!

---

### Post by recurrente on 2011-09-02
Hola, prueba con este comando que me hice despues de buscar por aquí y por alla:
[PHP]find . -name '?' | xargs convmv -r --notest -f cp850 -t UTF-8[/PHP]
Ejecútalo en un directorio y arreglará los acentos dentro de todo el árbol. A mí me funciona bastante bien. La clave es el el programita convmv y los parámetros cp850 y UTF-8 :P

---

### Post by iusmike on 2011-11-08
Funciona recurrente, aunque no coloca los acentos,(al menos no me los muestra asi en ubuntu 10.04) cambia los caracteres y revierte la codificacion no valida, gracias.

Agrego ademas, que si lo quieres ejecutar (aunque no lo creo conveniente) en tu carpeta como root habria que hacer un:

sudo su

poner la contraseña

y luego este comando

[COLOR=blue]# find / -name 'usuario' -prune -o -name '?' | xargs convmv -r --notest -f ISO-8859-1 -t UTF-8 [/COLOR]   
 
Recordar instalar el paquete convmv con un

[COLOR=blue]sudo apt-get install convmv [/COLOR]  

Fuente:
[http://teamouralis.es/viewtopic.php?f=78&t=6325](http://teamouralis.es/viewtopic.php?f=78&t=6325)

---

### Post by NauTiluS1 on 2012-01-26
Gracias, buscaba algo asi, ya que tengo muchos archivos con ese problema.

---

