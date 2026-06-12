---
title: "Programas con WINE, lentos"
date: 2012-05-27
forum: Software
---

### Post by Pictopix on 2012-05-27
Hace unos días decidí instalar Starcraft I (con la expasión Broodwar)  a mi pc, ya que hace tiempo no jugaba. Pero lo que ocurre es que  funciona terriblemente lento. Intente hacer de todo con wine y/o  playonlinux y nada. Muchas "soluciones" recurrían a configurar el  Xorg.conf y eso que ni lo tenia, así que recurrí a tutoriales para crear  un archivo xorg.conf y nada. Ademas muchas ayudas eran para ubuntus  antiguos. Tengo instalado Ubuntu 12.04 con LXDE (Lubuntu).

Aqui mis "fps"
```

glxgears

391 frames in 5.0 seconds = 78.108 FPS
425 frames in 5.0 seconds = 84.805 FPS
425 frames in 5.0 seconds = 84.804 FPS
426 frames in 5.0 seconds = 85.003 FPS
426 frames in 5.0 seconds = 85.002 FPS
425 frames in 5.0 seconds = 84.804 FPS
426 frames in 5.0 seconds = 85.004 FPS
426 frames in 5.0 seconds = 85.004 FPS
426 frames in 5.0 seconds = 85.004 FPS
426 frames in 5.0 seconds = 85.003 FPS
400 frames in 5.0 seconds = 79.817 FPS
425 frames in 5.0 seconds = 84.724 FPS
425 frames in 5.0 seconds = 84.882 FPS
419 frames in 5.0 seconds = 83.642 FPS
422 frames in 5.0 seconds = 84.368 FPS
426 frames in 5.0 seconds = 85.003 FPS
411 frames in 5.0 seconds = 82.012 FPS
384 frames in 5.0 seconds = 76.624 FPS
426 frames in 5.0 seconds = 85.003 FPS
416 frames in 5.1 seconds = 81.970 FPS
399 frames in 5.0 seconds = 79.689 FPS
425 frames in 5.0 seconds = 84.805 FPS
425 frames in 5.0 seconds = 84.990 FPS
393 frames in 5.0 seconds = 78.125 FPS
338 frames in 5.0 seconds = 67.545 FPS
396 frames in 5.0 seconds = 79.022 FPS
404 frames in 5.0 seconds = 80.614 FPS
353 frames in 5.0 seconds = 70.435 FPS
390 frames in 5.0 seconds = 77.819 FPS
```
---------------------------------------------------------------------------

lspci

```
$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
00:07.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 SE] (Secondary) (rev 01)
```---------------------------------------------------------------------------

lshw

