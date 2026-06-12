---
title: "Ubuntu inicia en la linea de comandos en lugar del entorno de escritorio."
date: 2011-06-18
forum: Software
---

### Post by nemodot on 2011-06-18
Hola amigos, 

estuve instalando Ubuntu 10.10 ayer y luego de la instalación me puse a actualizar los programas con el Gestor de Actualizaciones, luego de un buen rato vuelvo y hay un mensaje de error, así que pongo a actualizar nuevamente y luego de muchas horas se queda trabado en una parte y no avanza más, así que decidí reiniciar.

Pero ahora cada vez que ingreso a ubuntu, entro a una especie de linea de comandos donde tengo que hacer el login y eso es todo.

Cómo puedo restaurar el entorno de escritorio?

---

### Post by asterix77 on 2011-06-18
¿Que pasa si es que escribes el siguiente comando?

$startx

---

### Post by nemodot on 2011-06-18
Eso lo he probado, pero tenia entendido que ya no sirve.

Pero ciertamente no me inicia el entorno.

---

### Post by guillermolisi on 2011-06-18
Que resultado te dio probar con ```
sudo service gdm start
``` ?

Que informacion pudiste ver en /var/log/xorg.0.log ?
Que informacion pudiste ver en /var/log/dmesg ?

Por las dudas, corriste en una terminal/consola ```
sudo dpkg --configure -a
``` ?

---

### Post by nemodot on 2011-06-18
Cuando hago el *service gdm start* me tira:
"job is already running"
Estará corriendo pero no parece que funcione bien.

Y cuando hice el *sudo dpkg --configure -a* se me quedo colgado configurando un tal hplip-cups asi que tuve que reiniciarla.

---

### Post by guillermolisi on 2011-06-18
> **nemodot said:**
> Cuando hago el *service gdm start* me tira:
"job is already running"
Estará corriendo pero no parece que funcione bien.

Y cuando hice el *sudo dpkg --configure -a* se me quedo colgado configurando un tal hplip-cups asi que tuve que reiniciarla.
Entonces probaria de parar gdm ```
sudo service gdm stop
```correr de nuevo ```
sudo dpkg --configure -a
```y despues de que esta proceso haya finalizado correctamente (con la aplicacion de paquetes pendientes de instalacion) reiniciaria para ver si todo se debio a una actualizacion a medias o es otro el problema.

---

### Post by nemodot on 2011-06-18
Hice lo que me indicaste pero vuelve a colgarse varios minutis configurando algo y la computadora no parece trabajar nada.

Qué tal si borro esos paquetes donde aparentemente se queda colgada la configuración? Parecen ser paquetes de hewlett packard de los que puedo prescindir.

---

### Post by guillermolisi on 2011-06-18
hplip-cups es el modulo de CUPS, Common Unix Printing System, para impresoras HP con y sin Postcript.

Que paquetes serian los que borrarias ?
Como los borrarias para asegurarte que no quede alguna dependencia sin resolver y/o paquete roto ?

A todo esto, que mirror de repositorios estas usando ? Los de ARG ?
Si es asi, te sugiero que los cambies por otros, Brasil por ejemplo, y vuelvas a probar la actualizacion con ```
sudo apt-get update
```y
```
sudo apt-get dist-upgrade
```

---

### Post by nemodot on 2011-06-18
Borraría ese y otro más que comienza con "hp" con un simple *remove*.

Pero pensé en esa alternativa que planteas de cambiar los mirrors por los de brasil, aunque no sé como hacerlo desde ahi, que debería escribir?

Por cierto, no quiero actualizar a la última versión de Ubuntu, tuve muchos problemas y nunca pude resolverlos, quiero quedarme en la 10.10.

---

### Post by guillermolisi on 2011-06-18
> **nemodot said:**
> Borraría ese y otro más que comienza con "hp" con un simple *remove*.

Pero pensé en esa alternativa que planteas de cambiar los mirrors por los de brasil, aunque no sé como hacerlo desde ahi, que debería escribir?

Por cierto, no quiero actualizar a la última versión de Ubuntu, tuve muchos problemas y nunca pude resolverlos, quiero quedarme en la 10.10.
Para cambiar de mirror sin interface grafica tenes que editar el archivo /etc/apt/sources.list, por ej: ```
sudo nano /etc/pat/sources.list
``` y reemplazar el subdominio que indica de que pais u origen es el mirror por el que corresponda al nuevo que quieras utilizar.
Si queres probar con los centrales, con borrar ese subdominio es suficiente: Doy un par de lineas de ejemplo de como deberia quedarte: > deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates universe

