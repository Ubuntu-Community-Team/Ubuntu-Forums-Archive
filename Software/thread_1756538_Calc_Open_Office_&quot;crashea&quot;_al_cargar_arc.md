---
title: "Calc Open Office &quot;crashea&quot; al cargar archivos pesados."
date: 2011-05-12
forum: Software
---

### Post by granjero on 2011-05-12
Hola. Como les va?
Yo ando con un problema. Tengo una pc funcionando en producción que más que nada maneja archivos .xls que son archivos de finanzas que tienen muchisimas solapas y cientos de columnas. Son archivos que pesan entre 1,1Mb y 2,8Mb.

El problema es el siguiente:

La persona que la utiliza me cuenta que cada tanto cuando abre uno de estos archivos la pc se "cuelga" y por lo que vi una vez que estaba ahí cuando sucede el problema es que el panel inferior se llena de botones de ventanas sin título y las ventanas ya abiertas pierden el decorador de ventanas y la pc se congela.

Otra cosa que noté es que el consumo de memoria durante la carga de los archivos se dispara. La máquina tiene 1Gb de RAM y 1Gb de SWAP. Una vez terminada la carga inicial del archivo el consumo de RAM baja pero no así la SWAP.


También lo probé en mi PC de Escritorio que tiene 2GB de RAM y no llega a usar la SWAP pero el consumo de RAM durante la carga de los archivos es Sorprendente. 

A alguien se le ocurre algo que se pueda hacer para evitar estos cuelgues que me están dando unos dolores de cabeza increibles...

les cuento las características de la PC:
```

lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```

```
lshw
    description: Computer
    product: K8NF4G-SATA2
    vendor: TEMPLATE
    version: 1.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: K8NF4G-SATA2
       physical id: 0
       version: 1.00
       serial: 00000000
       slot: TBD
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.60 (01/11/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.2
          serial: TBD
          slot: CPUSocket
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System memory
          physical id: 3
          size: 1015MiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-display
          description: VGA compatible controller
          product: C51G [GeForce 6100]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:19 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fc000000-fcffffff memory:febe0000-febfffff(prefetchable)
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:5000(size=64) ioport:6000(size=64)
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:febde000-febdefff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:febdfc00-febdfcff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-disk
             description: ATA Disk
             product: WDC WD800BB-56JK
             vendor: Western Digital
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 05.0
             serial: WD-WCAMD9389453
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=1c630f04
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: d7e7aea1-28a0-49ac-8cd6-107654c2485d
                size: 976MiB
                capacity: 976MiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 73GiB
                capacity: 73GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 14GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 59GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S202J
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:f80(size=8) ioport:f00(size=4) ioport:e80(size=8) ioport:e00(size=4) ioport:e000(size=16) memory:febdd000-febddfff
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-multimedia
          description: Multimedia audio controller
          product: MCP51 AC97 Audio Controller
          vendor: nVidia Corporation
          physical id: 10.2
          bus info: pci@0000:00:10.2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: irq:23 ioport:d800(size=256) ioport:d400(size=256) memory:febdc000-febdcfff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a1
          serial: 00:13:8f:7d:f9:36
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.157 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:20 memory:febdb000-febdbfff ioport:dc00(size=8)
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
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

saludos!

---

### Post by guillermolisi on 2011-05-12
Creo que lo mas importante es conocer las caracteristicas de esas planillas.
El uso de tablas dinamicas y funciones de base de datos hace que una planilla que en disco ocupa algunos Mb en RAM se expanda increiblemente.

Si, ademas, hay otras planillas linkeadas, peor aun.

---

### Post by granjero on 2011-05-12
Guillermo gracias por responder, te cuento:

Las planillas son planillas de ingresos. La única fórmula que hay es autosuma. No están linkeadas las planilals nisiquiera entre las solapas. EL tema es que tiene muchísimas solapas; no pude ni contarlas. Deben ser como 100 o 150 solapas. Y tienen en promedio 50 o 60 columnas y no más de 100 filas.

Hoy a la mañana cambié la pc por otra con un core 2 y 1Gb de RAM. Para descartar algún tema de Hard. Y el problema persiste.

Lo que noto es que al momento de abrir los archivos, como mencionaba antes la RAM se dispara y también aumenta la SWAP. Mi teoría es que el crash se deba al agotamiento de memoria.

Pero lo que me da bronca es que se agote la memoria con unos archivos de exell.

Que pasa si le aumento la swap a 3 o 4 GB???

Otra cosa que noté es que si lo guardo como .ods el uso de memoria es muchísimo menor. Pero todavía no puedo migrar las extensiones. Son archivos que tienen años de trabajo.

Muchas gracias por responder!

Saludos!

---

### Post by guillermolisi on 2011-05-12
No veo problema en incrementar la particion swap, salvo el retrabajo de redimensionar particiones.

Por lo que comentas y en base a esa prueba con una planilla convertida a formato abierto, indudablemente hay algo en las originales que complica el trabajo del Spreadsheet.

Si esas planillas .xls se trabajan en Windows, tambien se va a los caños el uso de memoria real y virtual ?

---

### Post by juancarlospaco on 2011-05-12
En los Settings esta cuanta RAM se puede tomar el programa para los archivos y ejecucion, 
si no modificas eso podes ponerle 8 Gigas de RAM que sera lo mismo que tener 1Gb.

---

### Post by granjero on 2011-05-12
Guillermo, JuanCarlos, gracias por responder.

En Win no generan complicaciones estos archivos. El trabajo de redimensionar las particiones es ínfimo comparado con el trabajo que me están dando los cuelgues.

Juancarlos, cómo es eso que comentás de los Settings?
A dónde cambio esos seteos?

Saludos.

---

### Post by juancarlospaco on 2011-05-12
Herramientas--->Opciones--->Memoria

---

### Post by granjero on 2011-05-12
JuanCarlos.

No termino de entender cuál modificar.

Esto es lo que veo cuando voy donde me decís.

Saludos!

---

### Post by biale on 2011-05-13
Lo que sigue fue mas bien pensado para mejorar la performance de writer con imagenes, pero a falta de algo mejor te da una idea de los valores:

```

Herramientas/ opciones/ OpenOffice.org/ Memoria de trabajo:

Deshacer. Cantidad de pasos 			100 	&#8594; 	50 (pasos)
Graphics cache					20	&#8594;	120 Mb
Memory per object				5,2	&#8594;	20 Mb
Number of objects				20		(idem)
Eliminar (OO) de la memoria tras		10'	&#8594;	30'

```

Aunque parece estar tomando memoria, y mucha.

---