```
descripción: Equipo de escritorio
    anchura: 32 bits
    capacidades: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuración: boot=normal chassis=desktop cpus=1
  *-core
       descripción: Placa base
       producto: MS-6785
       fabricante: MICRO-STAR INTERNATIONAL CO., LTD
       id físico: 0
     *-firmware
          descripción: BIOS
          fabricante: Phoenix Technologies, LTD
          id físico: 0
          versión: 6.00 PG
          date: 12/08/2003
          tamaño: 128KiB
          capacidad: 192KiB
          capacidades: isa pci pnp apm upgrade shadowing escd cdboot  bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720  int13floppy2880 int5printscreen int9keyboard int14serial int17printer  int10video acpi usb agp ls120boot zipboot
     *-cpu
          descripción: CPU
          producto: Intel(R) Celeron(R) CPU 2.60GHz
          fabricante: Intel Corp.
          id físico: 4
          información del bus: cpu@0
          versión: 15.2.9
          ranura: Socket 478
          tamaño: 2600MHz
          capacidad: 4GHz
          anchura: 32 bits
          reloj: 100MHz
          capacidades: boot fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe up pebs bts cid xtpr
          configuración: id=0
        *-cache:0
             descripción: L1 caché
             id físico: 8
             ranura: Internal Cache
             tamaño: 8KiB
             capacidad: 20KiB
             capacidades: synchronous internal write-back
        *-cache:1
             descripción: L2 caché
             id físico: 9
             ranura: External Cache
             tamaño: 128KiB
             capacidad: 128KiB
             capacidades: synchronous external write-back
     *-memory
          descripción: Memoria de sistema
          id físico: 19
          ranura: Placa de sistema o placa base
          tamaño: 1280MiB
          capacidad: 2GiB
        *-bank:0
             descripción: DIMM SDRAM Síncrono
             producto: None
             fabricante: None
             id físico: 0
             serie: None
             ranura: A0
             tamaño: 256MiB
             anchura: 64 bits
        *-bank:1
             descripción: DIMM SDRAM Síncrono
             producto: None
             fabricante: None
             id físico: 1
             serie: None
             ranura: A1
             tamaño: 1GiB
             anchura: 64 bits
     *-pci
          descripción: Host bridge
          producto: 645xx
          fabricante: Silicon Integrated Systems [SiS]
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 50
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=agpgart-sis latency=32
          recursos: irq:0 memoria:d0000000-d7ffffff
        *-pci
             descripción: PCI bridge
             producto: AGP Port (virtual PCI-to-PCI bridge)
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 1
             información del bus: pci@0000:00:01.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pci normal_decode bus_master
             recursos: ioport:9000(size=4096) memoria:e8000000-e9ffffff memoria:d8000000-e7ffffff
           *-display:0
                descripción: VGA compatible controller
                producto: RV280 [Radeon 9200 SE]
                fabricante: Hynix Semiconductor (Hyundai Electronics)
                id físico: 0
                información del bus: pci@0000:01:00.0
                versión: 01
                anchura: 32 bits
                reloj: 66MHz
                capacidades: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuración: driver=radeon latency=32 mingnt=8
                recursos: irq:16 memoria:d8000000-dfffffff  ioport:9000(size=256) memoria:e9000000-e900ffff  memoria:e8000000-e801ffff
           *-display:1 NO RECLAMADO
                descripción: Display controller
                producto: RV280 [Radeon 9200 SE] (Secondary)
                fabricante: Hynix Semiconductor (Hyundai Electronics)
                id físico: 0.1
                información del bus: pci@0000:01:00.1
                versión: 01
                anchura: 32 bits
                reloj: 66MHz
                capacidades: pm cap_list
                configuración: latency=32 mingnt=8
                recursos: memoria:e0000000-e7ffffff memoria:e9010000-e901ffff
        *-isa
             descripción: ISA bridge
             producto: SiS963 [MuTIOL Media IO] LPC Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 14
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master
             configuración: latency=0
        *-serial
             descripción: SMBus
             producto: SiS961/2/3 SMBus controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 2.1
             información del bus: pci@0000:00:02.1
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             configuración: driver=sis96x_smbus latency=0
             recursos: irq:0 ioport:10c0(size=32)
        *-firewire
             descripción: FireWire (IEEE 1394)
             producto: FireWire Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 2.3
             información del bus: pci@0000:00:02.3
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm ohci bus_master cap_list rom
             configuración: driver=firewire_ohci latency=32 maxlatency=12 mingnt=4
             recursos: irq:17 memoria:eb405000-eb405fff memoria:50000000-5001ffff
        *-ide
             descripción: IDE interface
             producto: 5513 IDE Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 2.5
             información del bus: pci@0000:00:02.5
             nombre lógico: scsi0
             nombre lógico: scsi1
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ide pm bus_master cap_list emulated
             configuración: driver=pata_sis latency=128
             recursos: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
           *-disk
                descripción: ATA Disk
                producto: ST380012A
                fabricante: Seagate
                id físico: 0
                información del bus: scsi@0:0.0.0
                nombre lógico: /dev/sda
                versión: 4.04
                serie: 5JV57TXX
                tamaño: 74GiB (80GB)
                capacidades: partitioned partitioned:dos
                configuración: ansiversion=5 signature=a5fba5fb
              *-volume:0
                   descripción: Extended partition
                   id físico: 1
                   información del bus: scsi@0:0.0.0,1
                   nombre lógico: /dev/sda1
                   tamaño: 953MiB
                   capacidad: 953MiB
                   capacidades: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      descripción: Linux swap / Solaris partition
                      id físico: 5
                      nombre lógico: /dev/sda5
                      capacidad: 953MiB
                      capacidades: nofs
              *-volume:1
                   descripción: Linux filesystem partition
                   fabricante: Linux
                   id físico: 2
                   información del bus: scsi@0:0.0.0,2
                   nombre lógico: /dev/sda2
                   nombre lógico: /boot
                   versión: 1.0
                   serie: 09b35745-53d0-45f7-b026-ad2bb7bac5e8
                   tamaño: 286MiB
                   capacidad: 286MiB
                   capacidades: primary bootable ext2 initialized
                   configuración: filesystem=ext2 modified=2012-05-17  22:09:31 mount.fstype=ext2 mount.options=rw,relatime,errors=continue  state=mounted
              *-volume:2
                   descripción: partición EXT4
                   fabricante: Linux
                   id físico: 3
                   información del bus: scsi@0:0.0.0,3
                   nombre lógico: /dev/sda3
                   nombre lógico: /
                   versión: 1.0
                   serie: 30416963-90e6-4345-bf20-dd1bf5e23768
                   tamaño: 14GiB
                   capacidad: 14GiB
                   capacidades: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuración: created=2012-03-25 21:00:25  filesystem=ext4 lastmountpoint=/ modified=2012-05-13 22:06:13  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered  mounted=2012-05-17 22:09:16 state=mounted
              *-volume:3
                   descripción: partición EXT4
                   fabricante: Linux
                   id físico: 4
                   información del bus: scsi@0:0.0.0,4
                   nombre lógico: /dev/sda4
                   nombre lógico: /home
                   versión: 1.0
                   serie: 1ec4dae8-5a6a-4617-b6d5-69834f06039f
                   tamaño: 58GiB
                   capacidad: 58GiB
                   capacidades: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuración: created=2012-03-25 21:00:30  filesystem=ext4 lastmountpoint=/home modified=2012-05-17 22:09:16  mount.fstype=ext4  mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered  mounted=2012-05-17 22:09:16 state=mounted
           *-cdrom
                descripción: DVD-RAM writer
                producto: CD/DVDW SH-S182M
                fabricante: TSSTcorp
                id físico: 1
                información del bus: scsi@1:0.0.0
                nombre lógico: /dev/cdrom
                nombre lógico: /dev/cdrw
                nombre lógico: /dev/dvd
                nombre lógico: /dev/dvdrw
                nombre lógico: /dev/sr0
                versión: SB02
                capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuración: ansiversion=5 status=nodisc
        *-multimedia
             descripción: Multimedia audio controller
             producto: SiS7012 AC'97 Sound Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 2.7
             información del bus: pci@0000:00:02.7
             versión: a0
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list
             configuración: driver=snd_intel8x0 latency=32 maxlatency=11 mingnt=52
             recursos: irq:18 ioport:a000(size=256) ioport:a400(size=128)
        *-usb:0
             descripción: USB controller
             producto: USB 1.1 Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 3
             información del bus: pci@0000:00:03.0
             versión: 0f
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ohci bus_master
             configuración: driver=ohci_hcd latency=32 maxlatency=80
             recursos: irq:20 memoria:eb400000-eb400fff
        *-usb:1
             descripción: USB controller
             producto: USB 1.1 Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 3.1
             información del bus: pci@0000:00:03.1
             versión: 0f
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ohci bus_master
             configuración: driver=ohci_hcd latency=32 maxlatency=80
             recursos: irq:21 memoria:eb401000-eb401fff
        *-usb:2
             descripción: USB controller
             producto: USB 1.1 Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 3.2
             información del bus: pci@0000:00:03.2
             versión: 0f
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ohci bus_master
             configuración: driver=ohci_hcd latency=32 maxlatency=80
             recursos: irq:22 memoria:eb402000-eb402fff
        *-usb:3
             descripción: USB controller
             producto: USB 2.0 Controller
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 3.3
             información del bus: pci@0000:00:03.3
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=32 maxlatency=80
             recursos: irq:23 memoria:eb403000-eb403fff
        *-network
             descripción: Ethernet interface
             producto: SiS900 PCI Fast Ethernet
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 4
             información del bus: pci@0000:00:04.0
             nombre lógico: eth0
             versión: 91
             serie: 00:0c:76:c0:a0:03
             tamaño: 100Mbit/s
             capacidad: 100Mbit/s
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuración: autonegotiation=on broadcast=yes  driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full  ip=190.163.183.80 latency=32 link=yes maxlatency=11 mingnt=52  multicast=yes port=MII speed=100Mbit/s
             recursos: irq:19 ioport:a800(size=256) memoria:eb404000-eb404fff memoria:50020000-5003ffff
        *-communication:0
             descripción: Communication controller
             producto: PCI 9835 Multi-I/O Controller
             fabricante: NetMos Technology
             id físico: 6
             información del bus: pci@0000:00:06.0
             versión: 01
             anchura: 32 bits
             reloj: 33MHz
             configuración: driver=parport_serial latency=32
             recursos: irq:17 ioport:ac00(size=8) ioport:b000(size=8)  ioport:b400(size=8) ioport:b800(size=8) ioport:bc00(size=8)  ioport:c000(size=16)
        *-communication:1 NO RECLAMADO
             descripción: Communication controller
             producto: 536EP Data Fax Modem
             fabricante: Intel Corporation
             id físico: 7
             información del bus: pci@0000:00:07.0
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list
             configuración: latency=32
             recursos: memoria:eb000000-eb3fffff
```Saludos

---

### Post by juancarlospaco on 2012-05-27
Drivers Propietarios de ATI ...?

---

### Post by Pictopix on 2012-05-28
Em, realmente nose como comprobar eso, me podrias decir donde puedo ver esos datos?

Saludos y gracias por responder

---

### Post by dirty fingers on 2012-06-20
Jamas un juego con wine funciono rápido. No pierdas tiempo, si te gusta jugar, comprate una consola o instala winbug en otra partición.

---

