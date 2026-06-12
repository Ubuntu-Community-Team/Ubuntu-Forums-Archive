---
title: "[SOLVED] Desinstalando, reinstalando y actualizando Wine"
date: 2008-12-26
forum: Software
---

### Post by FalNix on 2008-12-26
Hola gente.
Soy bastante nuevo en Ubuntu y bueno quería instalar el Worms World Party. Me di cuenta que necesitaba el Wine, asi que usé el agregar o quitar programas  y lo instalé. Despues instalé el Worms, pero lo corrí y no me anduvo. Me enoje y lo desisntalé, y me di cuenta que seguia figurando en el menu. Pense que lo habia desinstalado mal asi que lo volvi a instalar solo para quitarlo luego. Me hizo el mismo problema pero ahora me lo instalo en una carpeta diferente y por supuesto no andaba. Me re enoje y desisntale el wine y todo.

Días después quise instalar el Wine de nuevo para ver si podía jugar el GTA San Andreas. Mi sorpresa fue cuando quise instalar el wine. Parecía que se instalaba bien pero en el menu aplicaciones no aparecía como la primera vez, de hecho no aparecía. Pensé que lo instale mal, así que lo desisntalé y lo volvi a instalar y lo mismo.

Después vi que por la computadora quedaron archivos del wine y del worms. Usando "gksu nautilus" borre los archivos que encontré con "locate wine" menos algunos que me pareció que no tenian nada que ver como winefish.
Intente usando el gestor de paquetes de Synaptic para usar la opción borrar todo inclusive los archivos de configuración, luego lo instalaba y no cambiaba en nada. También usé en la consola los comandos "sudo apt-get remove wine" y "sudo apt-get autoremove wine", luego probé instalandolo y no cambió nada.

Me dio la impresión que Ubuntu aunque no tiene un registro como Windows, debe tener algo parecido, y además cada aplicación desinstalada deja un montón de huellas en el sistema.

Luego me enteré que hay que actualizar y configurar el wine antes de usarlo.

En resumen despues de leer toda mi historia quisiera por favor que me ayudaran a:
-Borrar wine completamente, asi como otras aplicaciones que quiera eliminar en el futuro y que no dejen huellas.
-Instalar wine y que se vea como la primera vez que lo instalé.
-Decirme de donde me puedo bajar las actualizaciones de librerias y demas archivos del wine.

Sino la unica que me queda es copiar todas mis cosas y instalar el ubuntu desde cero.

De antemano gracias

PD: uso Ubuntu 8.04 Hardy henron

---

### Post by Tosh78 on 2008-12-27
Fijate que en tu carpeta personal, si vas a ver y seleccionas mostrar archivos ocultos, vas a ver que hay una carpeta que se llama .wine
Eso quiere decir que es una carpeta oculta. Proba borrarla cada vez que desinstales wine.
Para actualizarlo, una vez que lo tengas instalado, el mismo sistema te va a decir que hay paquetes para actualizar.
Suerte y conta como te va.

---

