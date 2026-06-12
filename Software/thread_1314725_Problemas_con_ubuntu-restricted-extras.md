---
title: "Problemas con ubuntu-restricted-extras"
date: 2009-11-04
forum: Software
---

### Post by ramiro_md on 2009-11-04
Buenas, resulta que después de un grato paso por Debian vuelvo a mis pagos. De nuevo con Ubuntu, en su flamante(?) versión 9.10, me alegré de ver que esta versión se instaló e inició el sistema más rápido (por lo menos en mi pc) que las dos versiones anteriores.
EN fin estoy teniendo el siguiente problema, cuando instalé ubuntu-restricted-extras se ve que no puede terminar de configurar el paquete ttf-mscorefonts, entonces siempre que quiero instalar algo me tira que ese paquete va  a ser configurado. Entonces es ahí cuando empieza a intentar resolver direcciones (tal vez de las cuales descargará las fuentes), digo que intenta porque no puede resolver ninguna :|. La salida en la consola es la siguiente:
```

--2009-11-04 19:21:32--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-11-04 19:21:42--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo switch.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «switch.dl.sourceforge.net»
--2009-11-04 19:21:52--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo mesh.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «mesh.dl.sourceforge.net»
--2009-11-04 19:22:02--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo dfn.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «dfn.dl.sourceforge.net»
--2009-11-04 19:22:12--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo heanet.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «heanet.dl.sourceforge.net»
--2009-11-04 19:22:22--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo jaist.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «jaist.dl.sourceforge.net»
--2009-11-04 19:22:32--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo nchc.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «nchc.dl.sourceforge.net»
--2009-11-04 19:22:42--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo ufpr.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «ufpr.dl.sourceforge.net»
--2009-11-04 19:22:52--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo internode.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «internode.dl.sourceforge.net»
--2009-11-04 19:23:02--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo voxel.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «voxel.dl.sourceforge.net»
--2009-11-04 19:23:12--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo kent.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «kent.dl.sourceforge.net»
--2009-11-04 19:23:22--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo internap.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «internap.dl.sourceforge.net»
sha256sum: andale32.exe: No existe el fichero ó directorio
andale32.exe: FALLO al abrir o leer
sha256sum: ADVERTENCIA: 1 de 1 del archivo listado no se ha podido leer
Checksum mismatch for andale32.exe, aborting!
dpkg: error al procesar ttf-mscorefonts-installer (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
Se encontraron errores al procesar:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-04 19:23:34--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-11-04 19:23:44--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo switch.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «switch.dl.sourceforge.net»
--2009-11-04 19:23:54--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo mesh.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «mesh.dl.sourceforge.net»
--2009-11-04 19:24:04--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo dfn.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «dfn.dl.sourceforge.net»
--2009-11-04 19:24:14--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo heanet.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «heanet.dl.sourceforge.net»
--2009-11-04 19:24:24--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo jaist.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «jaist.dl.sourceforge.net»
--2009-11-04 19:24:34--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo nchc.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «nchc.dl.sourceforge.net»
--2009-11-04 19:24:44--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo ufpr.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «ufpr.dl.sourceforge.net»
--2009-11-04 19:24:54--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo internode.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «internode.dl.sourceforge.net»
--2009-11-04 19:25:04--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo voxel.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «voxel.dl.sourceforge.net»
--2009-11-04 19:25:14--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo kent.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «kent.dl.sourceforge.net»
--2009-11-04 19:25:24--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo internap.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «internap.dl.sourceforge.net»
sha256sum: andale32.exe: No existe el fichero ó directorio
andale32.exe: FALLO al abrir o leer
sha256sum: ADVERTENCIA: 1 de 1 del archivo listado no se ha podido leer
Checksum mismatch for andale32.exe, aborting!
dpkg: error al procesar ttf-mscorefonts-installer (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
Se encontraron errores al procesar:
 ttf-mscorefonts-installer
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

```
Espero que algún entendido me pueda dar una mano :D.
Un saludo y gracias.

---

### Post by Mauro22 on 2009-11-04
Que yo sepa, siempre hubo problemas con ese paquete... o tarda en responder, o aborta, pero siempre tiene un As en la manga...


Intenta mas tarde!
):P

---

### Post by ramiro_md on 2009-11-04
> **Mauro22 said:**
> Que yo sepa, siempre hubo problemas con ese paquete... o tarda en responder, o aborta, pero siempre tiene un As en la manga...


Intenta mas tarde!
):P

Eso supuse, pero tengo que seguir instalando cosas y ese problema mediante no puedo (n)..bueno, voy a probar más tarde :/.

Un saludo mauro.

---

### Post by josecuervo86 on 2009-11-04
Ramiro, de donde estas tratando de bajar el paquete? de sourceforge? Porque fijate que esta tratando de bajarte un **.exe**! No se si te habías fijado en eso!

Si queres bajarte la ttf-mscorefonts-installer bajalas de aca: [http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer](http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer)

---

### Post by juancarlospaco on 2009-11-04
josecuervo86: las Fuentes *(Fonts)* de Microsoft SON .exe, 
el installer *(.deb)* es un Script de Bash que Wget*[SIZE="1"]ea[/SIZE]* los archivos desde Sourceforge.
*[SIZE="1"](me hace acordar a Arch)[/SIZE]*

ramiro_md:
y desde mi locacion y conexion esta andando correctamente:

```
juan@karmic:~$ wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
--2009-11-05 01:16:34--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo kent.dl.sourceforge.net... 212.219.56.167
Conectando a kent.dl.sourceforge.net|212.219.56.167|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net [siguiente]
--2009-11-05 01:16:35--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... 216.34.181.59
Conectando a downloads.sourceforge.net|216.34.181.59|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://ufpr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [siguiente]
--2009-11-05 01:16:36--  http://ufpr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolviendo ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Conectando a ufpr.dl.sourceforge.net|200.236.31.1|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 198384 (194K) [application/x-msdos-program]
Guardando: «andale32.exe»

100%[======================================>] 198.384     37,1K/s   en 5,2s    

2009-11-05 01:16:42 (37,1 KB/s) - `andale32.exe' guardado [198384/198384]

juan@karmic:~$
```

Proba en otro momento de reinstalar el paquete.

Si no, no te hagas drama, busca e instala[ las Liberation Fonts ]("apt:/ttf-liberation")*(en Repos)*,
son Clones de las de Microsoft hechas por Red Hat.
:)

---

### Post by josecuervo86 on 2009-11-04
> **juancarlospaco said:**
> josecuervo86: las Fuentes *(Fonts)* de Microsoft SON .exe, 
el installer *(.deb)* es un Script de Bash que Wget*[SIZE="1"]ea[/SIZE]* los archivos desde Sourceforge.
*[SIZE="1"](me hace acordar a Arch)[/SIZE]*

Tremendo FAIL el mio

---

### Post by ramiro_md on 2009-11-05
Bueno, le puse fin al problema desinstalando el ttf-mscorefonts-instaler e instalando el paquete liberation (como aconsejó juancarlospaco).
Un saludo gente.

---

### Post by rojojuan on 2009-11-06
Yo lo instalé al incluír ubuntu-restricted-extras. Y anda bien.

---