apt-get dist-upgrade no te actualiza la version de Ubuntu sino que instala cualquier dependencia nueva que algun paquete requiera y no tengas instalada.

apt-get upgrade solo actualiza los paquetes que tengas instalados y si hay que instalar una dependencia nueva deja el paquete que la requiera sin actualizar.

---

### Post by nemodot on 2011-06-18
Borre las ar y deje todos los repositorios como vos decías, hice el *apt-get update* y me tira:

dpkg fue interrumpido, debe ejecutar manualmente 'dpkg - configure-a' para corregir el problema

Lo mismo me hace cuando le hago el *upgrade *o el *dist-upgrade*

Luego vuelvo a hacer el *sudo dpkg --configure -a* y se me cuelga nuevamente en el mismo lugar:

Configurando hpijs (3.10.6-1ubuntu.10.2)...

No mueve de ahi. Tampoco puedo removerlo con *remove*

---

### Post by guillermolisi on 2011-06-18
Todo suena a que hay problemas en los paquetes que se bajaron en la actualizacion.

Si tenes instalado Aptitude proba de borrar los cambios pendientes y el cache de paquetes.

Si invocas ```
sudo aptitude
```lo podes usar en modo pantalla completa en una consola y te resultara mas facil que por linea de comando ya que podras usar el menu del que dispone.

Tambien posee una opcion para encontrar paquetes rotos y una funcion de Resolver que te ayuda en los casos de conflictos.

---

### Post by nemodot on 2011-06-18
No entiendo nada de lo que dices al final, no conozco el programa y no puedo entrar en gnome así que estoy esclavizado a la linea de comandos. Voy a ver que sale...

---

### Post by nemodot on 2011-06-18
Se ve que aptitude no viene mas con ubuntu, y no puedo instalarlo asi que ya fue, voy a tener que volver a instalar el sistema por tercera vez. Qué mal están haciendo ultimamente las cosas en canonical...

---

### Post by guillermolisi on 2011-06-18
> **nemodot said:**
> No entiendo nada de lo que dices al final, no conozco el programa y no puedo entrar en gnome así que estoy esclavizado a la linea de comandos. Voy a ver que sale...

Aptitude se usa en consola, a pesar de que tambien posee una interface pseudo-grafica (caracteres graficos a partir de codigo ASCII extendido - ncurses).

Desde la version 10.10 (si no recuerdo mal) tenes que instalarlo (decision tomada el año pasado y que figura en la documentacion de las novedades que vienen con la version 10.10).

Instalarlo, probarlo y usarlo, es facil: ```
sudo apt-get install aptitude
```o sea, nada que vos no sepas hacer.

Familiarizate con Aptitude y podras no solo aprender algo mas sino tambien solucionar tu problema de paquetes actual y cualquier otro que se presente a futuro.

La opcion de volver a instalar todo siempre existe pero si vas por la tercera en vias de una cuarta, es que algo no estas haciendo bien, por lo menos desde la adquisicion de conocimientos para resolver problemas, IMHO.

Igualmente vos tenes la decision final.

---

### Post by Brath-ga on 2012-11-16
A mi me pasa lo mismo.
Utilizo la 12.04 y hasta ayer sin problemas.
Despues de actualizar paquetes nuevos, (actualizo diariamente), entre ellos el nuevo kernel para la 12.04, al reiniciar me envía a la tty1 y no deja entrar en modo gráfico.

Hice todo lo que explica Guillermolisi, pero sin resultado, instalé aptitude, pero no hay paquetes rotos, por último visualicé Xorg.0.log y encontré los fallos, no puede cargar los módulos de nvidia, pero mi inglés es muy básico y no entiendo como solucionarlo.
No puse aquí el log porque me parece muy largo, pero si me podeis hechar una mano lo envío o lo pego.
Gracias.

---

### Post by gmunioz on 2012-11-16
Cuando se actualiza el kernel, es necesario controlar que se instalen tambien los kernel headers y cuando se tienen instalados drivers privativos, en caso de ser descargados desde la web del fabricante se deben reinstalar, si son privativos de los repositorios, inicia con un kernel anterior y reinstalalos.