### Post by guillermolisi on 2008-12-27
Ademas de lo que te han dicho respecto de los archivos/directorios ocultos que empiezan con un punto, te recomiendo que consultes la base de aplicaciones de Wine en [http://appdb.winehq.org/](http://appdb.winehq.org/).

En esa base podras consultar sobre que grado de compatibilidad han logrado tanto en la instalacion como en la ejecucion de determinado software para Windows.

---

### Post by faktorqm on 2008-12-28
Cuando lo terminas de instalar, en sistema -> preferencias -> menu principal te tiene que aparecer, quiza destildada la opcion.
Si al menos te aparece, pero sigue sin funcionar, ejecuta desde una consola o apretando ALT+F2 "winecfg" (sin comillas) y ahi te aparece la ventana de configuracion del wine. 
Si el juego sigue sin funcionar, ejecuta en la consola el comando correspondiente para ejecutar el WWP (eso lo ves en el editor de menu, apretando propiedades, si es que te aparece) y si no aparece podes probar (ejemplo asi no mas) en una terminal "wine wwp.exe" y postear la salida que saca, muy probablemente determinemos el problema. Salu2!

---

### Post by FalNix on 2008-12-29
Holas.
Primero gracias por sus respuestas.

> ...ejecuta desde una consola o apretando ALT+F2 "winecfg" (sin comillas) y ahi te aparece la ventana de configuracion del wine. 

Con eso pude abrir bien la configuración del wine y después probé correr un programa instalado en el directorio C: trucho.

  wine C:\\Archivos\ de\ programa\\epsxe170\\ePSXe.exe

Es un emulador de Play Station que quise probar, y aparentemente funcionaria bien si no fuera porque me faltan los archivos .dll de wine. me tira ese error.

err:module:import_dll Library zlib1.dll (which is needed by L"C:\\Archivos de programa\\epsxe170\\ePSXe.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\epsxe170\\ePSXe.exe" failed, status c0000135

En las actualizaciones automáticas de Ubuntu no me aparece ninguna actualizacion para wine, tal vez se deba a que no tengo los repositorios de donde se bajan actualizaciones.
Aparentemente el wine se instala bien. Usando los comandos de consola es posible hacer funcionar los programas en el directorio "C:\". Lo unico que veo que falla son 2 cosas ahora.

--En el menu aplicaciones no aparece--
Ya me fije en "sistema -> preferencias -> menu principal" y no aparece un menu llamado wine como antes donde te dice las aplicaciones que tenés, el acceso a la configuración, etc. Lo mas que aparece es en el submenu "otras" destilado una aplicación "Wine cargador de programas de Windows". Pero si lo tildo y lo trato de ejecutar no pasa nada.

--me faltan las librerias .dll para correr los programas--

Como ya dije el gestor de actualizaciones no me muestra actualizaciones para wine. Tengo los siguientes repositorios:

cdrom:[Ubutu .04.1_Hardy Henron_ - Release i386... 
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner (Codigo fuente)
Ubuntu 4.10 <<Warty Warthog>>

En el último (Warty Warthog) cuando lo tildo para que me de actualizaciones, me dice que no encuentra el repositorio, y no me deja ver las actualizaciones. Tal vez se deba a que no es para mi versión 4.08 sino para la 4.10.

Si me pueden ayudar con estas dos últimas cositas el problema quedaría solucionado.

Desde ya muchas gracias.

---

### Post by faktorqm on 2008-12-29
> **FalNix said:**
> Holas.
Primero gracias por sus respuestas.

 

Con eso pude abrir bien la configuración del wine y después probé correr un programa instalado en el directorio C: trucho.

  wine C:\\Archivos\ de\ programa\\epsxe170\\ePSXe.exe

Es un emulador de Play Station que quise probar, y aparentemente funcionaria bien si no fuera porque me faltan los archivos .dll de wine. me tira ese error.

err:module:import_dll Library zlib1.dll (which is needed by L"C:\\Archivos de programa\\epsxe170\\ePSXe.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\epsxe170\\ePSXe.exe" failed, status c0000135

En las actualizaciones automáticas de Ubuntu no me aparece ninguna actualizacion para wine, tal vez se deba a que no tengo los repositorios de donde se bajan actualizaciones.
Aparentemente el wine se instala bien. Usando los comandos de consola es posible hacer funcionar los programas en el directorio "C:\". Lo unico que veo que falla son 2 cosas ahora.

Bien, deberias poner las dll's que faltan en la ubicacion que el programa las busca! no tiene nada que ver con actualizar o no. Tenes que mirar, primero que el emulador ese de play station este soportado en la direccion que te paso guille, si esta soportado y no te anda, tenes que buscar la dll esa que falta y copiarla en algun lado que el programa la encuentre (por darte un ejemplo asi no mas, c:\archivos de programa\play\, que eso en gnu/linux seria ~/.wine/drive_c/Archivos\ de\ programa/play)

> **FalNix said:**
> 
--En el menu aplicaciones no aparece--
Ya me fije en "sistema -> preferencias -> menu principal" y no aparece un menu llamado wine como antes donde te dice las aplicaciones que tenés, el acceso a la configuración, etc. Lo mas que aparece es en el submenu "otras" destilado una aplicación "Wine cargador de programas de Windows". Pero si lo tildo y lo trato de ejecutar no pasa nada.


Hace la entrada a manopla, te digo como lo tengo yo por ejemplo con un visor de bases de datos dbf:

```
env WINEPREFIX="/home/faktorqm/.wine" wine "C:\Archivos de programa\DBF Viewer 2000\dbview.exe" C:\Archivos de programa\DBF Viewer 2000\dbf.ico
```

otro ejemplo (simulador de redes de cisco)

```
env WINEPREFIX="/home/faktorqm/.wine" wine "C:\Archivos de programa\Packet Tracer 4.11\bin\PacketTracer4.exe"
```

el mismo pero desinstalador:

```
env WINEPREFIX="/home/faktorqm/.wine" wine "C:\Archivos de programa\Packet Tracer 4.11\unins000.exe" 
```

> **FalNix said:**
> 
--me faltan las librerias .dll para correr los programas--

Como ya dije el gestor de actualizaciones no me muestra actualizaciones para wine. Tengo los siguientes repositorios:

cdrom:[Ubutu .04.1_Hardy Henron_ - Release i386... 
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner (Codigo fuente)
Ubuntu 4.10 <<Warty Warthog>>

En el último (Warty Warthog) cuando lo tildo para que me de actualizaciones, me dice que no encuentra el repositorio, y no me deja ver las actualizaciones. Tal vez se deba a que no es para mi versión 4.08 sino para la 4.10.

Si me pueden ayudar con estas dos últimas cositas el problema quedaría solucionado.

Desde ya muchas gracias.

De vuelta, no es problema de actualizaciones. Las versiones de ubuntu, que son LTS duran 2 años. Es decir, que los repositorios estan on line durante ese tiempo y despues chau. Las versiones no-LTS duran 9 meses creo, (6 de periodo y 3 de changui) y despues chau. No lo encuentra por que no existe mas!
La version de ubuntu la podes averiguar con el comando 

```
lsb_release -a
```

la version del kernel con

```
uname -r
```

Espero que te haya servido. Salu2!

---

### Post by FalNix on 2008-12-29
Holas.
Bueno gracias, me baje el archivo .dll, lo busque en el google y lo puse en system32 del wine y anduvo.
Puse la linea de comando en el nuevo elemento del menú (modificada con mi nombre mas vale) y anduvo todo bien.
Recién lo probé al emulador y anda lo mas bien. Supongo que las demás aplicaciones también funcionarán si les bajo los .dll que necesitan.
Bueno, de nuevo muchas gracias, ya se solucionó todo. Ya le hice clic en la estrellita a cada uno para que le sume un gracias más.
Me quedo la duda nomas de porque al reinstalarlo no aparece mas el menú, pero bueno, ya lo hice a mano asi que no importa.

De nuevo gracias.

---

