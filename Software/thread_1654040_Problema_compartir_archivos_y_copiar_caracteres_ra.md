---
title: "Problema compartir archivos y copiar caracteres raros"
date: 2010-12-27
forum: Software
---

### Post by condes on 2010-12-27
Necesito compartir archivos de una computadora con Linux a otra. Sin embargo, me tira un error (parece clásico) de "no coincide el nombre del directorio o algo así" y entonces, luego de leer varios post, instalo samba, libapache2--svn y winbind. Bueno, nada de eso funcionó. Así que decidí eliminar libapache2-svn (solamente) porque ya estaba instalado con el samba. Y supuse que eliminándolo y luego volviéndolo a instalar, tal vez, el problema se solucionaría. Bueno, ocurrió que no se solucionó sino peor..., ahora, cuando toco con el botón derecho sobre una carpeta para compartir, no me aparece la opción de compartir.

Por otro lado, ya esto desde otras pc, cuando copio archivos en red o los envío a un usb me tira errores debido a caracteres extraños para el sistema ubuntu como acentos o la ñ. Es totalmente imposible que deje de usar tales caracteres puesto que son parte de mi idioma. 

Bueno, son dos problemas que van de la mano, porque necesito pasar información en red.


SAludos y gracias

---

### Post by asterix77 on 2010-12-28
Un poco enredada la explicación de tu problema.

1) La "otra" computadora ¿tiene linux?
2) ¿si ambas tienen linux, que distribución usan y que versión?
3) El error que te aparece ¿cuándo te aparece?, es decir tras hacer que cosa.
4) "Por otro lado, ya esto desde otras pc, cuando copio archivos en red...." . ¿como puedes hacer esto si no puedes compartir?.
5) Para que te aparezca la opción de "compartir" haciendo click derecho en una carpeta, debes tener instalado el paquete nautilus-share, junto con samba

$sudo apt-get install nautilus-share

En un pc con ubuntu, teniendo nautilus-share, y haciendo click derecho en una carpeta y dando a "compartir", si no tienes samba instalado, el sistema automáticamente te lo indica y te pregunta si quieres instalar samba; y eso es todo (eso en ambos pc a compartir).


Saludos

---

### Post by Maciett on 2010-12-28
Y sobre lo de caracteres extraños, evita poner tildes o ñ en los nombres de archivos y carpetas, úsalos sólo en el contenido de los mismos y no te molestará.

Saludos

---

### Post by moreback on 2010-12-28
Ubuntu usa principalmente UTF-8 para todo, incluso los nombres de archivo. Otros sistemas operativos como Windows no son tan estrictos en esto, por lo que probablemente usen ISO-8859-1 o algún otro.

Si quieres compatibilidad o evitarte dolores de cabeza, evita usar acentos y ñ en nombres de archivos o carpetas al traspasarlas a Windows.

Saludos.

---

### Post by condes on 2010-12-28
Gracias Asterix... instalé nautlius y ahora funca. Eso sí, el problema comenzó porque samba no se había instalado de forma automática. Y me tiraba errores. Pero bueno, este problema está solucionado. 

En cuanto a los acentos y Ñ, desde que tengo Ubuntu que no los uso. Pero tengo archivos viejos que sí tienen. Y, en mi opinión, no se le puede pedir a la gente que no use su propio idioma. Pero bueno, de no haber otra... PROBLEMA SOLUCIONADO

---

### Post by condes on 2010-12-28
Como no es la primera vez que tengo problemas con la red de Ubuntu, me tomé el trabajo de hacer una pequeña guía que intenta solucionar la mayoría de los problemas de la compartición de archivos. 

Aca va: 

Para poder compartir archivos, en teoría, es necesario samba. El paquete se instala de forma automática al utilizar la opción de "compartir archivos", que aparece al momento de tocar botón derecho del mouse sobre una carpeta. Sin embargo, antes o luego de instalar samba, puede haber problemas...

El primer problema que puede aparecer, es que samba no se instale de forma automática. En este caso deberemos instalarlo manualmente.

Si la opción de compartir archivos no se muestra por entorno gráfico hay que instalar nautilus-share. Luego, instalar samba.

Si la opción de compartir archivos existe y se verifica que samba está instalado, puede suceder que aparezca otro error al momento de compartir los archivos. Un error muy común es "la carpeta o archivo no existe". Para solucionar lo anterior puede probarse instalando  libapache2--svn. También puede probarse instalando samba-common-bin. Es preferible probar primero con libapache para la versión 9.10 y con samba-common-bin para la versión 10.

Por último, si lo que se necesita es compartir archivos con windows y hay problemas para hacerlo, puede probarse instalando winbind.

Lo otro que se puede hacer, solo si lo anterior no funcionó, es desinstalar y volver a instalar los paquetes principales como nautilius o samba (o todo).





PD: Los nombres de los paquetes están de forma literal, solo hay que picar en el terminar el clásico sudo aptitude install "nombre del paquete".

---

