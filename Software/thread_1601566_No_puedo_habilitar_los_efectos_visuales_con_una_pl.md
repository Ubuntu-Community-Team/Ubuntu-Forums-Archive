---
title: "No puedo habilitar los efectos visuales con una placa intel 945G"
date: 2010-10-20
forum: Software
---

### Post by frosklo on 2010-10-20
[FONT=Arial][SIZE=2]Antes estaba usando una placa NVIDIA 7200GS en Ubuntu 10.04  (compiz+emerald+cairo) pero se me quemo por sobretemperatura asi que ahora estoy usando la placa onboard que es una intel 945G.

Elimine todos los drivers Nvidia e instale los intel pero no pude habilitar los "efectos visuales", entonces cansado de intentar instale Ubuntu 10.10. Con la reinstalacion pude habilitar los efectos visuales (compiz+emerald).

Luego agregue el app:  &#8220;x-updates&#8221; ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")) para mantener actualizado las "X". Cuando hice el update, se actualizo el kernel. Luego del reinicio de la PC los efectos visuales quedaron deshabilitados.

No puedo habilitar los "efectos visuales" en Ubuntu 10.10 con mi placa de video onboard intel 945G.

Cuando trato de habilitar los efectos, ubuntu abre una ventana que indica que esta buscando "drivers de video", no encuentra nada, y me avisa del error que "no puede habilitar los efectos visuales". No entiendo porque busca drivers de video si ya los tiene instalados.

Como puedo resolver este problema? Gracias

Un poco de información acerca del problema:[/SIZE][/FONT]                                       [SIZE=2]


  ```
a@desktop:~$ glxinfo | grep "rendering"
[/SIZE][SIZE=2]   [/SIZE][SIZE=2]   
[/SIZE][SIZE=2]direct rendering: Yes[/SIZE]
``` [SIZE=2]


```
a@desktop:~$ ./compiz-check
[/SIZE][SIZE=2]   
[/SIZE][SIZE=2]  Gathering information about your system...
   
   Distribution:          Ubuntu 10.10
   Desktop environment:   GNOME
   Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
   Driver in use:         intel
   Rendering method:      AIGLX
   
  Checking if it's possible to run Compiz on your system...
   
   Checking for texture_from_pixmap...               [ OK ]
   Checking for non power of two support...          [ OK ]
   Checking for composite extension...               [ OK ]
   Checking for FBConfig...                          [ OK ]
   Checking for hardware/setup problems...           [ OK ]
[/SIZE]
```[FONT=&quot][SIZE=2]  
[/SIZE][/FONT][SIZE=2]

```
a@desktop:~$ DISPLAY=:0 glxinfo
[/SIZE][SIZE=2]   
[/SIZE][SIZE=2]  name of display: :0.0
  display: :0  screen: 0
  direct rendering: Yes
  server glx vendor string: SGI
  server glx version string: 1.4
  client glx vendor string: Mesa Project and SGI
  client glx version string: 1.4
  OpenGL vendor string: Tungsten Graphics, Inc
  OpenGL renderer string: Mesa DRI Intel(R) 945G GEM 20100330 DEVELOPMENT 
  OpenGL version string: 1.4 Mesa 7.9-devel
[/SIZE]
```[SIZE=2]  
[/SIZE] [FONT=&quot][SIZE=2]
[/SIZE][/FONT][SIZE=2]
```
a@desktop:~$ sudo lshw -C display
   
    *-display
         description: VGA compatible controller
         product: 82945G/GZ Integrated Graphics Controller
         vendor: Intel Corporation
         physical id: 2
         bus info: pci@0000:00:02.0
         version: 02
         width: 32 bits
         clock: 33MHz
         capabilities: msi pm vga_controller bus_master cap_list rom
         configuration: driver=i915 latency=0
         resources: irq:16 memory:dfe00000-dfe7ffff ioport:8800(size=8) memory:e0000000-efffffff memory:dfe80000-dfebffff

```PD: [/SIZE][http://ubuntuforums.org/showthread.php?t=1601485](http://ubuntuforums.org/showthread.php?t=1601485)

---

### Post by alfplayer on 2010-10-21
Aparentemente, el bug no está reportado en [https://bugs.launchpad.net/~ubuntu-x-swat]("https://bugs.launchpad.net/~ubuntu-x-swat")

---

