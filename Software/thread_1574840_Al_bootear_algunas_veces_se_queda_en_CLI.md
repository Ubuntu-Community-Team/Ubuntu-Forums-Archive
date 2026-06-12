---
title: "Al bootear algunas veces se queda en CLI"
date: 2010-09-14
forum: Software
---

### Post by drhrich on 2010-09-14
Hola a todos los foreros de habla hispana.

Tengo Ubuntu 10.04 amd-64 en una pc de escritorio (mother asus y micro amd 64). Muchas veces arranca normalemente, pero algunas veces (un 75% - 25%) al arrancar no abre la GUI y me deja directamente en la linea de comandos. Al ingresar y ejecutar startx arranca gnome normalmente.

Busqué en este foro pero no encontré este problema particular (o no supe buscarlo).
Como puedo entender mejor el problema? Que revisarían ustedes?

Gracias!

---

### Post by papibe on 2010-09-14
Translation:


Hello everyone that speaks Spanish.

I have Ubuntu 10.04 amd-64 in a desktop PC (asus micro motherboard - amd 64). It seldom starts OK. It often (75 % - 25 %) does not open the GUI, and goes directly to the command line. In that case, if I run startx, gnome starts normally.

I looked for similar threads in this forum, but I did not find this particular problem (may be I didn't do it right).

How do I get a better understanding of the problem? What would you check?

Thank you!

---

### Post by papibe on 2010-09-14
**English:**

It seems something goes wrong while trying to go to a graphic mode. Do you have a graphic card installed?

X Windows has a log that you can check for those kind of errors:
```
$ more /var/log/Xorg.0.log
```
It's a bit long. Try to look for errors (EE).

**Spanish:**

Pareciera que falla el inicio del modo gráfico. Que tarjeta gráfica usas? la del motherboard o instalaste una extra?

Revisa la bitácora de XWindows para buscar errores:
```
$ more /var/log/Xorg.0.log
```
Es un archivo un poco largo. Busca errores (EE).

Good Luck!

---

### Post by drhrich on 2010-09-14
Hola papibe. Gracias!

Estoy usando la tarjeta onboard, una nvidia con los controladores privativos.

En varios logs viejos encontré este tipo de errores:

```
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Sep 14 10:26:36 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 14 10:26:36 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 14 10:26:36 NVIDIA(0):     enabled.
(EE) Sep 14 10:26:36 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 14 10:26:36 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 14 10:26:36 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

```

En el actual no, pero arrancó correctamente.

A que readme se refiere y a que log? No encontré mensajes de error en kern.log ni sys.log, voy a seguirlos un tiempo más. 

Gracias de nuevo!

---

### Post by papibe on 2010-09-14
**English:**

To see the kernel log:
```
$ dmesg
```
I'm not sure if you can use the nvidia driver with a motherboard card. What is the result of this:
```
$ lshw
```

**Spanish:**

Pare ver el log del kernel:
```
$ dmesg
```
No estoy seguro que con una tarjeta del motherboard puedas usar el drive de nvidia. Puedes mostrarme el resultado del comando:
```
$ lshw
```

---

### Post by sandyd on 2010-09-14
> **drhrich said:**
> Hola papibe. Gracias!

Estoy usando la tarjeta onboard, una nvidia con los controladores privativos.

En varios logs viejos encontré este tipo de errores:

```
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Sep 14 10:26:36 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 14 10:26:36 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 14 10:26:36 NVIDIA(0):     enabled.
(EE) Sep 14 10:26:36 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 14 10:26:36 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 14 10:26:36 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

```En el actual no, pero arrancó correctamente.

A que readme se refiere y a que log? No encontré mensajes de error en kern.log ni sys.log, voy a seguirlos un tiempo más. 

Gracias de nuevo!
Por favor, intente presionar la tecla SHIFT mientras se inicia el equipo. "Modo de recuperación" y pulse Enter. [COLOR=#000000]A continuación, seleccione 'root' cuando la pantalla azul aparece. [/COLOR]Escriba el siguiente
```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Terrible sandy. Terrible of you to use google translator.
---------------------
English:
Lets try to get the display back first for the OP k?

I don't remember if recovery mode requires the root password or not (i havent used ubuntu for a long time now), but see if you can get him into a terminal and get him to run
```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```which will disable the nvidia driver for the time being.
We can then deal with the nvidia driver problem... after he has some form of GUI up.

---

### Post by drhrich on 2010-09-15
Hi, Thanks to all. If this don't bother you to much I will continue writing in spanish. (My englis grammar is like crap (not much worst than my vocabulary)). The good side is: I don't have any problems reading it.


Sandyd: Puedo conseguir una GUI simplemente ejecutando startx o sudo gdm. El inconveniente es que algunas veces arranca a la CLI y otras al GUI y me molesta los problemas erráticos.

Papibe:

Creo que la parte interesante de la salida de lshw es:

```

     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:22 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff memory:dffc0000-dffdffff(prefetchable)

```


En cuanto al controlador de nvidia, lo usaba con ubuntu 8.04 en esta misma pc sin ningún inconveniente, incluso podía utilizar compiz-fusion con algunos efectos.


La salida completa de lshw es:

[CODE]
dhr-desktop
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=40B69074-8DFE-D511-826B-001FC6C212B0
  *-core
       description: Motherboard
       product: M2N-MX SE Plus
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev x.xx
       serial: MF7085G02106758
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0503 (03/26/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 1GHz
          capacity: 2600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:e00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:dffff000-dfffffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dfffec00-dfffecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:dfff8000-dfffbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1f:c6:c2:12:b0
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=190.55.28.15 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:27 memory:dfffd000-dfffdfff ioport:e480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:e400(size=8) ioport:e080(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d880(size=16) memory:dfffc000-dfffcfff
        *-disk
             description: ATA Disk
             product: WDC WD1600AABS-0
             vendor: Western Digital
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 05.0
             serial: WD-WMAP9E912320
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=a818a818
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: eeb2c374-aba0-0a46-b2f2-d758d9276fdc
                size: 27GiB
                capacity: 27GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-09-08 08:59:22 filesystem=ntfs label=WinXP state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 121GiB
                capacity: 121GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 22GiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 10048MiB
              *-logicalvolume:2
                   description: Linux swap / Solaris partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 1906MiB
                   capabilities: nofs
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /
                   capacity: 87GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH20NS15
             vendor: HL-DT-ST
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: IL00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:22 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff memory:dffc0000-dffdffff(prefetchable)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: a
          bus info: usb@1:8
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
[\CODE]


Gracias a todos.

---

### Post by Sef on 2010-09-15
Moved to a spanish speaking forum.

---

### Post by papibe on 2010-09-15
...y nos movieron a un foro en español. Lo más probable es que sigamos conversando solos.

Necesito ver unos archivos pero son muy largos para que los pegues aquí. Usemos un sitio donde los puedas pegar. Familiarizate con:

[INDENT][pastebin]("http://pastebin.com/")[/INDENT]

Bootea tu máquina hasta que pase el error y te pase al CLI. Logéate(?) y ejecuta lo siguiente para crear copia de estos archivos:

```
$ sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
$ sudo cp /var/log/Xorg.0.log /var/log/Xorg.0.log.bak
$ sudo cp /var/log/kern.log   /var/log/kern.log.bak
```

Entra a la interfaz gráfica, anda a pastebin. Para cada copia que hiciste (*.bak) pégala y crea un url (no la pierdas!).

Responde este mensaje y pegas las ligas de los 3 archivos.

Saludos.

---

### Post by Iowan on 2010-09-15
The spanish IRC channel -> #ubuntu-es
The spanish language forum -> [http://www.ubuntu-es.org/forum2]("http://www.ubuntu-es.org/forum2")   :D

---

### Post by drhrich on 2010-09-19
Disculpame la demora. Estuve con poco tiempo por el trabajo.

Estos son los archivos:
kern.log.bak      [http://pastebin.com/StztwHvd](http://pastebin.com/StztwHvd)

xorg.log.bak      [http://pastebin.com/iZADeNft](http://pastebin.com/iZADeNft)

Xorg.0.log.bak    [http://pastebin.com/r0a5LMfH](http://pastebin.com/r0a5LMfH)

Gracias!

---

### Post by alfplayer on 2010-09-19
Del log del kernel, con *grep npviewer*:

Sep 13 22:12:05 dhr-desktop kernel: [  947.251323] npviewer.bin[1933]: segfault at 418 ip 00000000f60c1dd6 sp 00000000ffc3bbc8 error 6 in libflashplayer.so[f5e73000+b2c000]
Sep 15 22:12:48 dhr-desktop kernel: [20732.632619] npviewer.bin[6005]: segfault at 418 ip 00000000f607fdd6 sp 00000000ff9637d8 error 6 in libflashplayer.so[f5e31000+b2c000]
Sep 16 23:04:43 dhr-desktop kernel: [59920.346104] npviewer.bin[7707]: segfault at f57bd054 ip 00000000f6199733 sp 00000000ff9a3a30 error 4 in libflashplayer.so[f5dfa000+b2c000]
Sep 18 11:04:41 dhr-desktop kernel: [ 8013.744716] npviewer.bin[2112]: segfault at 418 ip 00000000f6087dd6 sp 00000000ffd19c78 error 6 in libflashplayer.so[f5e39000+b2c000]
Sep 18 18:12:01 dhr-desktop kernel: [33653.423282] npviewer.bin[4897]: segfault at ea21304c ip 00000000f61f3757 sp 00000000ffe98350 error 4 in libflashplayer.so[f5e54000+b2c000]

Problema con el reproductor Flash?

---

### Post by papibe on 2010-09-19
> Problema con el reproductor Flash?

Si, así parece. Revisa este reporte de error:
[INDENT][npviewer.bin crashed]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/560279")[/INDENT]

En ese caso el problema se resolvió instalando la versión de 64b del flash player. Te recomiendo primero desintalar el flash player que tienes instalado. Probar varias veces si inicia bien tu máquina y luego que este&#347; seguro de que tienes estabilidad, probar la versión de 64bits.

Cuéntanos como te va.

Suerte!

---

### Post by papibe on 2010-09-23
Parece que la versión de 64 bits estuvo descontinuada por un tiempo. Pero hay buenas noticias:

[64bit Flash for Linux returns]("http://www.omgubuntu.co.uk/2010/09/64bit-flash-for-ubuntu/")

[Install 64bit Flash from a PPA or .deb]("http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/")

Saludos.

---

