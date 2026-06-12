---
title: "Donde van los scripts de la opcion sesiones?"
date: 2008-07-13
forum: Software
---

### Post by niko_3100 on 2008-07-13
Chicos bueno, ya todos sabemos que dentro de Sistema-Preferencias-Sesiones se pueden crear scripts para levantar programas cuando arranca nuestro ubuntu linux, ejemplo mi querido conky levanta de esa manera. Pero mi consulta es como hacer lo mismo pero en modo consola? Cual seria la ruta donde tendria que poner mi script para que me lo tome? Es en /etc/init.d ?? porque si es ahi no se que hago mal, tiro mi script de conky (super sencillo eh, espera 20 segundos y ejecuta el conky, eso hace el script) y no me lo levanta nunca... le doy permisos de ejecucion y toda la bola esa jeje pero aun asi no logro hacerlo andar. ATENCION: no quiero hacerlo en modo grafico porque es re facil y ya lo se, mi intencion es hacerlo en modo consola.

---

### Post by Hei Ku on 2008-07-13
el init.d es para los daemons. Tendrias que buscar por el lado de ejecutar algo en el momento que arrancas bash, que es el modo consola de ubuntu. 

Fijate en ~/bash_profile.

---

### Post by rober-mpp on 2008-07-14
Hei Ku tiene razon, el init.d es para los deamons. 

Sin embargo, yo lo vengo utilizando para cargar algunas cosas en el startup del sistema :P, como por ejemplo la configuracion de la red.

Para hacerlo desde el init.d tenes que crear tu script en /etc/init.d y en ese mismo directorio correr el comando:

update-rc.d <tu_script> start 20 2 .

( Chequea que es cada parametro, lo que si estoy seguro es que lleva el punto al final separado por un espacio )

Este comando te agrega tu script al runlevel 2 (en este caso, es uno de los parametros), y lo ejecuta, en este caso para que haga un 'start' del mismo.

Creo que la forma mas correcta es como indica Hei Ku en el post anterior, aunque dependiendo cuando queres que se corra el script tenes varios archivos de bash a los cuales le podes agregar la ejecucion de tu script. Lamentablemente estoy en el laburo y no con ubuntu, de ultima en casa te los posteo.

Saludos

---

### Post by faktorqm on 2008-07-14
ke buena foto rober! jaja 

yo en el script de los modems el que levanta la conecion lo pongo en /etc/init.d, por ejemplo, mi script se llama adsl_up y lo pongo en /etc/init.d/adsl_up y me lo levanta solito.
El de sesiones me parece que como es para cada usuario lo levanta desde cada home, como dice Hei Ku, pero ni bien cambia de user no sirve. O sea, yo tengo ke orientar el de la conexion para todos los usuarios, pero bueno, eso depende de lo que quieras hacer vos. Salu2!!

---

### Post by niko_3100 on 2008-07-14
Claro tal cual que levante para todos los usuarios, entonces como serian los comandos? ademas del script propiamente dicho. Gracias.

---

