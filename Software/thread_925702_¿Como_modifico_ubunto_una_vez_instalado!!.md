---
title: "¿Como modifico ubunto una vez instalado?!!"
date: 2008-09-20
forum: Software
---

### Post by altebrown on 2008-09-20
Que tall!, mi duda es la siguiente como puedo modificar ubuntu una vez instalado, como consigo los codigo fuente y como se lo puede compilar..?, que soft utilizo, esta dentro de ubuntu??, si es asi cual es?, cual es la alternativa mejor acertada,por favor una ayudita, soy nuevo en esto y estoy con todo en programacion en "C", gracias y saquenme la duda, saludos!! jose,

---

### Post by c4d0rn4 on 2008-09-21
what?

ubuntu suele ser más para user frendly que para andar compilando. Aún así se puede, si lo que querés compilar es el kernel de linux (si mal no tengo entendido) vas a necesitar los headers y otras dependencias.

Distros que se tiran más a eso, me parecen, slackware o arch linux, pero no ubuntu.

Si lo que queres es cambiar el aspecto de ubuntu no hay que ponerse en eso, sino cambiar o configuarar el escritorio.

Para instalar programas lo más sencillo es synaptic, si no lo encuentras poné un la terminal:
 
sudo synaptic

en synaptic con el search buscas y casi seguro encontras.

---

### Post by Hei Ku on 2008-09-21
Si te referis a recompilar el kernel, mas vale que aprendas primero lo basico, como compilar algun programa.

Pero de dónde surge tu necesidad? Solo vale la pena recompilarlo para cosas muy particulares, como baja latencia o realtime.

---

### Post by pol666 on 2008-09-21
hombre... decinos que queres hacer particularmente ;)

---

### Post by valucha on 2008-09-21
[COLOR="DarkOrchid"]Para mi que habla de modificar cosas en sí de ubuntu, tipo agregar o quitar programas, ponerle KDE, xfce o gnome, etc..
[/COLOR]

---

### Post by guisheca on 2008-09-22
Para mi también se refiere a modificar el SO en si. El vago lo que busca es el código fuente de ubuntu para poder hacerle modificaciones. Esa me parece que es su intensión.

---

### Post by eldragon on 2008-09-22
buenas. aca una brebe reseña de lo que creo que buscas.

linux en si, es solo el kernel (una interfaz entre el usuario y el hardware).

para modificar esto (no te lo recomiendo por ahora), podrias bajar el source del kernel con
```

$ sudo apt-get install ubuntu-source

```
esto va a bajar el source code del kernel que tenes instalado, en un archivo comprimido que esta en /usr/src

cada programa, tiene su propio proyecto donde podes bajar su source, y compilar.

ejemplo: alsa-project.org

suerte

---

### Post by niko_3100 on 2008-09-25
Nunca respondi este muchacho nuevo...

---

### Post by sartrejp on 2008-09-26
Una lástima, un tipo valioso, al segundo post estaba compilando ubuntu....

---

### Post by lavaramano on 2008-09-28
por si alguien lo vuelve a leer y le interesa, los sources de todos los programas que hay en debian (por ende, ubuntu) se pueden bajar con:

```
apt-get source *paquete*
```

el cual solamente te baja el codigo fuente, un programa.orig.tar.gz que es el source del upstream sin modificar, un diff con los cambios hechos para debian/ubuntu, un .dsc y un changes.

ahi solamente les resta ver que dependencias para compilar necesitan en el archivo 'control' dentro del directorio debian en el directorio con el codigo fuente del upstream.

simulacion:
```


$ apt-get source htop
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Necesito descargar 148kB de archivos fuente.
Des:1 http://ftp.us.debian.org testing/main htop 0.7-1 (dsc) [969B]
Des:2 http://ftp.us.debian.org testing/main htop 0.7-1 (tar) [144kB]
Des:3 http://ftp.us.debian.org testing/main htop 0.7-1 (diff) [2955B]
Descargados 148kB en 4s (34,1kB/s)
dpkg-source: extracting htop in htop-0.7
dpkg-source: info: unpacking htop_0.7.orig.tar.gz
dpkg-source: info: applying htop_0.7-1.diff.gz
$ ls
htop-0.7  htop_0.7-1.diff.gz  htop_0.7-1.dsc  htop_0.7.orig.tar.gz
$ cd htop-0.7/
$ ls
aclocal.m4               CategoriesPanel.h  config.h      debug.h                Header.c      ListItem.h          MetersPanel.h  ProcessList.h    SignalItem.h    TraceScreen.c
AffinityPanel.c          ChangeLog          config.h.in   DebugMemory.c          Header.h      LoadAverageMeter.c  missing        README           SignalsPanel.c  TraceScreen.h
AffinityPanel.h          CheckItem.c        configure     DebugMemory.h          htop.1        LoadAverageMeter.h  NEWS           RichString.c     SignalsPanel.h  UptimeMeter.c
AUTHORS                  CheckItem.h        configure.ac  depcomp                htop.c        Makefile.am         Object.c       RichString.h     String.c        UptimeMeter.h
autogen.sh               ClockMeter.c       COPYING       DisplayOptionsPanel.c  htop.desktop  Makefile.in         Object.h       ScreenManager.c  String.h        UsersTable.c
AvailableColumnsPanel.c  ClockMeter.h       CPUMeter.c    DisplayOptionsPanel.h  htop.h        MemoryMeter.c       Panel.c        ScreenManager.h  SwapMeter.c     UsersTable.h
AvailableColumnsPanel.h  ColorsPanel.c      CPUMeter.h    FunctionBar.c          htop.png      MemoryMeter.h       Panel.h        scripts          SwapMeter.h     Vector.c
AvailableMetersPanel.c   ColorsPanel.h      CRT.c         FunctionBar.h          INSTALL       Meter.c             Process.c      Settings.c       TasksMeter.c    Vector.h
AvailableMetersPanel.h   ColumnsPanel.c     CRT.h         Hashtable.c            install-sh    Meter.h             Process.h      Settings.h       TasksMeter.h
CategoriesPanel.c        ColumnsPanel.h     **debian**        Hashtable.h            ListItem.c    MetersPanel.c       ProcessList.c  SignalItem.c     TODO 
$ cd debian/
$ ls
changelog  compat  **control**  copyright  dirs  docs  menu  rules  watch
$ cat control 
Source: htop
Section: utils
Priority: optional
Maintainer: Bartosz Fenski <fenio@debian.org>
**Build-Depends: debhelper (>= 4.0.0), libncurses5-dev, autotools-dev**
Standards-Version: 3.7.3
Homepage: http://htop.sourceforge.net

Package: htop
Architecture: any
Depends: ${shlibs:Depends}
Description: interactive processes viewer
 Htop is an ncursed-based process viewer similar to top, but it 
 allows to scroll the list vertically and horizontally to see
 all processes and their full command lines.
 .
 Tasks related to processes (killing, renicing) can be done without 
 entering their PIDs.

```

---

