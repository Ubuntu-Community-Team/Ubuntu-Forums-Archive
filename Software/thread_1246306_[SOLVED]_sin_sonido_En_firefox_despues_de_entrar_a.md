---
title: "[SOLVED] sin sonido En firefox despues de entrar a KDE"
date: 2009-08-21
forum: Software
---

### Post by cammell on 2009-08-21
hola; ando viendo entre actualizaciones asi que decidi ingresar por primera vez a mi kde que tenia instalado por aquello del amarok y del kaffeine asi que vi que podia configurar compiz tambien; y ps lo intente pero el gestor nomas hizo lo que le dio la gana y compiz no camino ni pa atraz ni pa adelante; ahora me enojo y me paso a gnome de nuevo pero al poner un video en firefox me percato que se ha quedado mudo en youtube; asi que me enojo y me doy cuanta que compiz esta todo desconfigurado con unas opciones bien sin ningun sentdo; asi que em enojo aun mas y entro a konkeror; porngo el mismo video e igual se queda mudo...tengo (o al menos tenia) todo configurado con alsa, para no tener broncas; pero segun he leido en un blog britanico KDE acostumbra secuestrar las saidas de sonido; ahora he probado volver a KDE y poner el mismo video y me percato de que se escucha como dios manda... asi que por eso andamos aqui; ahora aclaro TODOS los demas programas que usan audio alsa o relacion con ellos funcionan como dios manda....de hecho ya llevo 2 semanas con el problema que me he estado partiendo el craneo pero como ya me canse y no encuentro nada les pido ayuda...

ARREGLADO , ME TOPE CON ENTA SOLUCION GOOGLEANDO Y AQUI SE LAS PONGO:

cammell@cammell-laptop:~$ sudo apt-get install libflash-mozplugin
[sudo] password for cammell: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  libflash0c2
Se instalarán los siguientes paquetes NUEVOS:
  libflash-mozplugin libflash0c2
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 85.0kB de archivos.
Se utilizarán 365kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? A
Abortado.
cammell@cammell-laptop:~$ sudo apt-get install libflash-mozplugin
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  libflash0c2
Se instalarán los siguientes paquetes NUEVOS:
  libflash-mozplugin libflash0c2
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 85.0kB de archivos.
Se utilizarán 365kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? S
Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libflash0c2 0.4.13-9ubuntu1 [70.2kB]
Des:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libflash-mozplugin 0.4.13-9ubuntu1 [14.7kB]
Descargados 85.0kB en 1s (76.2kB/s)         
Seleccionando el paquete libflash0c2 previamente no seleccionado.
(Leyendo la base de datos ...  
344972 ficheros y directorios instalados actualmente.)
Desempaquetando libflash0c2 (de .../libflash0c2_0.4.13-9ubuntu1_i386.deb) ...
Seleccionando el paquete libflash-mozplugin previamente no seleccionado.
Desempaquetando libflash-mozplugin (de .../libflash-mozplugin_0.4.13-9ubuntu1_i386.deb) ...
Configurando libflash0c2 (0.4.13-9ubuntu1) ...

Configurando libflash-mozplugin (0.4.13-9ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cammell@cammell-laptop:~$ sudo apt-get install libflashsupport 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  libflashsupport
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 8326B de archivos.
Se utilizarán 65.5kB de espacio de disco adicional después de desempaquetar.
Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libflashsupport 1.9-0ubuntu1 [8326B]
Descargados 8326B en 0s (12.9kB/s)
Seleccionando el paquete libflashsupport previamente no seleccionado.
(Leyendo la base de datos ...  
345011 ficheros y directorios instalados actualmente.)
Desempaquetando libflashsupport (de .../libflashsupport_1.9-0ubuntu1_i386.deb) ...
Configurando libflashsupport (1.9-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by Hei Ku on 2009-08-21
O sea que tu problema no tiene nada que ver con KDE, sino con que no tenias todos los paquetes de flash. Gracias!

---

