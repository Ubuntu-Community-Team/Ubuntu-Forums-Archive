---
title: "Actualizaciones &quot;404 Not Found&quot;"
date: 2011-05-31
forum: Software
---

### Post by mecdem on 2011-05-31
Equipo Toshiba NB 105-SP2802A
Sistema: Ubuntu 10.04 (32 bits)
__________

Hola amigos.

En la actualización de hoy quedaron con un "404 Not Found" los siguientes archivos:

libpam0g_1.1.1-2ubuntu5.2_i386.deb
libpam-modules_1.1.1-2ubuntu5.2_i386.deb
libpam-runtime_1.1.1-2ubuntu5.2_all.deb

El repositorio de los tres es
[http://ar.archive.ubuntu.com/ubuntu/pool/main/p/pam/](http://ar.archive.ubuntu.com/ubuntu/pool/main/p/pam/)

Fuí a curiosear por ahí, y -en efecto-
existen los archivos ...1.1.1-2ubuntu5.1... 
pero no los ...1.1.1-2ubuntu5.2...

¿Es correcta mi observación?
¿Están faltando los archivos?
Y si faltan ¿por qué Synaptic los busca?
¿Cómo sabe que deben actualizarse si los archivos no están en el repositorio?

Gracias anticipadas por aclararme estas dudas.
Bueno, las que se pueda, porque quizás la respuesta a la última preguntita requiera que curse Ingeniería de Sistemas o algo así... :p

Un abrazo. MEC

---

### Post by guillermolisi on 2011-05-31
MEC

Cambia de mirror. Usa el central o alguno de Brasil, por ejemplo, que andan mejor que los locales. Por lo menos son mas consistentes.

Sabe que paquete tiene que actualizar porque los indices estan bien, marcan que hay una version nueva, pero el archivo, en definitiva, en el repositorio no fue debidamente actualizado y por esa inconsistencia te da ese error (aun mantiene la version anterior).

---

### Post by mecdem on 2011-05-31
Hola Guille.
Mil gracias.

Como corresponde a una principiante, ni idea de cómo cambiar de mirror.
Pero por allí andan las preguntas de otros principiantes y pude desasnarme en [http://ubuntuforums.org/showthread.php?t=1466816](http://ubuntuforums.org/showthread.php?t=1466816).

Así que seguí la ruta
Sistema - Administración - Origenes del Software - Pestaña Software de Ubuntu - Descargar desde... - Otro.
Ahi elegí un server de Brasil y... voilá!!

Ahora tengo de los tres archivos las versiones
1.1.1-2ubuntu5.3

¡¡SOLVED!!
Un abrazo. MEC

---

