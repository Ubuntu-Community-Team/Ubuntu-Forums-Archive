---
title: "Problemas de instalacion: unable to find a mediun containing a live file system"
date: 2012-03-14
forum: Software
---

### Post by nicoletoz on 2012-03-14
buenas gente, estoy arrancando en el mundo de linux, empeze hace unas semanas insertando directamente un disco de ubuntu 11.10 que queme aca mismo.
luego de bootear con el cd, cualquiera de las opciones del menu "instalacion total, probar ubuntu, chequear integridad del cd, etc" me mandaba a la pantalla de loading de ubuntu con los puntitos rojos y blancos y eso, para luego enviarme a una pantalla que dice busybox no se que y finalmente un error que decia "(intrafms) unable to find a medium containing a live file sysytem" no pudiendo solucionar este problema, simplemente decidi formatear el disco rigido, tras lo cual instale windows xp. hecho esto la instalacion de ubuntu corrio sin ninguna clase de error, deje windows en una particion de 40 gb y el resto se lo deje a ubuntu, pude correr sin problemas la maquina hasta que de un dia para otro, apague la pc y cuando la prendi no pude entrar mas a ubuntu. cuando lo selecciono desde el GRUB, aparece la pantalla violeta y luego se pone negra y ahi se queda. consultando con una amiga que tiene alguna idea, me recomendo que directamente me pase a otro os, xubuntu. me baje el disco de instalacion, booteo desde el cd, se me abre la pantalla de instalacion, apreto instalacion total y...boom. de vuelta el error de "unable to find a medium" etc.  la verdad que no tengo ni la mas minima intencion de volver a formatear todo (ademas de que no se como hacer para formatear las particiones de ubuntu, pero ese ya es otro tema) asi que acudo a ustedes linuxeros.

ayudaaaaaaaaaaaaaaaaaaaaaaaaaaaa

la pc es  una Intel pentium dual 1.8, con 1 gb de ram y una placa de video nvidia geforce fx 5200, con un disco rigido de 140 gb. lei por ahi que el problema puede tener que ver con el cd/dvd ROM. el que tengo yo un OPTIARC dvd rw ad-7260S, con entrada SATA.

me extendi un poco, pero creo que es mas facil si saben que es lo que me fue pasando y que fui probando.

un saludo y espero que puedan ayudarme!

---

### Post by Sergius14 on 2012-03-14
Que no te inicie desde el CD es raro, pero puede suceder si tenés corrupta o con errores la tabla de particiones....

El Live CD intenta acceder/montar los discos que tengas, así podes acceder a ellos y además, incluso, guardar datos de la sesión livecd para "resumir" luego.


Cuando incias con el LiveCD, hay una opción adicional que dice "Ramdisk".

Con esa opción, definitivamente no deberías tener problema alguno para inciarlo. Caso contrario, podés sacarte la duda e iniciarla con el disco desconectado (no hace falta que sea fisicamente, podes "sacarlo" desde el BIOS).


El como arreglar esto con Ubuntu, puede ser bastante simple, pero el primer paso es lograr que inicie el LiveCD con el disco conectado.


Si no podes inciarlo de ninguna forma, sería bueno que saques una captura de pantalla, o mejor dicho, una foto al monitor y que la adjuntes a este foro.

---

### Post by nicoletoz on 2012-03-19
buenas denuevo y gracias por contestar!! probe lo que me dijiste de desconectar el rigido (no supe hacerlo desde el bios, asi que directamente le deconecte la entrada SATA) y pude entrar perfectamente para instalar. la opcion RAMDISK no la encontre.  adjunto unas fotitos 

el error que me aparece al seleccionar la opcion de instalar:

[IMG]http://i240.photobucket.com/albums/ff133/nicoletox/DSCN1477.jpg[/IMG]

si tipeo exit desde ahi me manda esto:
[IMG]http://i240.photobucket.com/albums/ff133/nicoletox/DSCN1476.jpg[/IMG]

y si vuelvo a tipear exit me manda esto:

[IMG]http://i240.photobucket.com/albums/ff133/nicoletox/DSCN1475.jpg[/IMG]

y la pantalla de inicio de xubuntu es esta (ramdisk no aparece o al menos yo no lo vi =P :
[IMG]http://i240.photobucket.com/albums/ff133/nicoletox/DSCN1478.jpg[/IMG]


como sigo?

---

### Post by guillermolisi on 2012-03-20
Check disc for defects seria lo primero.

Tambien ayudaria que pruebes ese Live CD/pendrive en otra maquina que este funcionando para ver como se comporta.

Si en esa otra maquina funciona bien, algo habra que adecuar en la que estas usando ahora, algun parametro del BIOS, algun problema de RAM, etc.

---