---

### Post by Brath-ga on 2012-11-17
Intenté iniciar con la versión anterior de Ubuntu y el resultado es el mismo. Me envía a la tty1.

Instalé los últimos drivers que la página de Nvidia me recomienda y el problema persiste.

El informe de Xorg.0.log es este.

```

[    18.485] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    18.485] X Protocol Version 11, Revision 0
[    18.485] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    18.485] Current Operating System: Linux pinki-fixo 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686
[    18.485] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic-pae root=UUID=f1f819e3-60be-4e99-b0a1-0b9b86a650c9 ro quiet splash vt.handoff=7
[    18.485] Build Date: 29 August 2012  12:10:05AM
[    18.485] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    18.485] Current version of pixman: 0.24.4
[    18.485] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.485] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.486] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 17 10:53:41 2012
[    18.495] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.495] (==) No Layout section.  Using the first Screen section.
[    18.495] (==) No screen section available. Using defaults.
[    18.495] (**) |-->Screen "Default Screen Section" (0)
[    18.495] (**) |   |-->Monitor "<default monitor>"
[    18.496] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.496] (==) Automatically adding devices
[    18.496] (==) Automatically enabling devices
[    18.496] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.496] 	Entry deleted from font path.
[    18.496] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.496] 	Entry deleted from font path.
[    18.496] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.496] 	Entry deleted from font path.
[    18.496] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.496] 	Entry deleted from font path.
[    18.496] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.496] 	Entry deleted from font path.
[    18.496] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.496] 	Entry deleted from font path.
[    18.496] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.496] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.496] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.496] (II) Loader magic: 0xb77445a0
[    18.496] (II) Module ABI versions:
[    18.496] 	X.Org ANSI C Emulation: 0.4
[    18.496] 	X.Org Video Driver: 11.0
[    18.496] 	X.Org XInput driver : 16.0
[    18.496] 	X.Org Server Extension : 6.0
[    18.497] (--) PCI:*(0:6:0:0) 10de:0a20:1458:34d6 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[    18.497] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.497] (II) LoadModule: "extmod"
[    18.503] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.503] (II) Module extmod: vendor="X.Org Foundation"
[    18.503] 	compiled for 1.11.3, module version = 1.0.0
[    18.503] 	Module class: X.Org Server Extension
[    18.503] 	ABI class: X.Org Server Extension, version 6.0
[    18.503] (II) Loading extension MIT-SCREEN-SAVER
[    18.503] (II) Loading extension XFree86-VidModeExtension
[    18.504] (II) Loading extension XFree86-DGA
[    18.504] (II) Loading extension DPMS
[    18.504] (II) Loading extension XVideo
[    18.504] (II) Loading extension XVideo-MotionCompensation
[    18.504] (II) Loading extension X-Resource
[    18.504] (II) LoadModule: "dbe"
[    18.504] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.504] (II) Module dbe: vendor="X.Org Foundation"
[    18.504] 	compiled for 1.11.3, module version = 1.0.0
[    18.504] 	Module class: X.Org Server Extension
[    18.504] 	ABI class: X.Org Server Extension, version 6.0
[    18.504] (II) Loading extension DOUBLE-BUFFER
[    18.504] (II) LoadModule: "glx"
[    18.504] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.514] (II) Module glx: vendor="NVIDIA Corporation"
[    19.514] 	compiled for 4.0.2, module version = 1.0.0
[    19.514] 	Module class: X.Org Server Extension
[    19.515] (II) NVIDIA GLX Module  310.19  Wed Nov  7 23:42:11 PST 2012
[    19.515] (II) Loading extension GLX
[    19.515] (II) LoadModule: "record"
[    19.515] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.515] (II) Module record: vendor="X.Org Foundation"
[    19.515] 	compiled for 1.11.3, module version = 1.13.0
[    19.515] 	Module class: X.Org Server Extension
[    19.515] 	ABI class: X.Org Server Extension, version 6.0
[    19.515] (II) Loading extension RECORD
[    19.515] (II) LoadModule: "dri"
[    19.515] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.515] (II) Module dri: vendor="X.Org Foundation"
[    19.515] 	compiled for 1.11.3, module version = 1.0.0
[    19.515] 	ABI class: X.Org Server Extension, version 6.0
[    19.515] (II) Loading extension XFree86-DRI
[    19.515] (II) LoadModule: "dri2"
[    19.516] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.516] (II) Module dri2: vendor="X.Org Foundation"
[    19.516] 	compiled for 1.11.3, module version = 1.2.0
[    19.516] 	ABI class: X.Org Server Extension, version 6.0
[    19.516] (II) Loading extension DRI2
[    19.516] (==) Matched nvidia as autoconfigured driver 0
[    19.516] (==) Matched nouveau as autoconfigured driver 1
[    19.516] (==) Matched nv as autoconfigured driver 2
[    19.516] (==) Matched vesa as autoconfigured driver 3
[    19.516] (==) Matched fbdev as autoconfigured driver 4
[    19.516] (==) Assigned the driver to the xf86ConfigLayout
[    19.516] (II) LoadModule: "nvidia"
[    19.516] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    19.590] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.590] 	compiled for 4.0.2, module version = 1.0.0
[    19.591] 	Module class: X.Org Video Driver
[    19.602] (II) LoadModule: "nouveau"
[    19.602] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.602] (II) Module nouveau: vendor="X.Org Foundation"
[    19.602] 	compiled for 1.11.3, module version = 1.0.2
[    19.602] 	Module class: X.Org Video Driver
[    19.602] 	ABI class: X.Org Video Driver, version 11.0
[    19.602] (II) LoadModule: "nv"
[    19.603] (WW) Warning, couldn't open module nv
[    19.603] (II) UnloadModule: "nv"
[    19.603] (II) Unloading nv
[    19.603] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.603] (II) LoadModule: "vesa"
[    19.603] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.603] (II) Module vesa: vendor="X.Org Foundation"
[    19.603] 	compiled for 1.11.3, module version = 2.3.0
[    19.603] 	Module class: X.Org Video Driver
[    19.603] 	ABI class: X.Org Video Driver, version 11.0
[    19.603] (II) LoadModule: "fbdev"
[    19.604] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.604] (II) Module fbdev: vendor="X.Org Foundation"
[    19.604] 	compiled for 1.11.3, module version = 0.4.2
[    19.604] 	ABI class: X.Org Video Driver, version 11.0
[    19.604] (==) Matched nvidia as autoconfigured driver 0
[    19.604] (==) Matched nouveau as autoconfigured driver 1
[    19.604] (==) Matched nv as autoconfigured driver 2
[    19.604] (==) Matched vesa as autoconfigured driver 3
[    19.604] (==) Matched fbdev as autoconfigured driver 4
[    19.604] (==) Assigned the driver to the xf86ConfigLayout
[    19.604] (II) LoadModule: "nvidia"
[    19.604] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    19.604] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.604] 	compiled for 4.0.2, module version = 1.0.0
[    19.604] 	Module class: X.Org Video Driver
[    19.604] (II) UnloadModule: "nvidia"
[    19.604] (II) Unloading nvidia
[    19.604] (II) Failed to load module "nvidia" (already loaded, -1217353189)
[    19.604] (II) LoadModule: "nouveau"
[    19.605] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.605] (II) Module nouveau: vendor="X.Org Foundation"
[    19.605] 	compiled for 1.11.3, module version = 1.0.2
[    19.605] 	Module class: X.Org Video Driver
[    19.605] 	ABI class: X.Org Video Driver, version 11.0
[    19.605] (II) UnloadModule: "nouveau"
[    19.605] (II) Unloading nouveau
[    19.605] (II) Failed to load module "nouveau" (already loaded, -1217353189)
[    19.605] (II) LoadModule: "nv"
[    19.605] (WW) Warning, couldn't open module nv
[    19.605] (II) UnloadModule: "nv"
[    19.605] (II) Unloading nv
[    19.605] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.605] (II) LoadModule: "vesa"
[    19.606] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.606] (II) Module vesa: vendor="X.Org Foundation"
[    19.606] 	compiled for 1.11.3, module version = 2.3.0
[    19.606] 	Module class: X.Org Video Driver
[    19.606] 	ABI class: X.Org Video Driver, version 11.0
[    19.606] (II) UnloadModule: "vesa"
[    19.606] (II) Unloading vesa
[    19.606] (II) Failed to load module "vesa" (already loaded, 0)
[    19.606] (II) LoadModule: "fbdev"
[    19.606] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.606] (II) Module fbdev: vendor="X.Org Foundation"
[    19.606] 	compiled for 1.11.3, module version = 0.4.2
[    19.606] 	ABI class: X.Org Video Driver, version 11.0
[    19.606] (II) UnloadModule: "fbdev"
[    19.606] (II) Unloading fbdev
[    19.606] (II) Failed to load module "fbdev" (already loaded, 0)
[    19.611] (II) NVIDIA dlloader X Driver  310.19  Wed Nov  7 23:23:35 PST 2012
[    19.611] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.615] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    19.615] (II) NOUVEAU driver for NVIDIA chipset families :
[    19.615] 	RIVA TNT        (NV04)
[    19.615] 	RIVA TNT2       (NV05)
[    19.615] 	GeForce 256     (NV10)
[    19.615] 	GeForce 2       (NV11, NV15)
[    19.615] 	GeForce 4MX     (NV17, NV18)
[    19.615] 	GeForce 3       (NV20)
[    19.615] 	GeForce 4Ti     (NV25, NV28)
[    19.615] 	GeForce FX      (NV3x)
[    19.615] 	GeForce 6       (NV4x)
[    19.615] 	GeForce 7       (G7x)
[    19.615] 	GeForce 8       (G8x)
[    19.615] 	GeForce GTX 200 (NVA0)
[    19.615] 	GeForce GTX 400 (NVC0)
[    19.615] (II) VESA: driver for VESA chipsets: vesa
[    19.615] (II) FBDEV: driver for framebuffer: fbdev
[    19.615] (++) using VT number 7

[    19.616] (II) Loading sub module "wfb"
[    19.616] (II) LoadModule: "wfb"
[    19.617] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.617] (II) Module wfb: vendor="X.Org Foundation"
[    19.617] 	compiled for 1.11.3, module version = 1.0.0
[    19.617] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.617] (II) Loading sub module "ramdac"
[    19.617] (II) LoadModule: "ramdac"
[    19.617] (II) Module "ramdac" already built-in
[    19.619] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    19.619] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.620] (WW) Falling back to old probe method for vesa
[    19.620] (WW) Falling back to old probe method for fbdev
[    19.620] (II) Loading sub module "fbdevhw"
[    19.620] (II) LoadModule: "fbdevhw"
[    19.620] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.620] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.620] 	compiled for 1.11.3, module version = 0.0.2
[    19.620] 	ABI class: X.Org Video Driver, version 11.0
[    19.621] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    19.621] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    19.621] (==) NVIDIA(0): RGB weight 888
[    19.621] (==) NVIDIA(0): Default visual is TrueColor
[    19.621] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.623] (**) NVIDIA(0): Enabling 2D acceleration
[    19.637] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    19.637] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    19.637] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    19.637] (EE) NVIDIA(0):  *** Aborting ***
[    19.637] (EE) NVIDIA(0): Failing initialization of X screen 0
[    19.637] (II) UnloadModule: "nvidia"
[    19.637] (II) Unloading nvidia
[    19.637] (II) UnloadModule: "wfb"
[    19.637] (II) Unloading wfb
[    19.637] (EE) Screen(s) found, but none have a usable configuration.
[    19.637] 
Fatal server error:
[    19.637] no screens found
[    19.637] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    19.637] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    19.638] 
[    19.660]  ddxSigGiveUp: Closing log
[    19.660] Server terminated with error (1). Closing log file.

```

Y el comando lspci me devuelve la gráfica correcta.

```

06:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device 34d6
	Physical Slot: 16
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	Expansion ROM at fea00000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nvidia_experimental_304, nvidia_current_updates, nvidia, nouveau, nvidiafb


```

Incluso borré el xorg.conf (despues de hacer backup, por supuesto), pero nada. Al arrancar sin el me envía igualmente a la tty1.

Ya estoy empezando a desesperarme.

---

### Post by Brath-ga on 2012-11-17
Sigo intentado encontrar solución.

Al ejecutra nvidi-bug-report.sh ( ni sabía que existía ), me indica que el fallo está en: El módulo kernel de NVIDIA tiene la versión 304.48 pero este componente del controlador nvidia tiene la versión 310.19. Por favor, asegúrese de que el módulo del núcleo y todos los componentes del controlador de nvidia tengan la misma versión.

Ahora tengo que saber como se igualan las versiones.

---

