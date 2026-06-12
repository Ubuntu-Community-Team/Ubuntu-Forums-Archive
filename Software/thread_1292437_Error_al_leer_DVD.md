---
title: "Error al leer DVD"
date: 2009-10-15
forum: Software
---

### Post by jorgito on 2009-10-15
Hola Todos, 

Estaba intentando ver una pelicula en un DVD original.
Intenté con Totem y VLC y ninguno de los dos puede hacerlo.
Probe inclusive mirar un solo archivo .VOB de la estructura de archivos del DVD y el VLC no hace nada y el totem trabaja como loco y no muestra nada.

Copio la salida en la consola de los dos programas:

viviana@viviana:~$ vlc
VLC media player 0.8.6e Janus
[00000287] dvdread demuxer error: read failed for -1/4 blocks at 0x01
[00000280] main playlist: nothing to play
[00000294] dvdread demuxer error: read failed for -1/4 blocks at 0x01
[00000280] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: THE_KID
libdvdnav: DVD Serial Number: 3A27F98C___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/viviana/.dvdnav/THE_KID.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Afirmación `0' fallida.
Cancelado

viviana@viviana:~$ totem

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_15_0.IFO).

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_16_0.IFO).
** Message: Error: No se pudo leer del recurso.
dvdreadsrc.c(919): gst_dvd_read_src_create (): /play/source

La máquina es una notebook Olivetti 600 con 8.04
En otra OLivetti serie 800 con 8.04 solo probe con el totem y hace lo mismo.

Alguien tendrá alguna idea de lo que pasa?

Saludos y desde ya muchas gracias!

---

### Post by guillermolisi on 2009-10-15
Probaste ese DVD en otros reproductores y PCs, inclusive con otros SOs ?
La superficie de lectura no esta rayada y/o sucia ?

---

### Post by jorgito on 2009-10-15
Gracias Guillermo, 

El DVD anda OK en una reproductora. No tengo otra maquina (y menos otro SO) para probar.

Gracias de nuevo

---

### Post by juancarlospaco on 2009-10-15
*[SMPlayer]("apt:/smplayer") probaste?*

---

### Post by jorgito on 2009-10-15
No lo habia probado, pero lo instale y lo probe.
Abre el DVD, pero se ve con una cuadricula, principalmente llena de ruido y pedacitos de la pelicula. Intente sacar un snapshot pero no se donde corcho los guarda!

Saludos y gracias

P.S.: Los encontre y aca agrego uno

---

### Post by rvm4000 on 2009-10-16
¿Tienes instalado el paquete libdvdcss2?

Es necesario para poder reproducir dvds comerciales.

---

### Post by jorgito on 2009-10-16
Hola rvm4000, 

Synaptic no lo ve, ni en la maquina ni en los repositorios.
Encontre ayuda para instalar libdvdcss, pero aun no para libdvdcss2...
Gracias

OK, no tengo subtitulos, pero me alcanza por hoy!

Para instalar libdvdcss2 me guie por 
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Gracias de nuevo.

---

