---
title: "[resolucion de pantalla y 2d mode]"
date: 2012-05-04
forum: Uruguay Team
---

### Post by rockdrigo16 on 2012-05-04
bueno la verdad me tiene medio lleno esto.
Aacabo de instalar ubuntu 12.04
y cuando endo entro a MUnity me dice
"su ubuntu 12.04 is running in 2d mode
Many features will not be available"
Como cambio eso del modo 2d? cierro sesion y vuelvo a entrar (en ubuntu mode) y me lo sigue diciendo
no elijo la sesion 2d :S
y otra cosa es que no puedo cambiar la resolucion de la pantalla
esta fija en 1024 x 768 no me da mas opciones.
la computadora que tengo es una acer aspire 5732z.
por otro lado me dijieron que debía de ser porque para instalarlo me aparecia la pantalla en negro y use eso del nomodeset ([http://www.ubuntizando.com/2012/04/23/como-resolver-el-problema-de-la-pa](http://www.ubuntizando.com/2012/04/23/como-resolver-el-problema-de-la-pa)...)
Entonces reinverti los cambios
hice sudo gedit /etc/default/grub
y volvi a dejar la linea como estaba antes:
puse GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".
Y inicio ubuntu sin problemas, ya no se puso la pantalla negra. solo que sigue estando en modo 2d y sigo sin poder cambiar la resolucion de la pantalla
alguna ayuda por favor?
me tiene medio lleno ver las cosas estiradas y no poder tocar nada porque esta en 2d mode.
muchas gracias

---

### Post by samigina on 2012-05-04
Que tarjeta gráfica tiene tu equipo? Estas en 2d porque ubuntu no esta usando el controlador de la gráfica (eso hace nomodeset).

Abre una terminal y escribe lshw y pega aqui el resultado, también de lspci.

---

### Post by rockdrigo16 on 2012-05-05
Con el tema que no puedo cambiar la resolución de la pantalla me dijeron que pruebe con el programa resapplet, lo baje del centro de software pero cuando lo ejecuto no arranca.
la única resolución que me da a elegir es 1024x768 y se ve estirado.

También (con el tema de la resolución) eh intentado modificar /etc/X11/xorg.conf como decían por ahi, pero por no tenia el archivo ese, lo que e hecho es esto:
ctrl + alt + f1
sudo su
service lingthdm stop
xorg -configure
mv /root/xorg.conf.new /etc/X11/xorg.conf
gedit /etc/X11/xorg.conf
pero no encuentro para agregarle resoluciones.

No se si viene por este lado la solución de la resolución de la pantalla :S


Y tambien sigo en 2d mode.
te tiro las salidas del lshw y lspci.
Muchas gracias



/*-------------------------------------------------------------*/
$ sudo lshw


misterfire                
    descripción: Notebook
    producto: Aspire 5732Z (Montevina_Fab)
    fabricante: Acer
    versión: V3.04
    serie: LXPGU08009002295141601
    anchura: 32 bits
    capacidades: smbios-2.4 dmi-2.4
    configuración: boot=normal chassis=notebook family=Intel_Mobile sku=Montevina_Fab uuid=65333665-6166-6139-3036-705AB6172CCA
  *-core
       descripción: Placa base
       producto: Aspire 5732Z
       fabricante: Acer
       id físico: 0
       versión: V3.04
       serie: Base Board Serial Number
       ranura: Base Board Chassis Location
     *-firmware
          descripción: BIOS
          fabricante: Acer
          id físico: 0
          versión: V3.04
          date: 12/16/2009
          tamaño: 1MiB
          capacidades: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          descripción: Memoria de sistema
          id físico: 14
          ranura: Placa de sistema o placa base
          tamaño: 2GiB
        *-bank:0
             descripción: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-04-18 06:53+0000X-Generator: Launchpad (build 15099) Síncrono 800 MHz (1,2 ns)
             producto: 000000000000000000000000000000000000
             fabricante: 0000000000000000
             id físico: 0
             serie: 00000000
             ranura: DIMM0
             tamaño: 1GiB
             reloj: 800MHz (1.2ns)
        *-bank:1
             descripción: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-04-18 06:53+0000X-Generator: Launchpad (build 15099) Síncrono 800 MHz (1,2 ns)
             producto: 000000000000000000000000000000000000
             fabricante: 0000000000000000
             id físico: 1
             serie: 00000000
             ranura: DIMM2
             tamaño: 1GiB
             reloj: 800MHz (1.2ns)
     *-cpu
          descripción: CPU
          producto: Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
          fabricante: Intel Corp.
          id físico: 1f
          información del bus: cpu@0
          versión: 6.7.10
          serie: 0001-067A-0000-0000-0000-0000
          ranura: uPGA-478
          tamaño: 2200MHz
          capacidad: 2200MHz
          anchura: 64 bits
          reloj: 200MHz
          capacidades: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuración: id=0
        *-cache:0
             descripción: L2 caché
             id físico: 20
             ranura: L2 Cache
             tamaño: 1MiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
        *-cache:1
             descripción: L1 caché
             id físico: 22
             ranura: L1 Cache
             tamaño: 32KiB
             capacidad: 32KiB
             capacidades: synchronous internal write-back data
        *-logicalcpu:0
             descripción: CPU lógica
             id físico: 0.1
             anchura: 64 bits
             capacidades: logical
        *-logicalcpu:1
             descripción: CPU lógica
             id físico: 0.2
             anchura: 64 bits
             capacidades: logical
     *-cache
          descripción: L1 caché
          id físico: 21
          ranura: L1 Cache
          tamaño: 32KiB
          capacidad: 32KiB
          capacidades: synchronous internal write-back instruction
     *-pci
          descripción: Host bridge
          producto: Mobile 4 Series Chipset Memory Controller Hub
          fabricante: Intel Corporation
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 09
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=agpgart-intel
          recursos: irq:0
        *-display:0 NO RECLAMADO
             descripción: VGA compatible controller
             producto: Mobile 4 Series Chipset Integrated Graphics Controller
             fabricante: Intel Corporation
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 09
             anchura: 64 bits
             reloj: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list
             configuración: latency=0
             recursos: memoria:90000000-903fffff memoria:80000000-8fffffff ioport:50f0(size=8)
        *-display:1 NO RECLAMADO
             descripción: Display controller
             producto: Mobile 4 Series Chipset Integrated Graphics Controller
             fabricante: Intel Corporation
             id físico: 2.1
             información del bus: pci@0000:00:02.1
             versión: 09
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list
             configuración: latency=0
             recursos: memoria:93400000-934fffff
        *-usb:0
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB UHCI Controller #4
             fabricante: Intel Corporation
             id físico: 1a
             información del bus: pci@0000:00:1a.0
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=0
             recursos: irq:20 ioport:50c0(size=32)
        *-usb:1
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB2 EHCI Controller #2
             fabricante: Intel Corporation
             id físico: 1a.7
             información del bus: pci@0000:00:1a.7
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=0
             recursos: irq:21 memoria:96704c00-96704fff
        *-multimedia
             descripción: Audio device
             producto: 82801I (ICH9 Family) HD Audio Controller
             fabricante: Intel Corporation
             id físico: 1b
             información del bus: pci@0000:00:1b.0
             versión: 03
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuración: driver=snd_hda_intel latency=0
             recursos: irq:46 memoria:96700000-96703fff
        *-pci:0
             descripción: PCI bridge
             producto: 82801I (ICH9 Family) PCI Express Port 1
             fabricante: Intel Corporation
             id físico: 1c
             información del bus: pci@0000:00:1c.0
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:40 ioport:4000(size=4096) memoria:95700000-966fffff ioport:90400000(size=16777216)
        *-pci:1
             descripción: PCI bridge
             producto: 82801I (ICH9 Family) PCI Express Port 2
             fabricante: Intel Corporation
             id físico: 1c.1
             información del bus: pci@0000:00:1c.1
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:41 ioport:3000(size=4096) memoria:94600000-956fffff ioport:91400000(size=16777216)
           *-network
                descripción: Interfaz inalámbrica
                producto: AR928X Wireless Network Adapter (PCI-Express)
                fabricante: Atheros Communications Inc.
                id físico: 0
                información del bus: pci@0000:04:00.0
                nombre lógico: wlan0
                versión: 01
                serie: 70:1a:04:d2:6e:3c
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuración: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                recursos: irq:17 memoria:94600000-9460ffff
        *-pci:2
             descripción: PCI bridge
             producto: 82801I (ICH9 Family) PCI Express Port 3
             fabricante: Intel Corporation
             id físico: 1c.2
             información del bus: pci@0000:00:1c.2
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:42 ioport:1000(size=8192) memoria:93500000-945fffff ioport:92400000(size=16777216)
           *-network
                descripción: Ethernet interface
                producto: AR8132 Fast Ethernet
                fabricante: Atheros Communications Inc.
                id físico: 0
                información del bus: pci@0000:05:00.0
                nombre lógico: eth0
                versión: c0
                serie: 70:5a:b6:17:2c:ca
                capacidad: 100Mbit/s
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                recursos: irq:44 memoria:93500000-9353ffff ioport:1000(size=128)
        *-usb:2
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB UHCI Controller #1
             fabricante: Intel Corporation
             id físico: 1d
             información del bus: pci@0000:00:1d.0
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=0
             recursos: irq:23 ioport:50a0(size=32)
        *-usb:3
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB UHCI Controller #2
             fabricante: Intel Corporation
             id físico: 1d.1
             información del bus: pci@0000:00:1d.1
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=0
             recursos: irq:19 ioport:5080(size=32)
        *-usb:4
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB UHCI Controller #3
             fabricante: Intel Corporation
             id físico: 1d.2
             información del bus: pci@0000:00:1d.2
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=0
             recursos: irq:20 ioport:5060(size=32)
        *-usb:5
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB UHCI Controller #6
             fabricante: Intel Corporation
             id físico: 1d.3
             información del bus: pci@0000:00:1d.3
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=0
             recursos: irq:18 ioport:5040(size=32)
        *-usb:6
             descripción: USB controller
             producto: 82801I (ICH9 Family) USB2 EHCI Controller #1
             fabricante: Intel Corporation
             id físico: 1d.7
             información del bus: pci@0000:00:1d.7
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=0
             recursos: irq:23 memoria:96704800-96704bff
        *-pci:3
             descripción: PCI bridge
             producto: 82801 Mobile PCI Bridge
             fabricante: Intel Corporation
             id físico: 1e
             información del bus: pci@0000:00:1e.0
             versión: 93
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci subtractive_decode bus_master cap_list
        *-isa
             descripción: ISA bridge
             producto: ICH9M LPC Interface Controller
             fabricante: Intel Corporation
             id físico: 1f
             información del bus: pci@0000:00:1f.0
             versión: 03
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master cap_list
             configuración: latency=0
        *-storage
             descripción: SATA controller
             producto: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             fabricante: Intel Corporation
             id físico: 1f.2
             información del bus: pci@0000:00:1f.2
             nombre lógico: scsi0
             nombre lógico: scsi1
             versión: 03
             anchura: 32 bits
             reloj: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuración: driver=ahci latency=0
             recursos: irq:43 ioport:50e8(size=8) ioport:50fc(size=4) ioport:50e0(size=8) ioport:50f8(size=4) ioport:5020(size=32) memoria:96704000-967047ff
           *-disk
                descripción: ATA Disk
                producto: TOSHIBA MK2555GS
                fabricante: Toshiba
                id físico: 0
                información del bus: scsi@0:0.0.0
                nombre lógico: /dev/sda
                versión: FG00
                serie: Z9O2F1M5S
                tamaño: 232GiB (250GB)
                capacidades: partitioned partitioned:dos
                configuración: ansiversion=5 signature=852a68b4
              *-volume:0
                   descripción: Windows NTFS volumen
                   id físico: 1
                   información del bus: scsi@0:0.0.0,1
                   nombre lógico: /dev/sda1
                   versión: 3.1
                   serie: dcf3-f988
                   tamaño: 98MiB
                   capacidad: 100MiB
                   capacidades: primary bootable ntfs initialized
                   configuración: clustersize=4096 created=2010-06-21 18:01:43 filesystem=ntfs label=Reservado para el sistema state=clean
              *-volume:1
                   descripción: Windows NTFS volumen
                   id físico: 2
                   información del bus: scsi@0:0.0.0,2
                   nombre lógico: /dev/sda2
                   versión: 3.1
                   serie: 1e11a0ab-61be-b840-9cc3-e73251a99109
                   tamaño: 186GiB
                   capacidad: 186GiB
                   capacidades: primary ntfs initialized
                   configuración: clustersize=4096 created=2010-07-08 11:50:23 filesystem=ntfs label=Acer modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   descripción: Extended partition
                   id físico: 3
                   información del bus: scsi@0:0.0.0,3
                   nombre lógico: /dev/sda3
                   tamaño: 46GiB
                   capacidad: 46GiB
                   capacidades: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      descripción: Linux filesystem partition
                      id físico: 5
                      nombre lógico: /dev/sda5
                      nombre lógico: /
                      capacidad: 44GiB
                      configuración: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      descripción: Linux swap / Solaris partition
                      id físico: 6
                      nombre lógico: /dev/sda6
                      capacidad: 1977MiB
                      capacidades: nofs
           *-cdrom
                descripción: DVD-RAM writer
                producto: DVD RW AD-7585H
                fabricante: Optiarc
                id físico: 1
                información del bus: scsi@1:0.0.0
                nombre lógico: /dev/cdrom
                nombre lógico: /dev/cdrw
                nombre lógico: /dev/dvd
                nombre lógico: /dev/dvdrw
                nombre lógico: /dev/sr0
                versión: KX04
                capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuración: ansiversion=5 status=nodisc
        *-serial NO RECLAMADO
             descripción: SMBus
             producto: 82801I (ICH9 Family) SMBus Controller
             fabricante: Intel Corporation
             id físico: 1f.3
             información del bus: pci@0000:00:1f.3
             versión: 03
             anchura: 64 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: memoria:96705000-967050ff ioport:5000(size=32)
     *-scsi
          id físico: 1
          información del bus: usb@1:1
          nombre lógico: scsi8
          nombre lógico: scsi7
          capacidades: emulated scsi-host
          configuración: driver=usb-storage
        *-disk
             descripción: SCSI Disk
             id físico: 0
             información del bus: scsi@8:0.0.0
             nombre lógico: /dev/sdb
        *-cdrom
             descripción: SCSI CD-ROM
             producto: Mass Storage
             fabricante: HUAWEI
             id físico: 1
             información del bus: scsi@7:0.0.0
             nombre lógico: /dev/cdrom1
             nombre lógico: /dev/sr1
             versión: 2.31
             capacidades: removable audio
             configuración: ansiversion=2 status=ready
           *-medium
                id físico: 0
                nombre lógico: /dev/cdrom1
                capacidades: partitioned partitioned:mac
              *-volume:0 NO RECLAMADO
                   descripción: Apple partition map
                   id físico: 1
                   capacidad: 17KiB
              *-volume:1 NO RECLAMADO
                   descripción: Apple HFS
                   fabricante: Mac OS X
                   id físico: 2
                   versión: 4
                   serie: 00000000-0000-0000-0000-000000001000
                   tamaño: 24MiB
                   capacidad: 24MiB
                   capacidades: hfsplus initialized
                   configuración: checked=1903-12-31 20:15:16 created=2009-03-23 10:36:54 filesystem=hfsplus lastmountedby=10.0 modified=2009-03-23 07:36:54 state=clean
  *-battery
       descripción: Ion litio Battery
       producto: Li-lon Battery
       fabricante: -Virtual Battery 0-
       id físico: 1
       versión: 10/12/2007
       serie: Battery 0
       ranura: Fake
  *-power NO RECLAMADO
       descripción: OEM_Define1
       producto: OEM_Define4
       fabricante: OEM_Define2
       id físico: 2
       versión: OEM_Define5
       serie: OEM_Define2
       capacidad: 75mWh



/*-------------------------------------------------------------*/
$ lspci


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)

---

### Post by samigina on 2012-05-06
Hola, disculpa la tardanza.

Primero, el archivo .xorg hace varias ediciones ya no es necesario, solo con algunas ATI o Nvidia se necesita, la tuya es intel. Ten cuidado siguiendo consejos que no coincidan con tu hardware.

Siendo tu tarjeta una Intel deberias tener aceleración 3d por defecto, pero parece que efectivamente el driver no está intalado. Verifiquemoslo con este comando:

"glxinfo | grep render"

Este nos informara si tienes o no aceleración y si el driver está instalado.

Algo importante, qué versión de Ubuntu estas usando?

---

### Post by guillermolisi on 2012-05-07
Podrias exponer el contenido del log /var/log/dmesg ?
Las obtenes ingresando en terminal/consola
```
dmesg
``` y las pegas para verificar que sucede con el reconocimiento de ACPI (no esta reconociendo varios dispositivos, entre ellos el administrador de energia - ultimas lineas del archivo que expusiste.

Tambien seria interesante ver el contenido de /var/log/Xorg.0.log para ver que hace el SO con el reconocimiento de la placa de video.

---

### Post by rockdrigo16 on 2012-05-07
muchas gracias. Perdón la demora.
estoy usando ubuntu 12.04 antes tenia 10.04 y el único problema que tuve (con 10.04) era que no le bajaba el brillo en la pantalla.
les dejo aca las salidas.
quedo medio largo :S je

$ sudo apt-get install mesa-utils
$ glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".








/*----------------------------------------------------------------------*/


$ dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic-pae (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 (Ubuntu 3.2.0-24.37-generic-pae 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b96c000 (usable)
[    0.000000]  BIOS-e820: 000000007b96c000 - 000000007b9bf000 (reserved)
[    0.000000]  BIOS-e820: 000000007b9bf000 - 000000007ba82000 (usable)
[    0.000000]  BIOS-e820: 000000007ba82000 - 000000007babf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007babf000 - 000000007baec000 (usable)
[    0.000000]  BIOS-e820: 000000007baec000 - 000000007baff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007baff000 - 000000007bb00000 (usable)
[    0.000000]  BIOS-e820: 000000007bb00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Acer       Aspire 5732Z    /Aspire 5732Z    , BIOS V3.04 12/16/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7bb00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   1 base 0FFFC0000 mask FFFFE0000 uncachable
[    0.000000]   2 base 000000000 mask FC0000000 write-back
[    0.000000]   3 base 040000000 mask FC0000000 write-back
[    0.000000]   4 base 07C000000 mask FFC000000 uncachable
[    0.000000]   5 base 07BC00000 mask FFFC00000 uncachable
[    0.000000]   6 base 07BB00000 mask FFFF00000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 36500000 - 37278000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 7bafe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 7bafd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 7baee000 0984B (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 7ba8f000 00040
[    0.000000] ACPI: HPET 7bafc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 7bafb000 0006C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 7bafa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASF! 7baf9000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 7baf8000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 7baed000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 7baec000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007bb00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007b96c
[    0.000000]     0: 0x0007b9bf -> 0x0007ba82
[    0.000000]     0: 0x0007babf -> 0x0007baec
[    0.000000]     0: 0x0007baff -> 0x0007bb00
[    0.000000] On node 0 totalpages: 506347
[    0.000000] free_area_init_node: node 0, pgdat c186b480, node_mem_map f5588200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2175 pages used for memmap
[    0.000000]   HighMem zone: 275936 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7800000 s34240 r0 d23104 u524288
[    0.000000] pcpu-alloc: s34240 r0 d23104 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 502388
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=fa9771ea-a622-46c7-b866-af4384bd092f ro quiet splash nomodeset acpi_osi=Linux vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 8105728 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007bb00)
[    0.000000] Memory: 1976388k/2026496k available (5825k kernel code, 49000k reserved, 2850k data, 740k init, 1112444k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
[    0.000000]       .data : 0xc15b04bc - 0xc1878d00   (2850 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b04bc   (5825 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.356 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4388.71 BogoMIPS (lpj=8777424)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004032] Security Framework initialized
[    0.004051] AppArmor: AppArmor initialized
[    0.004053] Yama: becoming mindful.
[    0.004109] Mount-cache hash table entries: 512
[    0.004249] Initializing cgroup subsys cpuacct
[    0.004256] Initializing cgroup subsys memory
[    0.004264] Initializing cgroup subsys devices
[    0.004266] Initializing cgroup subsys freezer
[    0.004269] Initializing cgroup subsys blkio
[    0.004275] Initializing cgroup subsys perf_event
[    0.004303] CPU: Physical Processor ID: 0
[    0.004305] CPU: Processor Core ID: 0
[    0.004308] mce: CPU supports 6 MCE banks
[    0.004315] CPU0: Thermal monitoring enabled (TM1)
[    0.004319] using mwait in idle threads.
[    0.008577] ACPI: Core revision 20110623
[    0.016013] ftrace: allocating 26594 entries in 53 pages
[    0.020062] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020447] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060305] CPU0: Intel Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz stepping 0a
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.152040] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152083] Brought up 2 CPUs
[    0.152085] Total of 2 processors activated (8777.63 BogoMIPS).
[    0.153136] devtmpfs: initialized
[    0.153136] EVM: security.selinux
[    0.153136] EVM: security.SMACK64
[    0.153136] EVM: security.capability
[    0.153136] PM: Registering ACPI NVS region at 7ba82000 (249856 bytes)
[    0.153180] print_constraints: dummy: 
[    0.153213] RTC time: 19:19:09, date: 05/07/12
[    0.153258] NET: Registered protocol family 16
[    0.153292] Trying to unpack rootfs image as initramfs...
[    0.153414] EISA bus registered
[    0.153433] ACPI: bus type pci registered
[    0.153517] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.153521] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.153523] PCI: Using MMCONFIG for extended config space
[    0.153525] PCI: Using configuration type 1 for base access
[    0.156409] bio: create slab <bio-0> at 0
[    0.156510] ACPI: Added _OSI(Module Device)
[    0.156513] ACPI: Added _OSI(Processor Device)
[    0.156515] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156518] ACPI: Added _OSI(Processor Aggregator Device)
[    0.156520] ACPI: Added _OSI(Linux)
[    0.158955] ACPI: EC: Look up EC in DSDT
[    0.161386] ACPI: Executed 1 blocks of module-level executable AML code
[    0.163334] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
[    0.165956] ACPI: SSDT 7b98dc98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.168383] ACPI: Dynamic OEM Table Load:
[    0.168387] ACPI: SSDT   (null) 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.168541] ACPI: SSDT 7b98b598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.169097] ACPI: Dynamic OEM Table Load:
[    0.169101] ACPI: SSDT   (null) 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.216379] ACPI: SSDT 7b98ce18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.217020] ACPI: Dynamic OEM Table Load:
[    0.217024] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.240186] ACPI: SSDT 7b98df18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.240805] ACPI: Dynamic OEM Table Load:
[    0.240808] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.308129] ACPI: Interpreter enabled
[    0.308144] ACPI: (supports S0 S3 S4 S5)
[    0.308190] ACPI: Using IOAPIC for interrupt routing
[    0.463308] Freeing initrd memory: 13792k freed
[    0.513846] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.514095] ACPI: No dock devices found.
[    0.514098] HEST: Table not found.
[    0.514103] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.514434] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.515074] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.515078] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.515081] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.515085] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
[    0.515101] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.515129] DMAR: Forcing write-buffer flush capability
[    0.515158] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.515173] pci 0000:00:02.0: reg 10: [mem 0x90000000-0x903fffff 64bit]
[    0.515183] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.515190] pci 0000:00:02.0: reg 20: [io  0x50f0-0x50f7]
[    0.515231] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.515244] pci 0000:00:02.1: reg 10: [mem 0x93400000-0x934fffff 64bit]
[    0.515329] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.515386] pci 0000:00:1a.0: reg 20: [io  0x50c0-0x50df]
[    0.515463] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.516036] pci 0000:00:1a.7: reg 10: [mem 0x96704c00-0x96704fff]
[    0.520815] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.520821] pci 0000:00:1a.7: PME# disabled
[    0.520849] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.520867] pci 0000:00:1b.0: reg 10: [mem 0x96700000-0x96703fff 64bit]
[    0.520948] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.520953] pci 0000:00:1b.0: PME# disabled
[    0.520976] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.521060] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.521064] pci 0000:00:1c.0: PME# disabled
[    0.521090] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.521172] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.521177] pci 0000:00:1c.1: PME# disabled
[    0.521202] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.521285] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.521290] pci 0000:00:1c.2: PME# disabled
[    0.521321] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.521377] pci 0000:00:1d.0: reg 20: [io  0x50a0-0x50bf]
[    0.521445] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.521501] pci 0000:00:1d.1: reg 20: [io  0x5080-0x509f]
[    0.521568] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.521624] pci 0000:00:1d.2: reg 20: [io  0x5060-0x507f]
[    0.521693] pci 0000:00:1d.3: [8086:2939] type 0 class 0x000c03
[    0.521749] pci 0000:00:1d.3: reg 20: [io  0x5040-0x505f]
[    0.521825] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.522581] pci 0000:00:1d.7: reg 10: [mem 0x96704800-0x96704bff]
[    0.527000] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.527006] pci 0000:00:1d.7: PME# disabled
[    0.527028] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.527102] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.527238] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.527260] pci 0000:00:1f.2: reg 10: [io  0x50e8-0x50ef]
[    0.527270] pci 0000:00:1f.2: reg 14: [io  0x50fc-0x50ff]
[    0.527279] pci 0000:00:1f.2: reg 18: [io  0x50e0-0x50e7]
[    0.527289] pci 0000:00:1f.2: reg 1c: [io  0x50f8-0x50fb]
[    0.527298] pci 0000:00:1f.2: reg 20: [io  0x5020-0x503f]
[    0.527308] pci 0000:00:1f.2: reg 24: [mem 0x96704000-0x967047ff]
[    0.527363] pci 0000:00:1f.2: PME# supported from D3hot
[    0.527367] pci 0000:00:1f.2: PME# disabled
[    0.527387] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.527404] pci 0000:00:1f.3: reg 10: [mem 0x96705000-0x967050ff 64bit]
[    0.527430] pci 0000:00:1f.3: reg 20: [io  0x5000-0x501f]
[    0.527507] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.527512] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.527517] pci 0000:00:1c.0:   bridge window [mem 0x95700000-0x966fffff]
[    0.527524] pci 0000:00:1c.0:   bridge window [mem 0x90400000-0x913fffff 64bit pref]
[    0.527591] pci 0000:04:00.0: [168c:002a] type 0 class 0x000280
[    0.527617] pci 0000:04:00.0: reg 10: [mem 0x94600000-0x9460ffff 64bit]
[    0.527746] pci 0000:04:00.0: supports D1
[    0.527748] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.527753] pci 0000:04:00.0: PME# disabled
[    0.527782] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.527794] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.527798] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.527803] pci 0000:00:1c.1:   bridge window [mem 0x94600000-0x956fffff]
[    0.527810] pci 0000:00:1c.1:   bridge window [mem 0x91400000-0x923fffff 64bit pref]
[    0.527878] pci 0000:05:00.0: [1969:1062] type 0 class 0x000200
[    0.527904] pci 0000:05:00.0: reg 10: [mem 0x93500000-0x9353ffff 64bit]
[    0.527919] pci 0000:05:00.0: reg 18: [io  0x1000-0x107f]
[    0.528077] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.528082] pci 0000:05:00.0: PME# disabled
[    0.536052] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
[    0.536056] pci 0000:00:1c.2:   bridge window [io  0x1000-0x2fff]
[    0.536061] pci 0000:00:1c.2:   bridge window [mem 0x93500000-0x945fffff]
[    0.536068] pci 0000:00:1c.2:   bridge window [mem 0x92400000-0x933fffff 64bit pref]
[    0.536141] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.536153] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.536155] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.536158] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.536161] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
[    0.536183] pci_bus 0000:00: on NUMA node 0
[    0.536187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.536487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.536543] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.536598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.536668]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.536671]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.536673] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.542289] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.542353] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.542415] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.542476] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
[    0.542539] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.542601] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.542664] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.542726] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.542861] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.542861] vgaarb: loaded
[    0.542861] vgaarb: bridge control possible 0000:00:02.0
[    0.542861] i2c-core: driver [aat2870] using legacy suspend method
[    0.542861] i2c-core: driver [aat2870] using legacy resume method
[    0.542861] SCSI subsystem initialized
[    0.542861] libata version 3.00 loaded.
[    0.542861] usbcore: registered new interface driver usbfs
[    0.542861] usbcore: registered new interface driver hub
[    0.542861] usbcore: registered new device driver usb
[    0.542861] PCI: Using ACPI for IRQ routing
[    0.544992] PCI: pci_cache_line_size set to 64 bytes
[    0.545081] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.545084] reserve RAM buffer: 000000007b96c000 - 000000007bffffff 
[    0.545088] reserve RAM buffer: 000000007ba82000 - 000000007bffffff 
[    0.545091] reserve RAM buffer: 000000007baec000 - 000000007bffffff 
[    0.545094] reserve RAM buffer: 000000007bb00000 - 000000007bffffff 
[    0.545214] NetLabel: Initializing
[    0.545216] NetLabel:  domain hash size = 128
[    0.545218] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.545228] NetLabel:  unlabeled traffic allowed by default
[    0.545361] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.545361] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.545361] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.548162] Switching to clocksource hpet
[    0.557429] AppArmor: AppArmor Filesystem Enabled
[    0.557465] pnp: PnP ACPI init
[    0.557486] ACPI: bus type pnp registered
[    0.557858] pnp 00:00: [bus 00-ff]
[    0.557861] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.557864] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.557867] pnp 00:00: [io  0x0d00-0xffff window]
[    0.557873] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.557875] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.557878] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.557880] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.557883] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.557885] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.557888] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.557890] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.557892] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.557895] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.557897] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.557900] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.557902] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.557904] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.557907] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.557909] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.558016] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.656179] pnp 00:01: [io  0x002e-0x002f]
[    0.656182] pnp 00:01: [io  0x004e-0x004f]
[    0.656184] pnp 00:01: [io  0x164e-0x164f]
[    0.656186] pnp 00:01: [io  0x0061]
[    0.656188] pnp 00:01: [io  0x0070]
[    0.656190] pnp 00:01: [io  0x0080]
[    0.656192] pnp 00:01: [io  0x0092]
[    0.656194] pnp 00:01: [io  0x00b2-0x00b3]
[    0.656196] pnp 00:01: [io  0x0063]
[    0.656198] pnp 00:01: [io  0x0065]
[    0.656200] pnp 00:01: [io  0x0067]
[    0.656202] pnp 00:01: [io  0x0600-0x060f]
[    0.656204] pnp 00:01: [io  0x0610]
[    0.656206] pnp 00:01: [io  0x0800-0x080f]
[    0.656208] pnp 00:01: [io  0x0810-0x0817]
[    0.656210] pnp 00:01: [io  0x0820-0x0823]
[    0.656212] pnp 00:01: [io  0x0400-0x047f]
[    0.656214] pnp 00:01: [io  0x0500-0x057f]
[    0.656216] pnp 00:01: [io  0x0068]
[    0.656218] pnp 00:01: [io  0x006c]
[    0.656220] pnp 00:01: [io  0xff2c-0xff2f]
[    0.656223] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.656225] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.656227] pnp 00:01: [mem 0xfed10000-0xfed13fff]
[    0.656229] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.656232] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.656234] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.656236] pnp 00:01: [mem 0xfed20000-0xfed8ffff]
[    0.656238] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.656266] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.2 BAR 13 [io  0x1000-0x2fff]
[    0.656344] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.656347] system 00:01: [io  0x0610] has been reserved
[    0.656350] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.656353] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.656355] system 00:01: [io  0x0820-0x0823] has been reserved
[    0.656358] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.656361] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.656364] system 00:01: [io  0xff2c-0xff2f] has been reserved
[    0.656368] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.656371] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.656374] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.656377] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.656380] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.656384] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.656387] system 00:01: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.656390] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.656394] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.656424] pnp 00:02: [io  0x0000-0x001f]
[    0.656427] pnp 00:02: [io  0x0081-0x0091]
[    0.656429] pnp 00:02: [io  0x0093-0x009f]
[    0.656431] pnp 00:02: [io  0x00c0-0x00df]
[    0.656433] pnp 00:02: [dma 4]
[    0.656473] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.656497] pnp 00:03: [io  0x0070-0x0077]
[    0.656534] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.656601] pnp 00:04: [irq 0 disabled]
[    0.656613] pnp 00:04: [irq 8]
[    0.656615] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.656655] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.656667] pnp 00:05: [io  0x00f0]
[    0.656673] pnp 00:05: [irq 13]
[    0.656710] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.656722] pnp 00:06: [mem 0xfff00000-0xffffffff]
[    0.656759] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.656787] pnp 00:07: [io  0x0060]
[    0.656789] pnp 00:07: [io  0x0064]
[    0.656795] pnp 00:07: [irq 1]
[    0.656837] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.656901] pnp 00:08: [irq 12]
[    0.656943] pnp 00:08: Plug and Play ACPI device, IDs SYN1b1d SYN1b00 SYN0002 PNP0f13 (active)
[    0.657124] pnp: PnP ACPI: found 9 devices
[    0.657126] ACPI: ACPI bus type pnp unregistered
[    0.657130] PnPBIOS: Disabled by ACPI PNP
[    0.694257] PCI: max bus depth: 1 pci_try_num: 2
[    0.694296] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.694300] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.694306] pci 0000:00:1c.0:   bridge window [mem 0x95700000-0x966fffff]
[    0.694311] pci 0000:00:1c.0:   bridge window [mem 0x90400000-0x913fffff 64bit pref]
[    0.694318] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.694321] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.694327] pci 0000:00:1c.1:   bridge window [mem 0x94600000-0x956fffff]
[    0.694331] pci 0000:00:1c.1:   bridge window [mem 0x91400000-0x923fffff 64bit pref]
[    0.694338] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
[    0.694342] pci 0000:00:1c.2:   bridge window [io  0x1000-0x2fff]
[    0.694347] pci 0000:00:1c.2:   bridge window [mem 0x93500000-0x945fffff]
[    0.694352] pci 0000:00:1c.2:   bridge window [mem 0x92400000-0x933fffff 64bit pref]
[    0.694358] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.694375] pci 0000:00:1c.0: enabling device (0001 -> 0003)
[    0.694390] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.694396] pci 0000:00:1c.0: setting latency timer to 64
[    0.694407] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.694411] pci 0000:00:1c.1: setting latency timer to 64
[    0.694422] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.694426] pci 0000:00:1c.2: setting latency timer to 64
[    0.694434] pci 0000:00:1e.0: setting latency timer to 64
[    0.694438] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.694441] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.694443] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.694446] pci_bus 0000:00: resource 7 [mem 0x80000000-0xfebfffff]
[    0.694449] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.694451] pci_bus 0000:02: resource 1 [mem 0x95700000-0x966fffff]
[    0.694454] pci_bus 0000:02: resource 2 [mem 0x90400000-0x913fffff 64bit pref]
[    0.694456] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.694459] pci_bus 0000:04: resource 1 [mem 0x94600000-0x956fffff]
[    0.694462] pci_bus 0000:04: resource 2 [mem 0x91400000-0x923fffff 64bit pref]
[    0.694464] pci_bus 0000:05: resource 0 [io  0x1000-0x2fff]
[    0.694467] pci_bus 0000:05: resource 1 [mem 0x93500000-0x945fffff]
[    0.694469] pci_bus 0000:05: resource 2 [mem 0x92400000-0x933fffff 64bit pref]
[    0.694472] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.694475] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.694477] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.694480] pci_bus 0000:06: resource 7 [mem 0x80000000-0xfebfffff]
[    0.694519] NET: Registered protocol family 2
[    0.694594] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.694835] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.695245] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.695509] TCP: Hash tables configured (established 131072 bind 65536)
[    0.695512] TCP reno registered
[    0.695515] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.695527] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.695646] NET: Registered protocol family 1
[    0.695668] pci 0000:00:02.0: Boot video device
[    0.695697] pci 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.695717] pci 0000:00:1a.0: PCI INT A disabled
[    0.695730] pci 0000:00:1a.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.712024] pci 0000:00:1a.7: PCI INT D disabled
[    0.712048] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.712067] pci 0000:00:1d.0: PCI INT A disabled
[    0.712079] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.712096] pci 0000:00:1d.1: PCI INT B disabled
[    0.712105] pci 0000:00:1d.2: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    0.712124] pci 0000:00:1d.2: PCI INT D disabled
[    0.712132] pci 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.712151] pci 0000:00:1d.3: PCI INT C disabled
[    0.712160] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.728023] pci 0000:00:1d.7: PCI INT A disabled
[    0.728044] PCI: CLS 64 bytes, default 64
[    0.728051] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.728053] Simple Boot Flag at 0x44 set to 0x1
[    0.728417] audit: initializing netlink socket (disabled)
[    0.728427] type=2000 audit(1336418349.724:1): initialized
[    0.754388] highmem bounce pool size: 64 pages
[    0.754394] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.762631] VFS: Disk quotas dquot_6.5.2
[    0.762713] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.763350] fuse init (API version 7.17)
[    0.763458] msgmni has been set to 1714
[    0.763875] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.763906] io scheduler noop registered
[    0.763909] io scheduler deadline registered
[    0.763917] io scheduler cfq registered (default)
[    0.764069] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.764125] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.764205] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.764254] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.764328] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.764377] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.764477] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764504] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.764579] intel_idle: MWAIT substates: 0x2220
[    0.764582] intel_idle: does not run on family 6 model 23
[    0.764831] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.765067] ACPI: AC Adapter [AC] (on-line)
[    0.765206] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0C:00/input/input0
[    0.765211] ACPI: Power Button [PWRB]
[    0.765371] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0D:00/input/input1
[    0.765388] ACPI: Lid Switch [LID0]
[    0.765465] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0E:00/input/input2
[    0.765469] ACPI: Sleep Button [SLPB]
[    0.765617] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.765621] ACPI: Power Button [PWRF]
[    0.765809] Monitor-Mwait will be used to enter C-1 state
[    0.765839] Monitor-Mwait will be used to enter C-2 state
[    0.765847] Marking TSC unstable due to TSC halts in idle
[    0.765856] ACPI: acpi_idle registered with cpuidle
[    0.865748] thermal LNXTHERM:00: registered as thermal_zone0
[    0.865751] ACPI: Thermal Zone [TZ01] (57 C)
[    0.865803] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.865815] ACPI: Battery Slot [BAT0] (battery present)
[    0.865857] ERST: Table is not found!
[    0.865859] GHES: HEST is not enabled!
[    0.865909] isapnp: Scanning for PnP cards...
[    0.865996] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.219369] isapnp: No Plug & Play device found
[    1.268383] Linux agpgart interface v0.103
[    1.268494] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    1.268604] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.269249] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.269382] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.271088] brd: module loaded
[    1.271970] loop: module loaded
[    1.272137] ahci 0000:00:1f.2: version 3.0
[    1.272151] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.272205] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.272244] ahci: SSS flag set, parallel bus scan disabled
[    1.272270] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.272274] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems sxs 
[    1.272280] ahci 0000:00:1f.2: setting latency timer to 64
[    1.280474] scsi0 : ahci
[    1.280586] scsi1 : ahci
[    1.280672] scsi2 : ahci
[    1.280758] scsi3 : ahci
[    1.280897] ata1: SATA max UDMA/133 abar m2048@0x96704000 port 0x96704100 irq 43
[    1.280901] ata2: SATA max UDMA/133 abar m2048@0x96704000 port 0x96704180 irq 43
[    1.280903] ata3: DUMMY
[    1.280904] ata4: DUMMY
[    1.281394] Fixed MDIO Bus: probed
[    1.281418] tun: Universal TUN/TAP device driver, 1.6
[    1.281420] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.281493] PPP generic driver version 2.4.2
[    1.281614] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.281636] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.281656] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.281660] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.281710] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.281741] ehci_hcd 0000:00:1a.7: debug port 1
[    1.285622] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.285640] ehci_hcd 0000:00:1a.7: irq 21, io mem 0x96704c00
[    1.300017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.300169] hub 1-0:1.0: USB hub found
[    1.300174] hub 1-0:1.0: 2 ports detected
[    1.300250] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.300265] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.300269] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.300318] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.300344] ehci_hcd 0000:00:1d.7: debug port 1
[    1.304241] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.304256] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x96704800
[    1.320015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.320147] hub 2-0:1.0: USB hub found
[    1.320151] hub 2-0:1.0: 8 ports detected
[    1.320242] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.320259] uhci_hcd: USB Universal Host Controller Interface driver
[    1.320280] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.320289] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.320293] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.320349] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.320385] uhci_hcd 0000:00:1a.0: irq 20, io base 0x000050c0
[    1.320523] hub 3-0:1.0: USB hub found
[    1.320528] hub 3-0:1.0: 2 ports detected
[    1.320597] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.320605] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.320609] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.320660] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    1.320685] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[    1.320819] hub 4-0:1.0: USB hub found
[    1.320823] hub 4-0:1.0: 2 ports detected
[    1.320893] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.320901] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.320905] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.320955] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    1.320990] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005080
[    1.321128] hub 5-0:1.0: USB hub found
[    1.321132] hub 5-0:1.0: 2 ports detected
[    1.321204] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    1.321212] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.321216] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.321266] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    1.321292] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00005060
[    1.321428] hub 6-0:1.0: USB hub found
[    1.321432] hub 6-0:1.0: 2 ports detected
[    1.321503] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.321511] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.321515] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.321566] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 7
[    1.321601] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00005040
[    1.321736] hub 7-0:1.0: USB hub found
[    1.321740] hub 7-0:1.0: 2 ports detected
[    1.321864] usbcore: registered new interface driver libusual
[    1.321913] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.352683] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.352690] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.352836] mousedev: PS/2 mouse device common for all mice
[    1.354426] rtc_cmos 00:03: RTC can wake from S4
[    1.354548] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.354576] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.354639] device-mapper: uevent: version 1.0.3
[    1.354728] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.354765] EISA: Probing bus 0 at eisa.0
[    1.354769] EISA: Cannot allocate resource for mainboard
[    1.354771] Cannot allocate resource for EISA slot 1
[    1.354773] Cannot allocate resource for EISA slot 2
[    1.354775] Cannot allocate resource for EISA slot 3
[    1.354777] Cannot allocate resource for EISA slot 4
[    1.354779] Cannot allocate resource for EISA slot 5
[    1.354781] Cannot allocate resource for EISA slot 6
[    1.354783] Cannot allocate resource for EISA slot 7
[    1.354785] Cannot allocate resource for EISA slot 8
[    1.354786] EISA: Detected 0 cards.
[    1.354796] cpufreq-nforce2: No nForce2 chipset.
[    1.354848] cpuidle: using governor ladder
[    1.354930] cpuidle: using governor menu
[    1.354933] EFI Variables Facility v0.08 2004-May-17
[    1.355213] TCP cubic registered
[    1.355342] NET: Registered protocol family 10
[    1.355937] NET: Registered protocol family 17
[    1.355953] Registering the dns_resolver key type
[    1.355979] Using IPI No-Shortcut mode
[    1.356154] PM: Hibernation image not present or could not be loaded.
[    1.356168] registered taskstats version 1
[    1.366697]   Magic number: 12:804:343
[    1.366745] tty tty60: hash matches
[    1.366814] rtc_cmos 00:03: setting system clock to 2012-05-07 19:19:11 UTC (1336418351)
[    1.367168] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.367171] EDD information not available.
[    1.379440] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.612032] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.750297] Initializing USB Mass Storage driver...
[    1.750980] scsi7 : usb-storage 1-1:1.3
[    1.751369] scsi8 : usb-storage 1-1:1.4
[    1.751437] usbcore: registered new interface driver usb-storage
[    1.751439] USB Mass Storage support registered.
[    1.772040] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.823405] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG001J, max UDMA/100
[    1.823409] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.824245] ata1.00: configured for UDMA/100
[    1.824414] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    1.824557] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.824589] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.824608] sd 0:0:0:0: [sda] Write Protect is off
[    1.824612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.824634] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.860040] usb 2-4: new high-speed USB device number 2 using ehci_hcd
[    1.920264]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.920896] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.316047] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.317778] ata2.00: ATAPI: Optiarc DVD RW AD-7585H, KX04, max UDMA/100
[    2.318576] ata2.00: configured for UDMA/100
[    2.320120] ACPI: Battery Slot [BAT0] (battery present)
[    2.322011] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7585H  KX04 PQ: 0 ANSI: 5
[    2.325468] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.325472] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.325625] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.325716] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.325893] Freeing unused kernel memory: 740k freed
[    2.326232] Write protecting the kernel text: 5828k
[    2.326260] Write protecting the kernel read-only data: 2376k
[    2.326261] NX-protecting the kernel data: 4412k
[    2.345762] udevd[108]: starting version 175
[    2.451476] atl1c 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.451489] atl1c 0000:05:00.0: setting latency timer to 64
[    2.544700] atl1c 0000:05:00.0: version 1.0.1.0-NAPI
[    2.749487] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    2.752456] sr1: scsi-1 drive
[    2.752615] sr 7:0:0:0: Attached scsi CD-ROM sr1
[    2.752758] sr 7:0:0:0: Attached scsi generic sg2 type 5
[    2.753472] scsi 8:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[    2.754112] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    2.757846] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[    3.097246] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   17.271290] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.300718] udevd[348]: starting version 175
[   17.347972] lp: driver loaded but no devices found
[   17.349053] Adding 2024444k swap on /dev/sda6.  Priority:-1 extents:1 across:2024444k 
[   17.402508] wmi: Mapper loaded
[   17.454952] acer_wmi: Acer Laptop ACPI-WMI Extras
[   17.458596] acer_wmi: Function bitmap for Communication Device: 0x1
[   17.458797] acer_wmi: Brightness must be controlled by generic video driver
[   17.524446] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   17.802645] type=1400 audit(1336429167.929:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=598 comm="apparmor_parser"
[   17.807269] type=1400 audit(1336429167.933:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=598 comm="apparmor_parser"
[   17.807527] type=1400 audit(1336429167.933:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=598 comm="apparmor_parser"
[   17.860689] Bluetooth: Core ver 2.16
[   17.860786] NET: Registered protocol family 31
[   17.860788] Bluetooth: HCI device and connection manager initialized
[   17.860792] Bluetooth: HCI socket layer initialized
[   17.860794] Bluetooth: L2CAP socket layer initialized
[   17.861109] Bluetooth: SCO socket layer initialized
[   17.862686] ppdev: user-space parallel port driver
[   17.892196] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.892200] Bluetooth: BNEP filters: protocol multicast
[   17.897210] type=1400 audit(1336429168.025:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=636 comm="apparmor_parser"
[   17.897792] type=1400 audit(1336429168.025:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=636 comm="apparmor_parser"
[   17.904102] Bluetooth: RFCOMM TTY layer initialized
[   17.904108] Bluetooth: RFCOMM socket layer initialized
[   17.904110] Bluetooth: RFCOMM ver 1.11
[   17.990467] atl1c 0000:05:00.0: irq 44 for MSI/MSI-X
[   18.004163] [drm] Initialized drm 1.1.0 20060810
[   18.023613] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.023619] pci 0000:00:02.0: setting latency timer to 64
[   18.054466] pci 0000:00:02.0: irq 45 for MSI/MSI-X
[   18.054473] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.054475] [drm] No driver support for vblank timestamp query.
[   18.064510] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.065496] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.075360] cfg80211: Calling CRDA to update world regulatory domain
[   18.103733] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.103748] ath9k 0000:04:00.0: setting latency timer to 64
[   18.267563] Linux video capture interface: v2.00
[   18.275096] usbcore: registered new interface driver usbserial
[   18.275133] USB Serial support registered for generic
[   18.275208] usbcore: registered new interface driver usbserial_generic
[   18.275210] usbserial: USB Serial Driver core
[   18.275467] uvcvideo: Found UVC 1.00 device Video WebCam (064e:a103)
[   18.294303] input: Video WebCam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input5
[   18.294436] usbcore: registered new interface driver uvcvideo
[   18.294439] USB Video Class driver (1.1.1)
[   18.297701] USB Serial support registered for GSM modem (1-port)
[   18.297771] option 1-1:1.0: GSM modem (1-port) converter detected
[   18.298392] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   18.298409] option 1-1:1.1: GSM modem (1-port) converter detected
[   18.298527] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   18.298540] option 1-1:1.2: GSM modem (1-port) converter detected
[   18.298655] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[   18.298721] usbcore: registered new interface driver option
[   18.298723] option: v0.7.2:USB Driver for GSM modems
[   18.536295] acpi device:07: registered as cooling_device2
[   18.536526] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   18.537101] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   18.537218] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.539689] ath: EEPROM regdomain: 0x65
[   18.539693] ath: EEPROM indicates we should expect a direct regpair map
[   18.539696] ath: Country alpha2 being used: 00
[   18.539698] ath: Regpair used: 0x65
[   18.539731] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.539734] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539737] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.539740] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539742] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.539745] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539748] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.539751] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539753] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.539756] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539759] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.539762] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539764] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.539767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539769] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.539772] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539774] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.539777] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539780] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.539782] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539785] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.539788] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539790] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.539793] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539795] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.539798] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.539801] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.576843] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   18.614115] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.621756] Registered led device: ath9k-phy0
[   18.621767] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xf88e0000, irq=17
[   18.625670] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.625731] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.625797] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   18.656758] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.694238] init: failsafe main process (776) killed by TERM signal
[   18.741618] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.741842] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.745774] type=1400 audit(1336429168.873:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=895 comm="apparmor_parser"
[   18.754722] type=1400 audit(1336429168.881:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=896 comm="apparmor_parser"
[   18.770027] type=1400 audit(1336429168.897:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=896 comm="apparmor_parser"
[   18.770287] type=1400 audit(1336429168.897:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=896 comm="apparmor_parser"
[   18.784984] type=1400 audit(1336429168.913:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=898 comm="apparmor_parser"
[   18.797881] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   18.797885] cfg80211: World regulatory domain updated:
[   18.797887] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.797891] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.797893] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.797896] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.797899] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.797902] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.834943] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.835528] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.568422] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   19.568426] vesafb: scrolling: redraw
[   19.568429] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   19.569031] vesafb: framebuffer at 0x80000000, mapped to 0xf9380000, using 3072k, total 3072k
[   19.569228] Console: switching to colour frame buffer device 128x48
[   19.569256] fb0: VESA VGA frame buffer device
[   20.008621] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   20.122291] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9









/*----------------------------------------------------------------*/


$ gedit /var/log/Xorg.0.log

[    19.823] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.823] X Protocol Version 11, Revision 0
[    19.823] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[    19.823] Current Operating System: Linux MisterFire 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686
[    19.823] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=fa9771ea-a622-46c7-b866-af4384bd092f ro quiet splash nomodeset acpi_osi=Linux vt.handoff=7
[    19.823] Build Date: 20 April 2012  05:12:21AM
[    19.823] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.823] Current version of pixman: 0.24.4
[    19.823] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    19.823] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.823] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May  7 19:19:29 2012
[    19.842] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.843] (==) No Layout section.  Using the first Screen section.
[    19.843] (==) No screen section available. Using defaults.
[    19.843] (**) |-->Screen "Default Screen Section" (0)
[    19.843] (**) |   |-->Monitor "<default monitor>"
[    19.843] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    19.843] (==) Automatically adding devices
[    19.843] (==) Automatically enabling devices
[    19.843] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.843] 	Entry deleted from font path.
[    19.843] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.843] 	Entry deleted from font path.
[    19.843] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.843] 	Entry deleted from font path.
[    19.843] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.843] 	Entry deleted from font path.
[    19.843] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.843] 	Entry deleted from font path.
[    19.843] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.843] 	Entry deleted from font path.
[    19.843] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    19.843] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.843] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.843] (II) Loader magic: 0xb77895a0
[    19.843] (II) Module ABI versions:
[    19.843] 	X.Org ANSI C Emulation: 0.4
[    19.843] 	X.Org Video Driver: 11.0
[    19.843] 	X.Org XInput driver : 16.0
[    19.843] 	X.Org Server Extension : 6.0
[    19.844] (--) PCI:*(0:0:2:0) 8086:2a42:1025:0212 rev 9, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x000050f0/8
[    19.844] (--) PCI: (0:0:2:1) 8086:2a43:1025:0212 rev 9, Mem @ 0x93400000/1048576
[    19.845] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.845] (II) LoadModule: "extmod"
[    19.860] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.861] (II) Module extmod: vendor="X.Org Foundation"
[    19.861] 	compiled for 1.11.3, module version = 1.0.0
[    19.861] 	Module class: X.Org Server Extension
[    19.861] 	ABI class: X.Org Server Extension, version 6.0
[    19.861] (II) Loading extension MIT-SCREEN-SAVER
[    19.861] (II) Loading extension XFree86-VidModeExtension
[    19.861] (II) Loading extension XFree86-DGA
[    19.861] (II) Loading extension DPMS
[    19.861] (II) Loading extension XVideo
[    19.861] (II) Loading extension XVideo-MotionCompensation
[    19.861] (II) Loading extension X-Resource
[    19.861] (II) LoadModule: "dbe"
[    19.861] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.861] (II) Module dbe: vendor="X.Org Foundation"
[    19.861] 	compiled for 1.11.3, module version = 1.0.0
[    19.861] 	Module class: X.Org Server Extension
[    19.861] 	ABI class: X.Org Server Extension, version 6.0
[    19.861] (II) Loading extension DOUBLE-BUFFER
[    19.861] (II) LoadModule: "glx"
[    19.861] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    19.896] (II) Module glx: vendor="NVIDIA Corporation"
[    19.896] 	compiled for 4.0.2, module version = 1.0.0
[    19.896] 	Module class: X.Org Server Extension
[    19.896] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012
[    19.896] (II) Loading extension GLX
[    19.896] (II) LoadModule: "record"
[    19.896] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.896] (II) Module record: vendor="X.Org Foundation"
[    19.896] 	compiled for 1.11.3, module version = 1.13.0
[    19.896] 	Module class: X.Org Server Extension
[    19.896] 	ABI class: X.Org Server Extension, version 6.0
[    19.896] (II) Loading extension RECORD
[    19.896] (II) LoadModule: "dri"
[    19.897] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.897] (II) Module dri: vendor="X.Org Foundation"
[    19.897] 	compiled for 1.11.3, module version = 1.0.0
[    19.897] 	ABI class: X.Org Server Extension, version 6.0
[    19.897] (II) Loading extension XFree86-DRI
[    19.897] (II) LoadModule: "dri2"
[    19.897] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.897] (II) Module dri2: vendor="X.Org Foundation"
[    19.897] 	compiled for 1.11.3, module version = 1.2.0
[    19.897] 	ABI class: X.Org Server Extension, version 6.0
[    19.897] (II) Loading extension DRI2
[    19.897] (==) Matched intel as autoconfigured driver 0
[    19.897] (==) Matched vesa as autoconfigured driver 1
[    19.897] (==) Matched fbdev as autoconfigured driver 2
[    19.897] (==) Assigned the driver to the xf86ConfigLayout
[    19.897] (II) LoadModule: "intel"
[    19.898] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.898] (II) Module intel: vendor="X.Org Foundation"
[    19.898] 	compiled for 1.11.3, module version = 2.19.0
[    19.898] 	Module class: X.Org Video Driver
[    19.898] 	ABI class: X.Org Video Driver, version 11.0
[    19.898] (II) LoadModule: "vesa"
[    19.898] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.898] (II) Module vesa: vendor="X.Org Foundation"
[    19.898] 	compiled for 1.11.3, module version = 2.3.0
[    19.898] 	Module class: X.Org Video Driver
[    19.898] 	ABI class: X.Org Video Driver, version 11.0
[    19.898] (II) LoadModule: "fbdev"
[    19.899] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.899] (II) Module fbdev: vendor="X.Org Foundation"
[    19.899] 	compiled for 1.11.3, module version = 0.4.2
[    19.899] 	ABI class: X.Org Video Driver, version 11.0
[    19.899] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2)
[    19.899] (II) VESA: driver for VESA chipsets: vesa
[    19.899] (II) FBDEV: driver for framebuffer: fbdev
[    19.899] (++) using VT number 7

[    19.903] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.903] (WW) Falling back to old probe method for fbdev
[    19.903] (II) Loading sub module "fbdevhw"
[    19.903] (II) LoadModule: "fbdevhw"
[    19.903] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.903] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.903] 	compiled for 1.11.3, module version = 0.0.2
[    19.903] 	ABI class: X.Org Video Driver, version 11.0
[    19.903] (II) Loading sub module "vbe"
[    19.903] (II) LoadModule: "vbe"
[    19.904] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.904] (II) Module vbe: vendor="X.Org Foundation"
[    19.904] 	compiled for 1.11.3, module version = 1.1.0
[    19.904] 	ABI class: X.Org Video Driver, version 11.0
[    19.904] (II) Loading sub module "int10"
[    19.904] (II) LoadModule: "int10"
[    19.904] (II) Loading /usr/lib/xorg/modules/libint10.so
[    19.904] (II) Module int10: vendor="X.Org Foundation"
[    19.904] 	compiled for 1.11.3, module version = 1.0.0
[    19.904] 	ABI class: X.Org Video Driver, version 11.0
[    19.904] (II) VESA(0): initializing int10
[    19.904] (II) VESA(0): Bad V_BIOS checksum
[    19.904] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    19.905] (II) VESA(0): VESA BIOS detected
[    19.905] (II) VESA(0): VESA VBE Version 3.0
[    19.905] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    19.905] (II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
[    19.905] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    19.905] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    19.905] (II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
[    19.905] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    19.913] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    19.913] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    19.913] (==) VESA(0): RGB weight 888
[    19.913] (==) VESA(0): Default visual is TrueColor
[    19.913] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.913] (II) Loading sub module "ddc"
[    19.913] (II) LoadModule: "ddc"
[    19.913] (II) Module "ddc" already built-in
[    19.913] (II) VESA(0): VESA VBE DDC supported
[    19.913] (II) VESA(0): VESA VBE DDC Level 2
[    19.913] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    19.927] (II) VESA(0): VESA VBE DDC read successfully
[    19.927] (II) VESA(0): Manufacturer: LGD  Model: 1c2  Serial#: 0
[    19.927] (II) VESA(0): Year: 2008  Week: 0
[    19.927] (II) VESA(0): EDID Version: 1.3
[    19.927] (II) VESA(0): Digital Display Input
[    19.927] (II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    19.927] (II) VESA(0): Gamma: 2.20
[    19.927] (II) VESA(0): No DPMS capabilities specified
[    19.927] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    19.927] (II) VESA(0): First detailed timing is preferred mode
[    19.927] (II) VESA(0): redX: 0.608 redY: 0.338   greenX: 0.283 greenY: 0.586
[    19.927] (II) VESA(0): blueX: 0.150 blueY: 0.103   whiteX: 0.313 whiteY: 0.329
[    19.927] (II) VESA(0): Manufacturer's mask: 0
[    19.927] (II) VESA(0): Supported detailed timing:
[    19.929] (II) VESA(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
[    19.929] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    19.929] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    19.929] (II) VESA(0):  LG Display
[    19.929] (II) VESA(0): Monitor name: LP156WH1-TLA3
[    19.929] (II) VESA(0): EDID (in hex):
[    19.929] (II) VESA(0): 	00ffffffffffff0030e4c20100000000
[    19.929] (II) VESA(0): 	00120103802213780ae8959b56489626
[    19.929] (II) VESA(0): 	1a505400000001010101010101010101
[    19.929] (II) VESA(0): 	0101010101013e1c56a0500016303020
[    19.929] (II) VESA(0): 	350058c2100000190000000000000000
[    19.929] (II) VESA(0): 	00000000000000000000000000fe004c
[    19.929] (II) VESA(0): 	4720446973706c61790a2020000000fc
[    19.929] (II) VESA(0): 	004c503135365748312d544c413300de
[    19.929] (II) VESA(0): EDID vendor "LGD", prod id 450
[    19.929] (II) VESA(0): Printing DDC gathered Modelines:
[    19.929] (II) VESA(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    19.929] (II) VESA(0): Searching for matching VESA mode(s):
[    19.929] Mode: 160 (0x0)
[    19.929] 	ModeAttributes: 0x0
[    19.929] 	WinAAttributes: 0x0
[    19.929] 	WinBAttributes: 0x0
[    19.929] 	WinGranularity: 0
[    19.929] 	WinSize: 0
[    19.929] 	WinASegment: 0x0
[    19.929] 	WinBSegment: 0x0
[    19.929] 	WinFuncPtr: 0x0
[    19.929] 	BytesPerScanline: 0
[    19.929] 	XResolution: 0
[    19.929] 	YResolution: 0
[    19.929] 	XCharSize: 0
[    19.929] 	YCharSize: 0
[    19.929] 	NumberOfPlanes: 0
[    19.929] 	BitsPerPixel: 0
[    19.929] 	NumberOfBanks: 0
[    19.929] 	MemoryModel: 0
[    19.929] 	BankSize: 0
[    19.929] 	NumberOfImages: 0
[    19.929] 	RedMaskSize: 0
[    19.929] 	RedFieldPosition: 0
[    19.929] 	GreenMaskSize: 0
[    19.929] 	GreenFieldPosition: 0
[    19.929] 	BlueMaskSize: 0
[    19.929] 	BlueFieldPosition: 0
[    19.929] 	RsvdMaskSize: 0
[    19.929] 	RsvdFieldPosition: 0
[    19.929] 	DirectColorModeInfo: 0
[    19.929] 	PhysBasePtr: 0x0
[    19.929] 	LinBytesPerScanLine: 0
[    19.929] 	BnkNumberOfImagePages: 0
[    19.929] 	LinNumberOfImagePages: 0
[    19.929] 	LinRedMaskSize: 0
[    19.929] 	LinRedFieldPosition: 0
[    19.929] 	LinGreenMaskSize: 0
[    19.929] 	LinGreenFieldPosition: 0
[    19.929] 	LinBlueMaskSize: 0
[    19.929] 	LinBlueFieldPosition: 0
[    19.929] 	LinRsvdMaskSize: 0
[    19.929] 	LinRsvdFieldPosition: 0
[    19.929] 	MaxPixelClock: 0
[    19.930] Mode: 161 (0x0)
[    19.930] 	ModeAttributes: 0x0
[    19.930] 	WinAAttributes: 0x0
[    19.930] 	WinBAttributes: 0x0
[    19.930] 	WinGranularity: 0
[    19.930] 	WinSize: 0
[    19.930] 	WinASegment: 0x0
[    19.930] 	WinBSegment: 0x0
[    19.930] 	WinFuncPtr: 0x0
[    19.930] 	BytesPerScanline: 0
[    19.930] 	XResolution: 0
[    19.930] 	YResolution: 0
[    19.930] 	XCharSize: 0
[    19.930] 	YCharSize: 0
[    19.930] 	NumberOfPlanes: 0
[    19.930] 	BitsPerPixel: 0
[    19.930] 	NumberOfBanks: 0
[    19.930] 	MemoryModel: 0
[    19.930] 	BankSize: 0
[    19.930] 	NumberOfImages: 0
[    19.930] 	RedMaskSize: 0
[    19.930] 	RedFieldPosition: 0
[    19.930] 	GreenMaskSize: 0
[    19.930] 	GreenFieldPosition: 0
[    19.930] 	BlueMaskSize: 0
[    19.930] 	BlueFieldPosition: 0
[    19.930] 	RsvdMaskSize: 0
[    19.930] 	RsvdFieldPosition: 0
[    19.930] 	DirectColorModeInfo: 0
[    19.930] 	PhysBasePtr: 0x0
[    19.930] 	LinBytesPerScanLine: 0
[    19.930] 	BnkNumberOfImagePages: 0
[    19.930] 	LinNumberOfImagePages: 0
[    19.930] 	LinRedMaskSize: 0
[    19.930] 	LinRedFieldPosition: 0
[    19.930] 	LinGreenMaskSize: 0
[    19.930] 	LinGreenFieldPosition: 0
[    19.930] 	LinBlueMaskSize: 0
[    19.930] 	LinBlueFieldPosition: 0
[    19.930] 	LinRsvdMaskSize: 0
[    19.930] 	LinRsvdFieldPosition: 0
[    19.930] 	MaxPixelClock: 0
[    19.930] Mode: 162 (0x0)
[    19.930] 	ModeAttributes: 0x0
[    19.930] 	WinAAttributes: 0x0
[    19.930] 	WinBAttributes: 0x0
[    19.930] 	WinGranularity: 0
[    19.930] 	WinSize: 0
[    19.930] 	WinASegment: 0x0
[    19.930] 	WinBSegment: 0x0
[    19.930] 	WinFuncPtr: 0x0
[    19.930] 	BytesPerScanline: 0
[    19.930] 	XResolution: 0
[    19.930] 	YResolution: 0
[    19.930] 	XCharSize: 0
[    19.930] 	YCharSize: 0
[    19.930] 	NumberOfPlanes: 0
[    19.930] 	BitsPerPixel: 0
[    19.930] 	NumberOfBanks: 0
[    19.930] 	MemoryModel: 0
[    19.930] 	BankSize: 0
[    19.930] 	NumberOfImages: 0
[    19.930] 	RedMaskSize: 0
[    19.930] 	RedFieldPosition: 0
[    19.930] 	GreenMaskSize: 0
[    19.930] 	GreenFieldPosition: 0
[    19.930] 	BlueMaskSize: 0
[    19.930] 	BlueFieldPosition: 0
[    19.930] 	RsvdMaskSize: 0
[    19.930] 	RsvdFieldPosition: 0
[    19.930] 	DirectColorModeInfo: 0
[    19.930] 	PhysBasePtr: 0x0
[    19.930] 	LinBytesPerScanLine: 0
[    19.930] 	BnkNumberOfImagePages: 0
[    19.930] 	LinNumberOfImagePages: 0
[    19.930] 	LinRedMaskSize: 0
[    19.930] 	LinRedFieldPosition: 0
[    19.930] 	LinGreenMaskSize: 0
[    19.930] 	LinGreenFieldPosition: 0
[    19.930] 	LinBlueMaskSize: 0
[    19.930] 	LinBlueFieldPosition: 0
[    19.930] 	LinRsvdMaskSize: 0
[    19.930] 	LinRsvdFieldPosition: 0
[    19.930] 	MaxPixelClock: 0
[    19.930] Mode: 163 (0x0)
[    19.930] 	ModeAttributes: 0x0
[    19.930] 	WinAAttributes: 0x0
[    19.931] 	WinBAttributes: 0x0
[    19.931] 	WinGranularity: 0
[    19.931] 	WinSize: 0
[    19.931] 	WinASegment: 0x0
[    19.931] 	WinBSegment: 0x0
[    19.931] 	WinFuncPtr: 0x0
[    19.931] 	BytesPerScanline: 0
[    19.931] 	XResolution: 0
[    19.931] 	YResolution: 0
[    19.931] 	XCharSize: 0
[    19.931] 	YCharSize: 0
[    19.931] 	NumberOfPlanes: 0
[    19.931] 	BitsPerPixel: 0
[    19.931] 	NumberOfBanks: 0
[    19.931] 	MemoryModel: 0
[    19.931] 	BankSize: 0
[    19.931] 	NumberOfImages: 0
[    19.931] 	RedMaskSize: 0
[    19.931] 	RedFieldPosition: 0
[    19.931] 	GreenMaskSize: 0
[    19.931] 	GreenFieldPosition: 0
[    19.931] 	BlueMaskSize: 0
[    19.931] 	BlueFieldPosition: 0
[    19.931] 	RsvdMaskSize: 0
[    19.931] 	RsvdFieldPosition: 0
[    19.931] 	DirectColorModeInfo: 0
[    19.931] 	PhysBasePtr: 0x0
[    19.931] 	LinBytesPerScanLine: 0
[    19.931] 	BnkNumberOfImagePages: 0
[    19.931] 	LinNumberOfImagePages: 0
[    19.931] 	LinRedMaskSize: 0
[    19.931] 	LinRedFieldPosition: 0
[    19.931] 	LinGreenMaskSize: 0
[    19.931] 	LinGreenFieldPosition: 0
[    19.931] 	LinBlueMaskSize: 0
[    19.931] 	LinBlueFieldPosition: 0
[    19.931] 	LinRsvdMaskSize: 0
[    19.931] 	LinRsvdFieldPosition: 0
[    19.931] 	MaxPixelClock: 0
[    19.931] Mode: 164 (0x0)
[    19.931] 	ModeAttributes: 0x0
[    19.931] 	WinAAttributes: 0x0
[    19.931] 	WinBAttributes: 0x0
[    19.931] 	WinGranularity: 0
[    19.931] 	WinSize: 0
[    19.931] 	WinASegment: 0x0
[    19.931] 	WinBSegment: 0x0
[    19.931] 	WinFuncPtr: 0x0
[    19.931] 	BytesPerScanline: 0
[    19.931] 	XResolution: 0
[    19.931] 	YResolution: 0
[    19.931] 	XCharSize: 0
[    19.931] 	YCharSize: 0
[    19.931] 	NumberOfPlanes: 0
[    19.931] 	BitsPerPixel: 0
[    19.931] 	NumberOfBanks: 0
[    19.931] 	MemoryModel: 0
[    19.931] 	BankSize: 0
[    19.931] 	NumberOfImages: 0
[    19.931] 	RedMaskSize: 0
[    19.931] 	RedFieldPosition: 0
[    19.931] 	GreenMaskSize: 0
[    19.931] 	GreenFieldPosition: 0
[    19.931] 	BlueMaskSize: 0
[    19.931] 	BlueFieldPosition: 0
[    19.931] 	RsvdMaskSize: 0
[    19.931] 	RsvdFieldPosition: 0
[    19.931] 	DirectColorModeInfo: 0
[    19.931] 	PhysBasePtr: 0x0
[    19.931] 	LinBytesPerScanLine: 0
[    19.931] 	BnkNumberOfImagePages: 0
[    19.931] 	LinNumberOfImagePages: 0
[    19.931] 	LinRedMaskSize: 0
[    19.931] 	LinRedFieldPosition: 0
[    19.931] 	LinGreenMaskSize: 0
[    19.931] 	LinGreenFieldPosition: 0
[    19.931] 	LinBlueMaskSize: 0
[    19.931] 	LinBlueFieldPosition: 0
[    19.931] 	LinRsvdMaskSize: 0
[    19.931] 	LinRsvdFieldPosition: 0
[    19.931] 	MaxPixelClock: 0
[    19.931] Mode: 165 (0x0)
[    19.931] 	ModeAttributes: 0x0
[    19.931] 	WinAAttributes: 0x0
[    19.931] 	WinBAttributes: 0x0
[    19.931] 	WinGranularity: 0
[    19.931] 	WinSize: 0
[    19.931] 	WinASegment: 0x0
[    19.931] 	WinBSegment: 0x0
[    19.931] 	WinFuncPtr: 0x0
[    19.931] 	BytesPerScanline: 0
[    19.931] 	XResolution: 0
[    19.931] 	YResolution: 0
[    19.932] 	XCharSize: 0
[    19.932] 	YCharSize: 0
[    19.932] 	NumberOfPlanes: 0
[    19.932] 	BitsPerPixel: 0
[    19.932] 	NumberOfBanks: 0
[    19.932] 	MemoryModel: 0
[    19.932] 	BankSize: 0
[    19.932] 	NumberOfImages: 0
[    19.932] 	RedMaskSize: 0
[    19.932] 	RedFieldPosition: 0
[    19.932] 	GreenMaskSize: 0
[    19.932] 	GreenFieldPosition: 0
[    19.932] 	BlueMaskSize: 0
[    19.932] 	BlueFieldPosition: 0
[    19.932] 	RsvdMaskSize: 0
[    19.932] 	RsvdFieldPosition: 0
[    19.932] 	DirectColorModeInfo: 0
[    19.932] 	PhysBasePtr: 0x0
[    19.932] 	LinBytesPerScanLine: 0
[    19.932] 	BnkNumberOfImagePages: 0
[    19.932] 	LinNumberOfImagePages: 0
[    19.932] 	LinRedMaskSize: 0
[    19.932] 	LinRedFieldPosition: 0
[    19.932] 	LinGreenMaskSize: 0
[    19.932] 	LinGreenFieldPosition: 0
[    19.932] 	LinBlueMaskSize: 0
[    19.932] 	LinBlueFieldPosition: 0
[    19.932] 	LinRsvdMaskSize: 0
[    19.932] 	LinRsvdFieldPosition: 0
[    19.932] 	MaxPixelClock: 0
[    19.932] Mode: 166 (0x0)
[    19.932] 	ModeAttributes: 0x0
[    19.932] 	WinAAttributes: 0x0
[    19.932] 	WinBAttributes: 0x0
[    19.932] 	WinGranularity: 0
[    19.932] 	WinSize: 0
[    19.932] 	WinASegment: 0x0
[    19.932] 	WinBSegment: 0x0
[    19.932] 	WinFuncPtr: 0x0
[    19.932] 	BytesPerScanline: 0
[    19.932] 	XResolution: 0
[    19.932] 	YResolution: 0
[    19.932] 	XCharSize: 0
[    19.932] 	YCharSize: 0
[    19.932] 	NumberOfPlanes: 0
[    19.932] 	BitsPerPixel: 0
[    19.932] 	NumberOfBanks: 0
[    19.932] 	MemoryModel: 0
[    19.932] 	BankSize: 0
[    19.932] 	NumberOfImages: 0
[    19.932] 	RedMaskSize: 0
[    19.932] 	RedFieldPosition: 0
[    19.932] 	GreenMaskSize: 0
[    19.932] 	GreenFieldPosition: 0
[    19.932] 	BlueMaskSize: 0
[    19.932] 	BlueFieldPosition: 0
[    19.932] 	RsvdMaskSize: 0
[    19.932] 	RsvdFieldPosition: 0
[    19.932] 	DirectColorModeInfo: 0
[    19.932] 	PhysBasePtr: 0x0
[    19.932] 	LinBytesPerScanLine: 0
[    19.932] 	BnkNumberOfImagePages: 0
[    19.932] 	LinNumberOfImagePages: 0
[    19.932] 	LinRedMaskSize: 0
[    19.932] 	LinRedFieldPosition: 0
[    19.932] 	LinGreenMaskSize: 0
[    19.932] 	LinGreenFieldPosition: 0
[    19.932] 	LinBlueMaskSize: 0
[    19.932] 	LinBlueFieldPosition: 0
[    19.932] 	LinRsvdMaskSize: 0
[    19.932] 	LinRsvdFieldPosition: 0
[    19.932] 	MaxPixelClock: 0
[    19.932] Mode: 167 (0x0)
[    19.932] 	ModeAttributes: 0x0
[    19.932] 	WinAAttributes: 0x0
[    19.932] 	WinBAttributes: 0x0
[    19.932] 	WinGranularity: 0
[    19.932] 	WinSize: 0
[    19.932] 	WinASegment: 0x0
[    19.932] 	WinBSegment: 0x0
[    19.932] 	WinFuncPtr: 0x0
[    19.932] 	BytesPerScanline: 0
[    19.932] 	XResolution: 0
[    19.932] 	YResolution: 0
[    19.932] 	XCharSize: 0
[    19.932] 	YCharSize: 0
[    19.932] 	NumberOfPlanes: 0
[    19.932] 	BitsPerPixel: 0
[    19.932] 	NumberOfBanks: 0
[    19.933] 	MemoryModel: 0
[    19.933] 	BankSize: 0
[    19.933] 	NumberOfImages: 0
[    19.933] 	RedMaskSize: 0
[    19.933] 	RedFieldPosition: 0
[    19.933] 	GreenMaskSize: 0
[    19.933] 	GreenFieldPosition: 0
[    19.933] 	BlueMaskSize: 0
[    19.933] 	BlueFieldPosition: 0
[    19.933] 	RsvdMaskSize: 0
[    19.933] 	RsvdFieldPosition: 0
[    19.933] 	DirectColorModeInfo: 0
[    19.933] 	PhysBasePtr: 0x0
[    19.933] 	LinBytesPerScanLine: 0
[    19.933] 	BnkNumberOfImagePages: 0
[    19.933] 	LinNumberOfImagePages: 0
[    19.933] 	LinRedMaskSize: 0
[    19.933] 	LinRedFieldPosition: 0
[    19.933] 	LinGreenMaskSize: 0
[    19.933] 	LinGreenFieldPosition: 0
[    19.933] 	LinBlueMaskSize: 0
[    19.933] 	LinBlueFieldPosition: 0
[    19.933] 	LinRsvdMaskSize: 0
[    19.933] 	LinRsvdFieldPosition: 0
[    19.933] 	MaxPixelClock: 0
[    19.933] Mode: 168 (0x0)
[    19.933] 	ModeAttributes: 0x0
[    19.933] 	WinAAttributes: 0x0
[    19.933] 	WinBAttributes: 0x0
[    19.933] 	WinGranularity: 0
[    19.933] 	WinSize: 0
[    19.933] 	WinASegment: 0x0
[    19.933] 	WinBSegment: 0x0
[    19.933] 	WinFuncPtr: 0x0
[    19.933] 	BytesPerScanline: 0
[    19.933] 	XResolution: 0
[    19.933] 	YResolution: 0
[    19.933] 	XCharSize: 0
[    19.933] 	YCharSize: 0
[    19.933] 	NumberOfPlanes: 0
[    19.933] 	BitsPerPixel: 0
[    19.933] 	NumberOfBanks: 0
[    19.933] 	MemoryModel: 0
[    19.933] 	BankSize: 0
[    19.933] 	NumberOfImages: 0
[    19.933] 	RedMaskSize: 0
[    19.933] 	RedFieldPosition: 0
[    19.933] 	GreenMaskSize: 0
[    19.933] 	GreenFieldPosition: 0
[    19.933] 	BlueMaskSize: 0
[    19.933] 	BlueFieldPosition: 0
[    19.933] 	RsvdMaskSize: 0
[    19.933] 	RsvdFieldPosition: 0
[    19.933] 	DirectColorModeInfo: 0
[    19.933] 	PhysBasePtr: 0x0
[    19.933] 	LinBytesPerScanLine: 0
[    19.933] 	BnkNumberOfImagePages: 0
[    19.933] 	LinNumberOfImagePages: 0
[    19.933] 	LinRedMaskSize: 0
[    19.933] 	LinRedFieldPosition: 0
[    19.933] 	LinGreenMaskSize: 0
[    19.933] 	LinGreenFieldPosition: 0
[    19.933] 	LinBlueMaskSize: 0
[    19.933] 	LinBlueFieldPosition: 0
[    19.933] 	LinRsvdMaskSize: 0
[    19.933] 	LinRsvdFieldPosition: 0
[    19.933] 	MaxPixelClock: 0
[    19.933] Mode: 169 (0x0)
[    19.933] 	ModeAttributes: 0x0
[    19.933] 	WinAAttributes: 0x0
[    19.933] 	WinBAttributes: 0x0
[    19.933] 	WinGranularity: 0
[    19.933] 	WinSize: 0
[    19.933] 	WinASegment: 0x0
[    19.933] 	WinBSegment: 0x0
[    19.933] 	WinFuncPtr: 0x0
[    19.933] 	BytesPerScanline: 0
[    19.933] 	XResolution: 0
[    19.933] 	YResolution: 0
[    19.933] 	XCharSize: 0
[    19.933] 	YCharSize: 0
[    19.933] 	NumberOfPlanes: 0
[    19.933] 	BitsPerPixel: 0
[    19.933] 	NumberOfBanks: 0
[    19.933] 	MemoryModel: 0
[    19.933] 	BankSize: 0
[    19.933] 	NumberOfImages: 0
[    19.933] 	RedMaskSize: 0
[    19.933] 	RedFieldPosition: 0
[    19.933] 	GreenMaskSize: 0
[    19.933] 	GreenFieldPosition: 0
[    19.934] 	BlueMaskSize: 0
[    19.934] 	BlueFieldPosition: 0
[    19.934] 	RsvdMaskSize: 0
[    19.934] 	RsvdFieldPosition: 0
[    19.934] 	DirectColorModeInfo: 0
[    19.934] 	PhysBasePtr: 0x0
[    19.934] 	LinBytesPerScanLine: 0
[    19.934] 	BnkNumberOfImagePages: 0
[    19.934] 	LinNumberOfImagePages: 0
[    19.934] 	LinRedMaskSize: 0
[    19.934] 	LinRedFieldPosition: 0
[    19.934] 	LinGreenMaskSize: 0
[    19.934] 	LinGreenFieldPosition: 0
[    19.934] 	LinBlueMaskSize: 0
[    19.934] 	LinBlueFieldPosition: 0
[    19.934] 	LinRsvdMaskSize: 0
[    19.934] 	LinRsvdFieldPosition: 0
[    19.934] 	MaxPixelClock: 0
[    19.934] Mode: 16a (0x0)
[    19.934] 	ModeAttributes: 0x0
[    19.934] 	WinAAttributes: 0x0
[    19.934] 	WinBAttributes: 0x0
[    19.934] 	WinGranularity: 0
[    19.934] 	WinSize: 0
[    19.934] 	WinASegment: 0x0
[    19.934] 	WinBSegment: 0x0
[    19.934] 	WinFuncPtr: 0x0
[    19.934] 	BytesPerScanline: 0
[    19.934] 	XResolution: 0
[    19.934] 	YResolution: 0
[    19.934] 	XCharSize: 0
[    19.934] 	YCharSize: 0
[    19.934] 	NumberOfPlanes: 0
[    19.934] 	BitsPerPixel: 0
[    19.934] 	NumberOfBanks: 0
[    19.934] 	MemoryModel: 0
[    19.934] 	BankSize: 0
[    19.934] 	NumberOfImages: 0
[    19.934] 	RedMaskSize: 0
[    19.934] 	RedFieldPosition: 0
[    19.934] 	GreenMaskSize: 0
[    19.934] 	GreenFieldPosition: 0
[    19.934] 	BlueMaskSize: 0
[    19.934] 	BlueFieldPosition: 0
[    19.934] 	RsvdMaskSize: 0
[    19.934] 	RsvdFieldPosition: 0
[    19.934] 	DirectColorModeInfo: 0
[    19.934] 	PhysBasePtr: 0x0
[    19.934] 	LinBytesPerScanLine: 0
[    19.934] 	BnkNumberOfImagePages: 0
[    19.934] 	LinNumberOfImagePages: 0
[    19.934] 	LinRedMaskSize: 0
[    19.934] 	LinRedFieldPosition: 0
[    19.934] 	LinGreenMaskSize: 0
[    19.934] 	LinGreenFieldPosition: 0
[    19.934] 	LinBlueMaskSize: 0
[    19.934] 	LinBlueFieldPosition: 0
[    19.934] 	LinRsvdMaskSize: 0
[    19.934] 	LinRsvdFieldPosition: 0
[    19.934] 	MaxPixelClock: 0
[    19.934] Mode: 16b (0x0)
[    19.934] 	ModeAttributes: 0x0
[    19.934] 	WinAAttributes: 0x0
[    19.934] 	WinBAttributes: 0x0
[    19.934] 	WinGranularity: 0
[    19.934] 	WinSize: 0
[    19.934] 	WinASegment: 0x0
[    19.934] 	WinBSegment: 0x0
[    19.934] 	WinFuncPtr: 0x0
[    19.934] 	BytesPerScanline: 0
[    19.934] 	XResolution: 0
[    19.934] 	YResolution: 0
[    19.934] 	XCharSize: 0
[    19.934] 	YCharSize: 0
[    19.934] 	NumberOfPlanes: 0
[    19.934] 	BitsPerPixel: 0
[    19.934] 	NumberOfBanks: 0
[    19.934] 	MemoryModel: 0
[    19.934] 	BankSize: 0
[    19.934] 	NumberOfImages: 0
[    19.934] 	RedMaskSize: 0
[    19.934] 	RedFieldPosition: 0
[    19.934] 	GreenMaskSize: 0
[    19.934] 	GreenFieldPosition: 0
[    19.934] 	BlueMaskSize: 0
[    19.934] 	BlueFieldPosition: 0
[    19.934] 	RsvdMaskSize: 0
[    19.934] 	RsvdFieldPosition: 0
[    19.934] 	DirectColorModeInfo: 0
[    19.934] 	PhysBasePtr: 0x0
[    19.934] 	LinBytesPerScanLine: 0
[    19.934] 	BnkNumberOfImagePages: 0
[    19.935] 	LinNumberOfImagePages: 0
[    19.935] 	LinRedMaskSize: 0
[    19.935] 	LinRedFieldPosition: 0
[    19.935] 	LinGreenMaskSize: 0
[    19.935] 	LinGreenFieldPosition: 0
[    19.935] 	LinBlueMaskSize: 0
[    19.935] 	LinBlueFieldPosition: 0
[    19.935] 	LinRsvdMaskSize: 0
[    19.935] 	LinRsvdFieldPosition: 0
[    19.935] 	MaxPixelClock: 0
[    19.935] Mode: 16c (0x0)
[    19.935] 	ModeAttributes: 0x0
[    19.935] 	WinAAttributes: 0x0
[    19.935] 	WinBAttributes: 0x0
[    19.935] 	WinGranularity: 0
[    19.935] 	WinSize: 0
[    19.935] 	WinASegment: 0x0
[    19.935] 	WinBSegment: 0x0
[    19.935] 	WinFuncPtr: 0x0
[    19.935] 	BytesPerScanline: 0
[    19.935] 	XResolution: 0
[    19.935] 	YResolution: 0
[    19.935] 	XCharSize: 0
[    19.935] 	YCharSize: 0
[    19.935] 	NumberOfPlanes: 0
[    19.935] 	BitsPerPixel: 0
[    19.935] 	NumberOfBanks: 0
[    19.935] 	MemoryModel: 0
[    19.935] 	BankSize: 0
[    19.935] 	NumberOfImages: 0
[    19.935] 	RedMaskSize: 0
[    19.935] 	RedFieldPosition: 0
[    19.935] 	GreenMaskSize: 0
[    19.935] 	GreenFieldPosition: 0
[    19.935] 	BlueMaskSize: 0
[    19.935] 	BlueFieldPosition: 0
[    19.935] 	RsvdMaskSize: 0
[    19.935] 	RsvdFieldPosition: 0
[    19.935] 	DirectColorModeInfo: 0
[    19.935] 	PhysBasePtr: 0x0
[    19.935] 	LinBytesPerScanLine: 0
[    19.935] 	BnkNumberOfImagePages: 0
[    19.935] 	LinNumberOfImagePages: 0
[    19.935] 	LinRedMaskSize: 0
[    19.935] 	LinRedFieldPosition: 0
[    19.935] 	LinGreenMaskSize: 0
[    19.935] 	LinGreenFieldPosition: 0
[    19.935] 	LinBlueMaskSize: 0
[    19.935] 	LinBlueFieldPosition: 0
[    19.935] 	LinRsvdMaskSize: 0
[    19.935] 	LinRsvdFieldPosition: 0
[    19.935] 	MaxPixelClock: 0
[    19.935] Mode: 16d (0x0)
[    19.935] 	ModeAttributes: 0x0
[    19.935] 	WinAAttributes: 0x0
[    19.935] 	WinBAttributes: 0x0
[    19.935] 	WinGranularity: 0
[    19.935] 	WinSize: 0
[    19.935] 	WinASegment: 0x0
[    19.935] 	WinBSegment: 0x0
[    19.935] 	WinFuncPtr: 0x0
[    19.935] 	BytesPerScanline: 0
[    19.935] 	XResolution: 0
[    19.935] 	YResolution: 0
[    19.935] 	XCharSize: 0
[    19.935] 	YCharSize: 0
[    19.935] 	NumberOfPlanes: 0
[    19.935] 	BitsPerPixel: 0
[    19.935] 	NumberOfBanks: 0
[    19.935] 	MemoryModel: 0
[    19.935] 	BankSize: 0
[    19.935] 	NumberOfImages: 0
[    19.935] 	RedMaskSize: 0
[    19.935] 	RedFieldPosition: 0
[    19.935] 	GreenMaskSize: 0
[    19.935] 	GreenFieldPosition: 0
[    19.935] 	BlueMaskSize: 0
[    19.935] 	BlueFieldPosition: 0
[    19.935] 	RsvdMaskSize: 0
[    19.935] 	RsvdFieldPosition: 0
[    19.935] 	DirectColorModeInfo: 0
[    19.935] 	PhysBasePtr: 0x0
[    19.935] 	LinBytesPerScanLine: 0
[    19.935] 	BnkNumberOfImagePages: 0
[    19.935] 	LinNumberOfImagePages: 0
[    19.935] 	LinRedMaskSize: 0
[    19.935] 	LinRedFieldPosition: 0
[    19.935] 	LinGreenMaskSize: 0
[    19.935] 	LinGreenFieldPosition: 0
[    19.936] 	LinBlueMaskSize: 0
[    19.936] 	LinBlueFieldPosition: 0
[    19.936] 	LinRsvdMaskSize: 0
[    19.936] 	LinRsvdFieldPosition: 0
[    19.936] 	MaxPixelClock: 0
[    19.936] Mode: 16e (0x0)
[    19.936] 	ModeAttributes: 0x0
[    19.936] 	WinAAttributes: 0x0
[    19.936] 	WinBAttributes: 0x0
[    19.936] 	WinGranularity: 0
[    19.936] 	WinSize: 0
[    19.936] 	WinASegment: 0x0
[    19.936] 	WinBSegment: 0x0
[    19.936] 	WinFuncPtr: 0x0
[    19.938] 	BytesPerScanline: 0
[    19.938] 	XResolution: 0
[    19.938] 	YResolution: 0
[    19.938] 	XCharSize: 0
[    19.938] 	YCharSize: 0
[    19.938] 	NumberOfPlanes: 0
[    19.938] 	BitsPerPixel: 0
[    19.938] 	NumberOfBanks: 0
[    19.938] 	MemoryModel: 0
[    19.938] 	BankSize: 0
[    19.938] 	NumberOfImages: 0
[    19.938] 	RedMaskSize: 0
[    19.938] 	RedFieldPosition: 0
[    19.938] 	GreenMaskSize: 0
[    19.938] 	GreenFieldPosition: 0
[    19.938] 	BlueMaskSize: 0
[    19.938] 	BlueFieldPosition: 0
[    19.938] 	RsvdMaskSize: 0
[    19.938] 	RsvdFieldPosition: 0
[    19.938] 	DirectColorModeInfo: 0
[    19.938] 	PhysBasePtr: 0x0
[    19.938] 	LinBytesPerScanLine: 0
[    19.938] 	BnkNumberOfImagePages: 0
[    19.938] 	LinNumberOfImagePages: 0
[    19.938] 	LinRedMaskSize: 0
[    19.938] 	LinRedFieldPosition: 0
[    19.938] 	LinGreenMaskSize: 0
[    19.938] 	LinGreenFieldPosition: 0
[    19.938] 	LinBlueMaskSize: 0
[    19.938] 	LinBlueFieldPosition: 0
[    19.938] 	LinRsvdMaskSize: 0
[    19.938] 	LinRsvdFieldPosition: 0
[    19.938] 	MaxPixelClock: 0
[    19.938] Mode: 16f (0x0)
[    19.938] 	ModeAttributes: 0x0
[    19.938] 	WinAAttributes: 0x0
[    19.938] 	WinBAttributes: 0x0
[    19.938] 	WinGranularity: 0
[    19.938] 	WinSize: 0
[    19.938] 	WinASegment: 0x0
[    19.938] 	WinBSegment: 0x0
[    19.938] 	WinFuncPtr: 0x0
[    19.938] 	BytesPerScanline: 0
[    19.938] 	XResolution: 0
[    19.938] 	YResolution: 0
[    19.938] 	XCharSize: 0
[    19.938] 	YCharSize: 0
[    19.938] 	NumberOfPlanes: 0
[    19.938] 	BitsPerPixel: 0
[    19.938] 	NumberOfBanks: 0
[    19.938] 	MemoryModel: 0
[    19.938] 	BankSize: 0
[    19.938] 	NumberOfImages: 0
[    19.938] 	RedMaskSize: 0
[    19.938] 	RedFieldPosition: 0
[    19.938] 	GreenMaskSize: 0
[    19.938] 	GreenFieldPosition: 0
[    19.938] 	BlueMaskSize: 0
[    19.938] 	BlueFieldPosition: 0
[    19.938] 	RsvdMaskSize: 0
[    19.938] 	RsvdFieldPosition: 0
[    19.938] 	DirectColorModeInfo: 0
[    19.938] 	PhysBasePtr: 0x0
[    19.938] 	LinBytesPerScanLine: 0
[    19.938] 	BnkNumberOfImagePages: 0
[    19.938] 	LinNumberOfImagePages: 0
[    19.938] 	LinRedMaskSize: 0
[    19.938] 	LinRedFieldPosition: 0
[    19.938] 	LinGreenMaskSize: 0
[    19.938] 	LinGreenFieldPosition: 0
[    19.938] 	LinBlueMaskSize: 0
[    19.938] 	LinBlueFieldPosition: 0
[    19.938] 	LinRsvdMaskSize: 0
[    19.938] 	LinRsvdFieldPosition: 0
[    19.938] 	MaxPixelClock: 0
[    19.938] Mode: 170 (0x0)
[    19.939] 	ModeAttributes: 0x0
[    19.939] 	WinAAttributes: 0x0
[    19.939] 	WinBAttributes: 0x0
[    19.939] 	WinGranularity: 0
[    19.939] 	WinSize: 0
[    19.939] 	WinASegment: 0x0
[    19.939] 	WinBSegment: 0x0
[    19.939] 	WinFuncPtr: 0x0
[    19.939] 	BytesPerScanline: 0
[    19.939] 	XResolution: 0
[    19.939] 	YResolution: 0
[    19.939] 	XCharSize: 0
[    19.939] 	YCharSize: 0
[    19.939] 	NumberOfPlanes: 0
[    19.939] 	BitsPerPixel: 0
[    19.939] 	NumberOfBanks: 0
[    19.939] 	MemoryModel: 0
[    19.939] 	BankSize: 0
[    19.939] 	NumberOfImages: 0
[    19.939] 	RedMaskSize: 0
[    19.939] 	RedFieldPosition: 0
[    19.939] 	GreenMaskSize: 0
[    19.939] 	GreenFieldPosition: 0
[    19.939] 	BlueMaskSize: 0
[    19.939] 	BlueFieldPosition: 0
[    19.939] 	RsvdMaskSize: 0
[    19.939] 	RsvdFieldPosition: 0
[    19.939] 	DirectColorModeInfo: 0
[    19.939] 	PhysBasePtr: 0x0
[    19.939] 	LinBytesPerScanLine: 0
[    19.939] 	BnkNumberOfImagePages: 0
[    19.939] 	LinNumberOfImagePages: 0
[    19.939] 	LinRedMaskSize: 0
[    19.939] 	LinRedFieldPosition: 0
[    19.939] 	LinGreenMaskSize: 0
[    19.939] 	LinGreenFieldPosition: 0
[    19.939] 	LinBlueMaskSize: 0
[    19.939] 	LinBlueFieldPosition: 0
[    19.939] 	LinRsvdMaskSize: 0
[    19.939] 	LinRsvdFieldPosition: 0
[    19.939] 	MaxPixelClock: 0
[    19.939] Mode: 171 (0x0)
[    19.939] 	ModeAttributes: 0x0
[    19.939] 	WinAAttributes: 0x0
[    19.939] 	WinBAttributes: 0x0
[    19.939] 	WinGranularity: 0
[    19.939] 	WinSize: 0
[    19.939] 	WinASegment: 0x0
[    19.939] 	WinBSegment: 0x0
[    19.939] 	WinFuncPtr: 0x0
[    19.939] 	BytesPerScanline: 0
[    19.939] 	XResolution: 0
[    19.939] 	YResolution: 0
[    19.939] 	XCharSize: 0
[    19.939] 	YCharSize: 0
[    19.939] 	NumberOfPlanes: 0
[    19.939] 	BitsPerPixel: 0
[    19.939] 	NumberOfBanks: 0
[    19.939] 	MemoryModel: 0
[    19.939] 	BankSize: 0
[    19.939] 	NumberOfImages: 0
[    19.939] 	RedMaskSize: 0
[    19.939] 	RedFieldPosition: 0
[    19.939] 	GreenMaskSize: 0
[    19.939] 	GreenFieldPosition: 0
[    19.939] 	BlueMaskSize: 0
[    19.939] 	BlueFieldPosition: 0
[    19.939] 	RsvdMaskSize: 0
[    19.939] 	RsvdFieldPosition: 0
[    19.939] 	DirectColorModeInfo: 0
[    19.939] 	PhysBasePtr: 0x0
[    19.939] 	LinBytesPerScanLine: 0
[    19.939] 	BnkNumberOfImagePages: 0
[    19.939] 	LinNumberOfImagePages: 0
[    19.939] 	LinRedMaskSize: 0
[    19.939] 	LinRedFieldPosition: 0
[    19.939] 	LinGreenMaskSize: 0
[    19.939] 	LinGreenFieldPosition: 0
[    19.939] 	LinBlueMaskSize: 0
[    19.939] 	LinBlueFieldPosition: 0
[    19.939] 	LinRsvdMaskSize: 0
[    19.939] 	LinRsvdFieldPosition: 0
[    19.939] 	MaxPixelClock: 0
[    19.940] Mode: 13c (0x0)
[    19.940] 	ModeAttributes: 0x0
[    19.940] 	WinAAttributes: 0x0
[    19.940] 	WinBAttributes: 0x0
[    19.940] 	WinGranularity: 0
[    19.940] 	WinSize: 0
[    19.940] 	WinASegment: 0x0
[    19.940] 	WinBSegment: 0x0
[    19.940] 	WinFuncPtr: 0x0
[    19.940] 	BytesPerScanline: 0
[    19.940] 	XResolution: 0
[    19.940] 	YResolution: 0
[    19.940] 	XCharSize: 0
[    19.940] 	YCharSize: 0
[    19.940] 	NumberOfPlanes: 0
[    19.940] 	BitsPerPixel: 0
[    19.940] 	NumberOfBanks: 0
[    19.940] 	MemoryModel: 0
[    19.940] 	BankSize: 0
[    19.940] 	NumberOfImages: 0
[    19.940] 	RedMaskSize: 0
[    19.940] 	RedFieldPosition: 0
[    19.940] 	GreenMaskSize: 0
[    19.940] 	GreenFieldPosition: 0
[    19.940] 	BlueMaskSize: 0
[    19.940] 	BlueFieldPosition: 0
[    19.940] 	RsvdMaskSize: 0
[    19.940] 	RsvdFieldPosition: 0
[    19.940] 	DirectColorModeInfo: 0
[    19.940] 	PhysBasePtr: 0x0
[    19.940] 	LinBytesPerScanLine: 0
[    19.940] 	BnkNumberOfImagePages: 0
[    19.940] 	LinNumberOfImagePages: 0
[    19.940] 	LinRedMaskSize: 0
[    19.940] 	LinRedFieldPosition: 0
[    19.940] 	LinGreenMaskSize: 0
[    19.940] 	LinGreenFieldPosition: 0
[    19.940] 	LinBlueMaskSize: 0
[    19.940] 	LinBlueFieldPosition: 0
[    19.940] 	LinRsvdMaskSize: 0
[    19.940] 	LinRsvdFieldPosition: 0
[    19.940] 	MaxPixelClock: 0
[    19.940] Mode: 14d (0x0)
[    19.940] 	ModeAttributes: 0x0
[    19.940] 	WinAAttributes: 0x0
[    19.940] 	WinBAttributes: 0x0
[    19.940] 	WinGranularity: 0
[    19.940] 	WinSize: 0
[    19.940] 	WinASegment: 0x0
[    19.940] 	WinBSegment: 0x0
[    19.940] 	WinFuncPtr: 0x0
[    19.940] 	BytesPerScanline: 0
[    19.940] 	XResolution: 0
[    19.940] 	YResolution: 0
[    19.940] 	XCharSize: 0
[    19.940] 	YCharSize: 0
[    19.940] 	NumberOfPlanes: 0
[    19.940] 	BitsPerPixel: 0
[    19.940] 	NumberOfBanks: 0
[    19.940] 	MemoryModel: 0
[    19.940] 	BankSize: 0
[    19.940] 	NumberOfImages: 0
[    19.940] 	RedMaskSize: 0
[    19.940] 	RedFieldPosition: 0
[    19.940] 	GreenMaskSize: 0
[    19.940] 	GreenFieldPosition: 0
[    19.940] 	BlueMaskSize: 0
[    19.940] 	BlueFieldPosition: 0
[    19.940] 	RsvdMaskSize: 0
[    19.940] 	RsvdFieldPosition: 0
[    19.940] 	DirectColorModeInfo: 0
[    19.940] 	PhysBasePtr: 0x0
[    19.940] 	LinBytesPerScanLine: 0
[    19.940] 	BnkNumberOfImagePages: 0
[    19.940] 	LinNumberOfImagePages: 0
[    19.940] 	LinRedMaskSize: 0
[    19.940] 	LinRedFieldPosition: 0
[    19.940] 	LinGreenMaskSize: 0
[    19.940] 	LinGreenFieldPosition: 0
[    19.940] 	LinBlueMaskSize: 0
[    19.940] 	LinBlueFieldPosition: 0
[    19.940] 	LinRsvdMaskSize: 0
[    19.940] 	LinRsvdFieldPosition: 0
[    19.940] 	MaxPixelClock: 0
[    19.941] Mode: 15c (0x0)
[    19.941] 	ModeAttributes: 0x0
[    19.941] 	WinAAttributes: 0x0
[    19.941] 	WinBAttributes: 0x0
[    19.941] 	WinGranularity: 0
[    19.941] 	WinSize: 0
[    19.941] 	WinASegment: 0x0
[    19.941] 	WinBSegment: 0x0
[    19.941] 	WinFuncPtr: 0x0
[    19.941] 	BytesPerScanline: 0
[    19.941] 	XResolution: 0
[    19.941] 	YResolution: 0
[    19.941] 	XCharSize: 0
[    19.941] 	YCharSize: 0
[    19.941] 	NumberOfPlanes: 0
[    19.941] 	BitsPerPixel: 0
[    19.941] 	NumberOfBanks: 0
[    19.941] 	MemoryModel: 0
[    19.941] 	BankSize: 0
[    19.941] 	NumberOfImages: 0
[    19.941] 	RedMaskSize: 0
[    19.941] 	RedFieldPosition: 0
[    19.941] 	GreenMaskSize: 0
[    19.941] 	GreenFieldPosition: 0
[    19.941] 	BlueMaskSize: 0
[    19.941] 	BlueFieldPosition: 0
[    19.941] 	RsvdMaskSize: 0
[    19.941] 	RsvdFieldPosition: 0
[    19.941] 	DirectColorModeInfo: 0
[    19.941] 	PhysBasePtr: 0x0
[    19.941] 	LinBytesPerScanLine: 0
[    19.941] 	BnkNumberOfImagePages: 0
[    19.941] 	LinNumberOfImagePages: 0
[    19.941] 	LinRedMaskSize: 0
[    19.941] 	LinRedFieldPosition: 0
[    19.941] 	LinGreenMaskSize: 0
[    19.941] 	LinGreenFieldPosition: 0
[    19.941] 	LinBlueMaskSize: 0
[    19.941] 	LinBlueFieldPosition: 0
[    19.941] 	LinRsvdMaskSize: 0
[    19.941] 	LinRsvdFieldPosition: 0
[    19.941] 	MaxPixelClock: 0
[    19.941] Mode: 13a (0x0)
[    19.941] 	ModeAttributes: 0x0
[    19.941] 	WinAAttributes: 0x0
[    19.941] 	WinBAttributes: 0x0
[    19.941] 	WinGranularity: 0
[    19.941] 	WinSize: 0
[    19.941] 	WinASegment: 0x0
[    19.941] 	WinBSegment: 0x0
[    19.941] 	WinFuncPtr: 0x0
[    19.941] 	BytesPerScanline: 0
[    19.941] 	XResolution: 0
[    19.941] 	YResolution: 0
[    19.941] 	XCharSize: 0
[    19.941] 	YCharSize: 0
[    19.941] 	NumberOfPlanes: 0
[    19.941] 	BitsPerPixel: 0
[    19.941] 	NumberOfBanks: 0
[    19.941] 	MemoryModel: 0
[    19.941] 	BankSize: 0
[    19.941] 	NumberOfImages: 0
[    19.941] 	RedMaskSize: 0
[    19.941] 	RedFieldPosition: 0
[    19.941] 	GreenMaskSize: 0
[    19.942] 	GreenFieldPosition: 0
[    19.942] 	BlueMaskSize: 0
[    19.942] 	BlueFieldPosition: 0
[    19.942] 	RsvdMaskSize: 0
[    19.942] 	RsvdFieldPosition: 0
[    19.942] 	DirectColorModeInfo: 0
[    19.942] 	PhysBasePtr: 0x0
[    19.942] 	LinBytesPerScanLine: 0
[    19.942] 	BnkNumberOfImagePages: 0
[    19.942] 	LinNumberOfImagePages: 0
[    19.942] 	LinRedMaskSize: 0
[    19.942] 	LinRedFieldPosition: 0
[    19.942] 	LinGreenMaskSize: 0
[    19.942] 	LinGreenFieldPosition: 0
[    19.942] 	LinBlueMaskSize: 0
[    19.942] 	LinBlueFieldPosition: 0
[    19.942] 	LinRsvdMaskSize: 0
[    19.942] 	LinRsvdFieldPosition: 0
[    19.942] 	MaxPixelClock: 0
[    19.942] Mode: 14b (0x0)
[    19.942] 	ModeAttributes: 0x0
[    19.942] 	WinAAttributes: 0x0
[    19.942] 	WinBAttributes: 0x0
[    19.942] 	WinGranularity: 0
[    19.942] 	WinSize: 0
[    19.942] 	WinASegment: 0x0
[    19.942] 	WinBSegment: 0x0
[    19.942] 	WinFuncPtr: 0x0
[    19.942] 	BytesPerScanline: 0
[    19.942] 	XResolution: 0
[    19.942] 	YResolution: 0
[    19.942] 	XCharSize: 0
[    19.942] 	YCharSize: 0
[    19.942] 	NumberOfPlanes: 0
[    19.942] 	BitsPerPixel: 0
[    19.942] 	NumberOfBanks: 0
[    19.942] 	MemoryModel: 0
[    19.942] 	BankSize: 0
[    19.942] 	NumberOfImages: 0
[    19.942] 	RedMaskSize: 0
[    19.942] 	RedFieldPosition: 0
[    19.942] 	GreenMaskSize: 0
[    19.942] 	GreenFieldPosition: 0
[    19.942] 	BlueMaskSize: 0
[    19.942] 	BlueFieldPosition: 0
[    19.942] 	RsvdMaskSize: 0
[    19.942] 	RsvdFieldPosition: 0
[    19.942] 	DirectColorModeInfo: 0
[    19.942] 	PhysBasePtr: 0x0
[    19.942] 	LinBytesPerScanLine: 0
[    19.942] 	BnkNumberOfImagePages: 0
[    19.942] 	LinNumberOfImagePages: 0
[    19.942] 	LinRedMaskSize: 0
[    19.942] 	LinRedFieldPosition: 0
[    19.942] 	LinGreenMaskSize: 0
[    19.942] 	LinGreenFieldPosition: 0
[    19.942] 	LinBlueMaskSize: 0
[    19.942] 	LinBlueFieldPosition: 0
[    19.942] 	LinRsvdMaskSize: 0
[    19.942] 	LinRsvdFieldPosition: 0
[    19.942] 	MaxPixelClock: 0
[    19.942] Mode: 15a (0x0)
[    19.943] 	ModeAttributes: 0x0
[    19.943] 	WinAAttributes: 0x0
[    19.943] 	WinBAttributes: 0x0
[    19.943] 	WinGranularity: 0
[    19.943] 	WinSize: 0
[    19.943] 	WinASegment: 0x0
[    19.943] 	WinBSegment: 0x0
[    19.943] 	WinFuncPtr: 0x0
[    19.943] 	BytesPerScanline: 0
[    19.943] 	XResolution: 0
[    19.943] 	YResolution: 0
[    19.943] 	XCharSize: 0
[    19.943] 	YCharSize: 0
[    19.943] 	NumberOfPlanes: 0
[    19.943] 	BitsPerPixel: 0
[    19.943] 	NumberOfBanks: 0
[    19.943] 	MemoryModel: 0
[    19.943] 	BankSize: 0
[    19.943] 	NumberOfImages: 0
[    19.943] 	RedMaskSize: 0
[    19.943] 	RedFieldPosition: 0
[    19.943] 	GreenMaskSize: 0
[    19.943] 	GreenFieldPosition: 0
[    19.943] 	BlueMaskSize: 0
[    19.943] 	BlueFieldPosition: 0
[    19.943] 	RsvdMaskSize: 0
[    19.943] 	RsvdFieldPosition: 0
[    19.943] 	DirectColorModeInfo: 0
[    19.943] 	PhysBasePtr: 0x0
[    19.943] 	LinBytesPerScanLine: 0
[    19.943] 	BnkNumberOfImagePages: 0
[    19.943] 	LinNumberOfImagePages: 0
[    19.943] 	LinRedMaskSize: 0
[    19.943] 	LinRedFieldPosition: 0
[    19.943] 	LinGreenMaskSize: 0
[    19.943] 	LinGreenFieldPosition: 0
[    19.943] 	LinBlueMaskSize: 0
[    19.943] 	LinBlueFieldPosition: 0
[    19.943] 	LinRsvdMaskSize: 0
[    19.943] 	LinRsvdFieldPosition: 0
[    19.943] 	MaxPixelClock: 0
[    19.943] Mode: 107 (0x0)
[    19.943] 	ModeAttributes: 0x0
[    19.943] 	WinAAttributes: 0x0
[    19.943] 	WinBAttributes: 0x0
[    19.943] 	WinGranularity: 0
[    19.943] 	WinSize: 0
[    19.943] 	WinASegment: 0x0
[    19.943] 	WinBSegment: 0x0
[    19.943] 	WinFuncPtr: 0x0
[    19.943] 	BytesPerScanline: 0
[    19.943] 	XResolution: 0
[    19.943] 	YResolution: 0
[    19.943] 	XCharSize: 0
[    19.943] 	YCharSize: 0
[    19.943] 	NumberOfPlanes: 0
[    19.943] 	BitsPerPixel: 0
[    19.943] 	NumberOfBanks: 0
[    19.943] 	MemoryModel: 0
[    19.943] 	BankSize: 0
[    19.943] 	NumberOfImages: 0
[    19.943] 	RedMaskSize: 0
[    19.943] 	RedFieldPosition: 0
[    19.943] 	GreenMaskSize: 0
[    19.943] 	GreenFieldPosition: 0
[    19.943] 	BlueMaskSize: 0
[    19.943] 	BlueFieldPosition: 0
[    19.943] 	RsvdMaskSize: 0
[    19.943] 	RsvdFieldPosition: 0
[    19.943] 	DirectColorModeInfo: 0
[    19.943] 	PhysBasePtr: 0x0
[    19.943] 	LinBytesPerScanLine: 0
[    19.943] 	BnkNumberOfImagePages: 0
[    19.943] 	LinNumberOfImagePages: 0
[    19.943] 	LinRedMaskSize: 0
[    19.943] 	LinRedFieldPosition: 0
[    19.943] 	LinGreenMaskSize: 0
[    19.943] 	LinGreenFieldPosition: 0
[    19.943] 	LinBlueMaskSize: 0
[    19.943] 	LinBlueFieldPosition: 0
[    19.943] 	LinRsvdMaskSize: 0
[    19.943] 	LinRsvdFieldPosition: 0
[    19.943] 	MaxPixelClock: 0
[    19.944] Mode: 11a (0x0)
[    19.944] 	ModeAttributes: 0x0
[    19.944] 	WinAAttributes: 0x0
[    19.944] 	WinBAttributes: 0x0
[    19.944] 	WinGranularity: 0
[    19.944] 	WinSize: 0
[    19.944] 	WinASegment: 0x0
[    19.944] 	WinBSegment: 0x0
[    19.944] 	WinFuncPtr: 0x0
[    19.944] 	BytesPerScanline: 0
[    19.944] 	XResolution: 0
[    19.944] 	YResolution: 0
[    19.944] 	XCharSize: 0
[    19.944] 	YCharSize: 0
[    19.944] 	NumberOfPlanes: 0
[    19.944] 	BitsPerPixel: 0
[    19.944] 	NumberOfBanks: 0
[    19.944] 	MemoryModel: 0
[    19.944] 	BankSize: 0
[    19.944] 	NumberOfImages: 0
[    19.944] 	RedMaskSize: 0
[    19.944] 	RedFieldPosition: 0
[    19.944] 	GreenMaskSize: 0
[    19.944] 	GreenFieldPosition: 0
[    19.944] 	BlueMaskSize: 0
[    19.944] 	BlueFieldPosition: 0
[    19.944] 	RsvdMaskSize: 0
[    19.944] 	RsvdFieldPosition: 0
[    19.944] 	DirectColorModeInfo: 0
[    19.944] 	PhysBasePtr: 0x0
[    19.944] 	LinBytesPerScanLine: 0
[    19.944] 	BnkNumberOfImagePages: 0
[    19.944] 	LinNumberOfImagePages: 0
[    19.944] 	LinRedMaskSize: 0
[    19.944] 	LinRedFieldPosition: 0
[    19.944] 	LinGreenMaskSize: 0
[    19.944] 	LinGreenFieldPosition: 0
[    19.944] 	LinBlueMaskSize: 0
[    19.944] 	LinBlueFieldPosition: 0
[    19.944] 	LinRsvdMaskSize: 0
[    19.944] 	LinRsvdFieldPosition: 0
[    19.944] 	MaxPixelClock: 0
[    19.944] Mode: 11b (0x0)
[    19.944] 	ModeAttributes: 0x0
[    19.944] 	WinAAttributes: 0x0
[    19.944] 	WinBAttributes: 0x0
[    19.944] 	WinGranularity: 0
[    19.944] 	WinSize: 0
[    19.944] 	WinASegment: 0x0
[    19.944] 	WinBSegment: 0x0
[    19.944] 	WinFuncPtr: 0x0
[    19.944] 	BytesPerScanline: 0
[    19.944] 	XResolution: 0
[    19.944] 	YResolution: 0
[    19.944] 	XCharSize: 0
[    19.944] 	YCharSize: 0
[    19.944] 	NumberOfPlanes: 0
[    19.944] 	BitsPerPixel: 0
[    19.944] 	NumberOfBanks: 0
[    19.944] 	MemoryModel: 0
[    19.944] 	BankSize: 0
[    19.944] 	NumberOfImages: 0
[    19.944] 	RedMaskSize: 0
[    19.944] 	RedFieldPosition: 0
[    19.944] 	GreenMaskSize: 0
[    19.944] 	GreenFieldPosition: 0
[    19.944] 	BlueMaskSize: 0
[    19.944] 	BlueFieldPosition: 0
[    19.944] 	RsvdMaskSize: 0
[    19.944] 	RsvdFieldPosition: 0
[    19.944] 	DirectColorModeInfo: 0
[    19.944] 	PhysBasePtr: 0x0
[    19.945] 	LinBytesPerScanLine: 0
[    19.945] 	BnkNumberOfImagePages: 0
[    19.945] 	LinNumberOfImagePages: 0
[    19.945] 	LinRedMaskSize: 0
[    19.945] 	LinRedFieldPosition: 0
[    19.945] 	LinGreenMaskSize: 0
[    19.945] 	LinGreenFieldPosition: 0
[    19.945] 	LinBlueMaskSize: 0
[    19.945] 	LinBlueFieldPosition: 0
[    19.945] 	LinRsvdMaskSize: 0
[    19.945] 	LinRsvdFieldPosition: 0
[    19.945] 	MaxPixelClock: 0
[    19.945] Mode: 105 (1024x768)
[    19.945] 	ModeAttributes: 0x9b
[    19.945] 	WinAAttributes: 0x7
[    19.945] 	WinBAttributes: 0x0
[    19.945] 	WinGranularity: 64
[    19.945] 	WinSize: 64
[    19.945] 	WinASegment: 0xa000
[    19.945] 	WinBSegment: 0x0
[    19.945] 	WinFuncPtr: 0xc00083ea
[    19.945] 	BytesPerScanline: 1024
[    19.945] 	XResolution: 1024
[    19.945] 	YResolution: 768
[    19.945] 	XCharSize: 8
[    19.945] 	YCharSize: 16
[    19.945] 	NumberOfPlanes: 1
[    19.945] 	BitsPerPixel: 8
[    19.945] 	NumberOfBanks: 1
[    19.945] 	MemoryModel: 4
[    19.945] 	BankSize: 0
[    19.945] 	NumberOfImages: 84
[    19.945] 	RedMaskSize: 0
[    19.945] 	RedFieldPosition: 0
[    19.945] 	GreenMaskSize: 0
[    19.945] 	GreenFieldPosition: 0
[    19.945] 	BlueMaskSize: 0
[    19.945] 	BlueFieldPosition: 0
[    19.945] 	RsvdMaskSize: 0
[    19.945] 	RsvdFieldPosition: 0
[    19.945] 	DirectColorModeInfo: 0
[    19.945] 	PhysBasePtr: 0x80000000
[    19.945] 	LinBytesPerScanLine: 1024
[    19.945] 	BnkNumberOfImagePages: 84
[    19.945] 	LinNumberOfImagePages: 84
[    19.945] 	LinRedMaskSize: 0
[    19.945] 	LinRedFieldPosition: 0
[    19.945] 	LinGreenMaskSize: 0
[    19.945] 	LinGreenFieldPosition: 0
[    19.945] 	LinBlueMaskSize: 0
[    19.945] 	LinBlueFieldPosition: 0
[    19.945] 	LinRsvdMaskSize: 0
[    19.945] 	LinRsvdFieldPosition: 0
[    19.945] 	MaxPixelClock: 230000000
[    19.948] Mode: 117 (1024x768)
[    19.948] 	ModeAttributes: 0x9b
[    19.948] 	WinAAttributes: 0x7
[    19.948] 	WinBAttributes: 0x0
[    19.948] 	WinGranularity: 64
[    19.948] 	WinSize: 64
[    19.948] 	WinASegment: 0xa000
[    19.948] 	WinBSegment: 0x0
[    19.948] 	WinFuncPtr: 0xc00083ea
[    19.948] 	BytesPerScanline: 2048
[    19.948] 	XResolution: 1024
[    19.948] 	YResolution: 768
[    19.948] 	XCharSize: 8
[    19.948] 	YCharSize: 16
[    19.948] 	NumberOfPlanes: 1
[    19.948] 	BitsPerPixel: 16
[    19.948] 	NumberOfBanks: 1
[    19.948] 	MemoryModel: 6
[    19.948] 	BankSize: 0
[    19.948] 	NumberOfImages: 41
[    19.948] 	RedMaskSize: 5
[    19.948] 	RedFieldPosition: 11
[    19.948] 	GreenMaskSize: 6
[    19.948] 	GreenFieldPosition: 5
[    19.948] 	BlueMaskSize: 5
[    19.948] 	BlueFieldPosition: 0
[    19.948] 	RsvdMaskSize: 0
[    19.948] 	RsvdFieldPosition: 0
[    19.948] 	DirectColorModeInfo: 0
[    19.948] 	PhysBasePtr: 0x80000000
[    19.948] 	LinBytesPerScanLine: 2048
[    19.948] 	BnkNumberOfImagePages: 41
[    19.948] 	LinNumberOfImagePages: 41
[    19.948] 	LinRedMaskSize: 5
[    19.948] 	LinRedFieldPosition: 11
[    19.948] 	LinGreenMaskSize: 6
[    19.948] 	LinGreenFieldPosition: 5
[    19.948] 	LinBlueMaskSize: 5
[    19.948] 	LinBlueFieldPosition: 0
[    19.948] 	LinRsvdMaskSize: 0
[    19.948] 	LinRsvdFieldPosition: 0
[    19.948] 	MaxPixelClock: 230000000
[    19.949] *Mode: 118 (1024x768)
[    19.949] 	ModeAttributes: 0x9b
[    19.949] 	WinAAttributes: 0x7
[    19.949] 	WinBAttributes: 0x0
[    19.949] 	WinGranularity: 64
[    19.949] 	WinSize: 64
[    19.949] 	WinASegment: 0xa000
[    19.949] 	WinBSegment: 0x0
[    19.949] 	WinFuncPtr: 0xc00083ea
[    19.949] 	BytesPerScanline: 4096
[    19.949] 	XResolution: 1024
[    19.949] 	YResolution: 768
[    19.949] 	XCharSize: 8
[    19.949] 	YCharSize: 16
[    19.949] 	NumberOfPlanes: 1
[    19.949] 	BitsPerPixel: 32
[    19.949] 	NumberOfBanks: 1
[    19.949] 	MemoryModel: 6
[    19.949] 	BankSize: 0
[    19.949] 	NumberOfImages: 20
[    19.949] 	RedMaskSize: 8
[    19.949] 	RedFieldPosition: 16
[    19.949] 	GreenMaskSize: 8
[    19.949] 	GreenFieldPosition: 8
[    19.949] 	BlueMaskSize: 8
[    19.949] 	BlueFieldPosition: 0
[    19.949] 	RsvdMaskSize: 8
[    19.949] 	RsvdFieldPosition: 24
[    19.949] 	DirectColorModeInfo: 0
[    19.949] 	PhysBasePtr: 0x80000000
[    19.949] 	LinBytesPerScanLine: 4096
[    19.949] 	BnkNumberOfImagePages: 20
[    19.949] 	LinNumberOfImagePages: 20
[    19.949] 	LinRedMaskSize: 8
[    19.949] 	LinRedFieldPosition: 16
[    19.949] 	LinGreenMaskSize: 8
[    19.949] 	LinGreenFieldPosition: 8
[    19.949] 	LinBlueMaskSize: 8
[    19.949] 	LinBlueFieldPosition: 0
[    19.949] 	LinRsvdMaskSize: 8
[    19.949] 	LinRsvdFieldPosition: 24
[    19.949] 	MaxPixelClock: 230000000
[    19.949] *Mode: 112 (640x480)
[    19.949] 	ModeAttributes: 0x9b
[    19.949] 	WinAAttributes: 0x7
[    19.949] 	WinBAttributes: 0x0
[    19.949] 	WinGranularity: 64
[    19.949] 	WinSize: 64
[    19.949] 	WinASegment: 0xa000
[    19.949] 	WinBSegment: 0x0
[    19.949] 	WinFuncPtr: 0xc00083ea
[    19.949] 	BytesPerScanline: 2560
[    19.949] 	XResolution: 640
[    19.949] 	YResolution: 480
[    19.949] 	XCharSize: 8
[    19.950] 	YCharSize: 16
[    19.950] 	NumberOfPlanes: 1
[    19.950] 	BitsPerPixel: 32
[    19.950] 	NumberOfBanks: 1
[    19.950] 	MemoryModel: 6
[    19.950] 	BankSize: 0
[    19.950] 	NumberOfImages: 52
[    19.950] 	RedMaskSize: 8
[    19.950] 	RedFieldPosition: 16
[    19.950] 	GreenMaskSize: 8
[    19.950] 	GreenFieldPosition: 8
[    19.950] 	BlueMaskSize: 8
[    19.950] 	BlueFieldPosition: 0
[    19.950] 	RsvdMaskSize: 8
[    19.950] 	RsvdFieldPosition: 24
[    19.950] 	DirectColorModeInfo: 0
[    19.950] 	PhysBasePtr: 0x80000000
[    19.950] 	LinBytesPerScanLine: 2560
[    19.950] 	BnkNumberOfImagePages: 52
[    19.950] 	LinNumberOfImagePages: 52
[    19.950] 	LinRedMaskSize: 8
[    19.950] 	LinRedFieldPosition: 16
[    19.950] 	LinGreenMaskSize: 8
[    19.950] 	LinGreenFieldPosition: 8
[    19.950] 	LinBlueMaskSize: 8
[    19.950] 	LinBlueFieldPosition: 0
[    19.950] 	LinRsvdMaskSize: 8
[    19.950] 	LinRsvdFieldPosition: 24
[    19.950] 	MaxPixelClock: 230000000
[    19.950] Mode: 114 (800x600)
[    19.950] 	ModeAttributes: 0x9b
[    19.950] 	WinAAttributes: 0x7
[    19.950] 	WinBAttributes: 0x0
[    19.950] 	WinGranularity: 64
[    19.950] 	WinSize: 64
[    19.950] 	WinASegment: 0xa000
[    19.950] 	WinBSegment: 0x0
[    19.950] 	WinFuncPtr: 0xc00083ea
[    19.950] 	BytesPerScanline: 1600
[    19.950] 	XResolution: 800
[    19.950] 	YResolution: 600
[    19.950] 	XCharSize: 8
[    19.950] 	YCharSize: 16
[    19.950] 	NumberOfPlanes: 1
[    19.950] 	BitsPerPixel: 16
[    19.950] 	NumberOfBanks: 1
[    19.950] 	MemoryModel: 6
[    19.950] 	BankSize: 0
[    19.950] 	NumberOfImages: 67
[    19.950] 	RedMaskSize: 5
[    19.950] 	RedFieldPosition: 11
[    19.950] 	GreenMaskSize: 6
[    19.950] 	GreenFieldPosition: 5
[    19.950] 	BlueMaskSize: 5
[    19.950] 	BlueFieldPosition: 0
[    19.950] 	RsvdMaskSize: 0
[    19.950] 	RsvdFieldPosition: 0
[    19.950] 	DirectColorModeInfo: 0
[    19.950] 	PhysBasePtr: 0x80000000
[    19.950] 	LinBytesPerScanLine: 1600
[    19.950] 	BnkNumberOfImagePages: 67
[    19.950] 	LinNumberOfImagePages: 67
[    19.950] 	LinRedMaskSize: 5
[    19.950] 	LinRedFieldPosition: 11
[    19.950] 	LinGreenMaskSize: 6
[    19.950] 	LinGreenFieldPosition: 5
[    19.950] 	LinBlueMaskSize: 5
[    19.950] 	LinBlueFieldPosition: 0
[    19.951] 	LinRsvdMaskSize: 0
[    19.951] 	LinRsvdFieldPosition: 0
[    19.951] 	MaxPixelClock: 230000000
[    19.953] *Mode: 115 (800x600)
[    19.953] 	ModeAttributes: 0x9b
[    19.953] 	WinAAttributes: 0x7
[    19.953] 	WinBAttributes: 0x0
[    19.953] 	WinGranularity: 64
[    19.953] 	WinSize: 64
[    19.953] 	WinASegment: 0xa000
[    19.953] 	WinBSegment: 0x0
[    19.953] 	WinFuncPtr: 0xc00083ea
[    19.953] 	BytesPerScanline: 3200
[    19.953] 	XResolution: 800
[    19.953] 	YResolution: 600
[    19.953] 	XCharSize: 8
[    19.953] 	YCharSize: 16
[    19.953] 	NumberOfPlanes: 1
[    19.953] 	BitsPerPixel: 32
[    19.953] 	NumberOfBanks: 1
[    19.953] 	MemoryModel: 6
[    19.953] 	BankSize: 0
[    19.953] 	NumberOfImages: 33
[    19.953] 	RedMaskSize: 8
[    19.953] 	RedFieldPosition: 16
[    19.953] 	GreenMaskSize: 8
[    19.953] 	GreenFieldPosition: 8
[    19.953] 	BlueMaskSize: 8
[    19.953] 	BlueFieldPosition: 0
[    19.953] 	RsvdMaskSize: 8
[    19.953] 	RsvdFieldPosition: 24
[    19.953] 	DirectColorModeInfo: 0
[    19.953] 	PhysBasePtr: 0x80000000
[    19.953] 	LinBytesPerScanLine: 3200
[    19.953] 	BnkNumberOfImagePages: 33
[    19.953] 	LinNumberOfImagePages: 33
[    19.953] 	LinRedMaskSize: 8
[    19.953] 	LinRedFieldPosition: 16
[    19.953] 	LinGreenMaskSize: 8
[    19.953] 	LinGreenFieldPosition: 8
[    19.953] 	LinBlueMaskSize: 8
[    19.953] 	LinBlueFieldPosition: 0
[    19.953] 	LinRsvdMaskSize: 8
[    19.953] 	LinRsvdFieldPosition: 24
[    19.953] 	MaxPixelClock: 230000000
[    19.954] Mode: 101 (640x480)
[    19.954] 	ModeAttributes: 0x9b
[    19.954] 	WinAAttributes: 0x7
[    19.954] 	WinBAttributes: 0x0
[    19.954] 	WinGranularity: 64
[    19.954] 	WinSize: 64
[    19.954] 	WinASegment: 0xa000
[    19.954] 	WinBSegment: 0x0
[    19.954] 	WinFuncPtr: 0xc00083ea
[    19.954] 	BytesPerScanline: 640
[    19.954] 	XResolution: 640
[    19.954] 	YResolution: 480
[    19.954] 	XCharSize: 8
[    19.954] 	YCharSize: 16
[    19.954] 	NumberOfPlanes: 1
[    19.954] 	BitsPerPixel: 8
[    19.954] 	NumberOfBanks: 1
[    19.954] 	MemoryModel: 4
[    19.954] 	BankSize: 0
[    19.954] 	NumberOfImages: 203
[    19.954] 	RedMaskSize: 0
[    19.954] 	RedFieldPosition: 0
[    19.954] 	GreenMaskSize: 0
[    19.954] 	GreenFieldPosition: 0
[    19.954] 	BlueMaskSize: 0
[    19.954] 	BlueFieldPosition: 0
[    19.954] 	RsvdMaskSize: 0
[    19.954] 	RsvdFieldPosition: 0
[    19.954] 	DirectColorModeInfo: 0
[    19.954] 	PhysBasePtr: 0x80000000
[    19.954] 	LinBytesPerScanLine: 640
[    19.954] 	BnkNumberOfImagePages: 203
[    19.954] 	LinNumberOfImagePages: 203
[    19.954] 	LinRedMaskSize: 0
[    19.954] 	LinRedFieldPosition: 0
[    19.954] 	LinGreenMaskSize: 0
[    19.954] 	LinGreenFieldPosition: 0
[    19.954] 	LinBlueMaskSize: 0
[    19.954] 	LinBlueFieldPosition: 0
[    19.954] 	LinRsvdMaskSize: 0
[    19.954] 	LinRsvdFieldPosition: 0
[    19.954] 	MaxPixelClock: 230000000
[    19.954] Mode: 103 (800x600)
[    19.954] 	ModeAttributes: 0x9b
[    19.954] 	WinAAttributes: 0x7
[    19.954] 	WinBAttributes: 0x0
[    19.954] 	WinGranularity: 64
[    19.954] 	WinSize: 64
[    19.954] 	WinASegment: 0xa000
[    19.955] 	WinBSegment: 0x0
[    19.955] 	WinFuncPtr: 0xc00083ea
[    19.955] 	BytesPerScanline: 832
[    19.955] 	XResolution: 800
[    19.955] 	YResolution: 600
[    19.955] 	XCharSize: 8
[    19.955] 	YCharSize: 16
[    19.955] 	NumberOfPlanes: 1
[    19.955] 	BitsPerPixel: 8
[    19.955] 	NumberOfBanks: 1
[    19.955] 	MemoryModel: 4
[    19.955] 	BankSize: 0
[    19.955] 	NumberOfImages: 126
[    19.955] 	RedMaskSize: 0
[    19.955] 	RedFieldPosition: 0
[    19.955] 	GreenMaskSize: 0
[    19.955] 	GreenFieldPosition: 0
[    19.955] 	BlueMaskSize: 0
[    19.955] 	BlueFieldPosition: 0
[    19.955] 	RsvdMaskSize: 0
[    19.955] 	RsvdFieldPosition: 0
[    19.955] 	DirectColorModeInfo: 0
[    19.955] 	PhysBasePtr: 0x80000000
[    19.955] 	LinBytesPerScanLine: 832
[    19.955] 	BnkNumberOfImagePages: 126
[    19.955] 	LinNumberOfImagePages: 126
[    19.955] 	LinRedMaskSize: 0
[    19.955] 	LinRedFieldPosition: 0
[    19.955] 	LinGreenMaskSize: 0
[    19.955] 	LinGreenFieldPosition: 0
[    19.955] 	LinBlueMaskSize: 0
[    19.955] 	LinBlueFieldPosition: 0
[    19.955] 	LinRsvdMaskSize: 0
[    19.955] 	LinRsvdFieldPosition: 0
[    19.955] 	MaxPixelClock: 230000000
[    19.955] Mode: 111 (640x480)
[    19.955] 	ModeAttributes: 0x9b
[    19.955] 	WinAAttributes: 0x7
[    19.955] 	WinBAttributes: 0x0
[    19.955] 	WinGranularity: 64
[    19.955] 	WinSize: 64
[    19.955] 	WinASegment: 0xa000
[    19.955] 	WinBSegment: 0x0
[    19.955] 	WinFuncPtr: 0xc00083ea
[    19.955] 	BytesPerScanline: 1280
[    19.955] 	XResolution: 640
[    19.955] 	YResolution: 480
[    19.955] 	XCharSize: 8
[    19.955] 	YCharSize: 16
[    19.955] 	NumberOfPlanes: 1
[    19.955] 	BitsPerPixel: 16
[    19.955] 	NumberOfBanks: 1
[    19.955] 	MemoryModel: 6
[    19.955] 	BankSize: 0
[    19.955] 	NumberOfImages: 101
[    19.955] 	RedMaskSize: 5
[    19.955] 	RedFieldPosition: 11
[    19.955] 	GreenMaskSize: 6
[    19.955] 	GreenFieldPosition: 5
[    19.955] 	BlueMaskSize: 5
[    19.955] 	BlueFieldPosition: 0
[    19.955] 	RsvdMaskSize: 0
[    19.955] 	RsvdFieldPosition: 0
[    19.955] 	DirectColorModeInfo: 0
[    19.955] 	PhysBasePtr: 0x80000000
[    19.955] 	LinBytesPerScanLine: 1280
[    19.955] 	BnkNumberOfImagePages: 101
[    19.955] 	LinNumberOfImagePages: 101
[    19.955] 	LinRedMaskSize: 5
[    19.956] 	LinRedFieldPosition: 11
[    19.956] 	LinGreenMaskSize: 6
[    19.956] 	LinGreenFieldPosition: 5
[    19.956] 	LinBlueMaskSize: 5
[    19.956] 	LinBlueFieldPosition: 0
[    19.956] 	LinRsvdMaskSize: 0
[    19.956] 	LinRsvdFieldPosition: 0
[    19.956] 	MaxPixelClock: 230000000
[    19.956] 
[    19.956] (II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
[    19.956] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    19.956] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    19.956] (WW) VESA(0): Unable to estimate virtual size
[    19.956] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    19.956] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    19.956] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    19.956] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    19.956] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    19.956] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    19.956] (WW) VESA(0): Unable to estimate virtual size
[    19.956] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    19.956] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    19.956] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    19.956] (**) VESA(0): *Built-in mode "1024x768"
[    19.956] (**) VESA(0): Display dimensions: (340, 190) mm
[    19.956] (**) VESA(0): DPI set to (76, 102)
[    19.956] (**) VESA(0): Using "Shadow Framebuffer"
[    19.956] (II) Loading sub module "shadow"
[    19.956] (II) LoadModule: "shadow"
[    19.956] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    19.956] (II) Module shadow: vendor="X.Org Foundation"
[    19.956] 	compiled for 1.11.3, module version = 1.1.0
[    19.956] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.956] (II) Loading sub module "fb"
[    19.956] (II) LoadModule: "fb"
[    19.957] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.957] (II) Module fb: vendor="X.Org Foundation"
[    19.957] 	compiled for 1.11.3, module version = 1.0.0
[    19.957] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.957] (II) UnloadModule: "fbdev"
[    19.957] (II) Unloading fbdev
[    19.957] (II) UnloadModule: "fbdevhw"
[    19.957] (II) Unloading fbdevhw
[    19.957] (==) Depth 24 pixmap format is 32 bpp
[    19.957] (II) Loading sub module "int10"
[    19.957] (II) LoadModule: "int10"
[    19.957] (II) Loading /usr/lib/xorg/modules/libint10.so
[    19.957] (II) Module int10: vendor="X.Org Foundation"
[    19.957] 	compiled for 1.11.3, module version = 1.0.0
[    19.957] 	ABI class: X.Org Video Driver, version 11.0
[    19.957] (II) VESA(0): initializing int10
[    19.958] (II) VESA(0): Bad V_BIOS checksum
[    19.958] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    19.958] (II) VESA(0): VESA BIOS detected
[    19.958] (II) VESA(0): VESA VBE Version 3.0
[    19.958] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    19.958] (II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
[    19.958] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    19.958] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    19.958] (II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
[    19.958] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    19.971] (II) VESA(0): virtual address = 0xb0d49000,
	physical address = 0x80000000, size = 67043328
[    19.978] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    20.023] (==) VESA(0): Default visual is TrueColor
[    20.024] (==) VESA(0): Backing store disabled
[    20.024] (==) VESA(0): DPMS enabled
[    20.024] (==) RandR enabled
[    20.024] (II) Initializing built-in extension Generic Event Extension
[    20.024] (II) Initializing built-in extension SHAPE
[    20.024] (II) Initializing built-in extension MIT-SHM
[    20.024] (II) Initializing built-in extension XInputExtension
[    20.024] (II) Initializing built-in extension XTEST
[    20.024] (II) Initializing built-in extension BIG-REQUESTS
[    20.024] (II) Initializing built-in extension SYNC
[    20.024] (II) Initializing built-in extension XKEYBOARD
[    20.024] (II) Initializing built-in extension XC-MISC
[    20.024] (II) Initializing built-in extension SECURITY
[    20.024] (II) Initializing built-in extension XINERAMA
[    20.024] (II) Initializing built-in extension XFIXES
[    20.024] (II) Initializing built-in extension RENDER
[    20.024] (II) Initializing built-in extension RANDR
[    20.024] (II) Initializing built-in extension COMPOSITE
[    20.024] (II) Initializing built-in extension DAMAGE
[    20.026] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    20.050] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.056] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    20.056] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.056] (II) LoadModule: "evdev"
[    20.056] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.056] (II) Module evdev: vendor="X.Org Foundation"
[    20.056] 	compiled for 1.11.3, module version = 2.7.0
[    20.056] 	Module class: X.Org XInput Driver
[    20.056] 	ABI class: X.Org XInput driver, version 16.0
[    20.056] (II) Using input driver 'evdev' for 'Power Button'
[    20.056] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.056] (**) Power Button: always reports core events
[    20.056] (**) evdev: Power Button: Device: "/dev/input/event3"
[    20.056] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.056] (--) evdev: Power Button: Found keys
[    20.056] (II) evdev: Power Button: Configuring as keyboard
[    20.056] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    20.056] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.056] (**) Option "xkb_rules" "evdev"
[    20.056] (**) Option "xkb_model" "pc105"
[    20.056] (**) Option "xkb_layout" "es"
[    20.061] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    20.062] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    20.062] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.062] (II) Using input driver 'evdev' for 'Video Bus'
[    20.062] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.062] (**) Video Bus: always reports core events
[    20.062] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    20.062] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.062] (--) evdev: Video Bus: Found keys
[    20.062] (II) evdev: Video Bus: Configuring as keyboard
[    20.062] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[    20.062] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    20.062] (**) Option "xkb_rules" "evdev"
[    20.062] (**) Option "xkb_model" "pc105"
[    20.062] (**) Option "xkb_layout" "es"
[    20.063] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.063] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.063] (II) Using input driver 'evdev' for 'Power Button'
[    20.063] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.063] (**) Power Button: always reports core events
[    20.063] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.063] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.063] (--) evdev: Power Button: Found keys
[    20.063] (II) evdev: Power Button: Configuring as keyboard
[    20.063] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0C:00/input/input0/event0"
[    20.063] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    20.063] (**) Option "xkb_rules" "evdev"
[    20.063] (**) Option "xkb_model" "pc105"
[    20.063] (**) Option "xkb_layout" "es"
[    20.063] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    20.063] (II) No input driver specified, ignoring this device.
[    20.063] (II) This device may have been added with another device file.
[    20.064] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    20.064] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.064] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.064] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.064] (**) Sleep Button: always reports core events
[    20.064] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    20.064] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    20.064] (--) evdev: Sleep Button: Found keys
[    20.064] (II) evdev: Sleep Button: Configuring as keyboard
[    20.064] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0E:00/input/input2/event2"
[    20.064] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    20.064] (**) Option "xkb_rules" "evdev"
[    20.064] (**) Option "xkb_model" "pc105"
[    20.064] (**) Option "xkb_layout" "es"
[    20.065] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    20.065] (II) No input driver specified, ignoring this device.
[    20.065] (II) This device may have been added with another device file.
[    20.066] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[    20.066] (II) No input driver specified, ignoring this device.
[    20.066] (II) This device may have been added with another device file.
[    20.067] (II) config/udev: Adding input device Video WebCam (/dev/input/event5)
[    20.067] (**) Video WebCam: Applying InputClass "evdev keyboard catchall"
[    20.067] (II) Using input driver 'evdev' for 'Video WebCam'
[    20.067] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.067] (**) Video WebCam: always reports core events
[    20.067] (**) evdev: Video WebCam: Device: "/dev/input/event5"
[    20.067] (--) evdev: Video WebCam: Vendor 0x64e Product 0xa103
[    20.067] (--) evdev: Video WebCam: Found keys
[    20.067] (II) evdev: Video WebCam: Configuring as keyboard
[    20.067] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input5/event5"
[    20.067] (II) XINPUT: Adding extended input device "Video WebCam" (type: KEYBOARD, id 10)
[    20.067] (**) Option "xkb_rules" "evdev"
[    20.067] (**) Option "xkb_model" "pc105"
[    20.067] (**) Option "xkb_layout" "es"
[    20.068] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    20.068] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.068] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.068] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.068] (**) AT Translated Set 2 keyboard: always reports core events
[    20.068] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    20.068] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.068] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.068] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.068] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    20.068] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    20.068] (**) Option "xkb_rules" "evdev"
[    20.068] (**) Option "xkb_model" "pc105"
[    20.068] (**) Option "xkb_layout" "es"
[    20.130] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    20.130] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.130] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    20.130] (II) LoadModule: "synaptics"
[    20.130] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.131] (II) Module synaptics: vendor="X.Org Foundation"
[    20.131] 	compiled for 1.11.3, module version = 1.5.99
[    20.131] 	Module class: X.Org XInput Driver
[    20.131] 	ABI class: X.Org XInput driver, version 16.0
[    20.131] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    20.131] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.131] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.131] (**) Option "Device" "/dev/input/event9"
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    20.171] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    20.171] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.172] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    20.172] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    20.172] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    20.172] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    20.172] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    20.172] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    20.172] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    20.172] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    20.172] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    20.172] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    20.172] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    20.172] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    38.452] (II) XKB: reuse xkmfile /var/lib/xkb/server-718511B28EE83035776F86B5B8BD8C9A5D1FC433.xkm

---

### Post by samigina on 2012-05-08
Sigues arranancando con nomodeset activo (mientras sea así no vas a tener el driver funcionando) según tu xorg.log:

> [ 19.823] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=fa9771ea-a622-46c7-b866-af4384bd092f ro quiet splash nomodeset acpi_osi=Linux vt.handoff=7

Cuando tu equipo inicie presiona la tecla Shift, en el menu de seleccion de sistema operativo presiona "e" y edita la linea eliminando "nomodeset" luego enter y nos cuentas.

---

### Post by guillermolisi on 2012-05-08
> **samigina said:**
> Sigues arranancando con nomodeset activo (mientras sea así no vas a tener el driver funcionando) según tu xorg.log:



Cuando tu equipo inicie presiona la tecla Shift, en el menu de seleccion de sistema operativo presiona "e" y edita la linea eliminando "nomodeset" luego enter y nos cuentas.
Si eso funciona despues vemos como introducir ese cambio en forma permanente.

---

### Post by rockdrigo16 on 2012-05-08
bueno, creo que vamos avanzando :D
cuando entra al grub selecciono a ubuntu presiono e
y me da para modificar
hay una linea que dice linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=(un-monton-de-caracetres-jeje) ro quiet splash nomodeset acpi_osi="Linux" $vt_handoff
si borro a nomodeset y aprieto f10 la resolucion de la pantalla empieza bien :D ya no se ve estirado, y la puedo cambiar. Pero sigo en modo 2d, si entro a myUnity me lo dice.
si borro nomodeset acpi_osi="Linux" y aprieto f10 la pantalla arranca en negro, y trato de subirle el brillo pero nada, la tengo que reiniciar queda en negro.
y cada vez que reinicio tengo que cambiar la linea esa. no se como guardar los cambios...
Muchas gracias

---

### Post by samigina on 2012-05-08
Para hacerlo permanente:

Ejecuta en una consola:

```
gksudo gedit /etc/default/grub
```

Se te abrirá un archivo de texto, edita esta linea eliminando el "nomodeset":
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Guarda y cierra.

Ejecuta en consola:
```
sudo update-grub
```

Reinicia.

Dejemos esa parte lista y seguimos con lo de Unity 2d.

---

### Post by rockdrigo16 on 2012-05-08
no se porque no esta funcionando.
Ejecuto $ gksudo gedit /etc/default/grub
me abre una ventana del gedit 
el archivo que se abre dice asi:

 If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


/*---------------------------------------------------------------------*/

como ven ahi no dice nada de nomodeset entonces ejecuto
entonces ejecuto en consola

/*---------------------------------------------------------------------*/

$ sudo update-grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-24-generic-pae
Found kernel: /boot/vmlinuz-3.2.0-23-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-31-generic
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


/*----------------------------------------------------------------------*/



pero cuando reinicio sigo con el nomodeset puesto, arranca y no puedo cambiar la resolucion de la pantalla.
Y si aprieto la e cuando empieza, esta la linea con el nomodeset escrito :confused:
Muchas gracias de nuevo

---

### Post by rockdrigo16 on 2012-05-09
bueno andando por la web encontre esto [http://ubuntuforums.org/showthread.php?t=1840959&page=2](http://ubuntuforums.org/showthread.php?t=1840959&page=2)
no me a servido de nada :S o por lo menos no lo e podido implementaar, pero creo que es algo parecido, yo sigo con el mismo problema, gelp, jej

---

### Post by guillermolisi on 2012-05-09
Puede ser que tengas instalado Grub y Grub2 y que por eso las modificaciones que introducis en Grub2 no se reflejan porque cuando inicias la maquina utiliza Grub (la version anterior a Grub2) ?

Digo esto porque revisando en mis maquinas con Grub2 no existe un archivo /boot/grub/menu.lst. Este archivo solo existe cuando se utiliza Grub.

Podrias verificar esto ?

---

### Post by samigina on 2012-05-09
Le diste al clavo Guillermo, ese grub.list no es necesario, creo que el OP lo creó para hacer la modificación del nomodeset (siguió tutoriales algo viejos según ví).

Segun la [wiki]("https://help.ubuntu.com/community/Grub2") ese archivo podría borrarse sin problemas.

Pero verifiquemos la versión de grub que tienes instalada:

Cuando el equipo inicia y llegas al menu de selección del sistema operativo, en la parte superior nos informa que grub está usando, el mío dice:

> GNU GRUB versión 1.99-21ubuntu3

Si dice lo mismo, tienes la versión correcta y podemos borrar el archivo menu.list

> sudo rm -f /boot/grub/menu.lst

Y ejecutar de nuevo

```
sudo update-grub
```

---

### Post by rockdrigo16 on 2012-05-09
emmm si tengo esa version de grub "GNU GRUB versión 1.99-21ubuntu3"
pero el /boot/grub/menu.lst me lo creo cuando ejecuto el sudo update-grub
mira, ejecuto
> sudo rm -f /boot/grub/menu.lst
sudo update-grub
 y sale > 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) 

   
si digo que no
no pasa nada...sigue igual, si digo que si crea el archivo ese, pero tambien sigue igual 	
la salida, si pongo que si es:> 
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-24-generic-pae
Found kernel: /boot/vmlinuz-3.2.0-23-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-31-generic
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


---

### Post by samigina on 2012-05-09
Bueno, bueno... parece que tienes un caos en ese sistema... :D

Un último intento o sino reinstalamos el grub:

Elimina de nuevo el menu.lst y ejecuta:
> sudo grub-mkconfig -o /boot/grub/grub.cfg

Por confirmar que grub tienes:

> dpkg -l | grep grub

---

### Post by guillermolisi on 2012-05-09
> **samigina said:**
> Bueno, bueno... parece que tienes un caos en ese sistema... :D

Un último intento o sino reinstalamos el grub:

Elimina de nuevo el menu.lst y ejecuta:


Por confirmar que grub tienes:

Coincido con la ensalada de Grubs :)

---

### Post by rockdrigo16 on 2012-05-09
bueno les cuento lo que paso primero hice 
> $ sudo grub-mkconfig -o /boot/grub/grub.cfg

Generating grub.cfg ...
Found background image: .background_cache.jpeg
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

y 

> $ dpkg -l | grep grub

ii  grub                                   0.97-29ubuntu66                         GRand Unified Bootloader (Legacy version)
ii  grub-common                            1.99-21ubuntu3                          GRand Unified Bootloader (common files)
rc  grub-pc                                1.99-21ubuntu3                          GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                            1.99-21ubuntu3                          GRand Unified Bootloader, version 2 (PC/BIOS binaries)


entonces reinicie pero la pantalla estaba en negro y no se arreglava con nada, volvi a reiniciar, entre con nomodeset y entonces ejecute

> gksudo gedit /etc/default/grub
 
y la linea que dice > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
la cambie por>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

hice 
> sudo update-grub
y repeti los dos primeros pasos y ya puedo cambiar la resolución de la pantalla, ya no se ve estirado :D
lo que sigo en el modo 2d :(
muchas gracias!!!!

---

### Post by samigina on 2012-05-10
OK, tenemos el equipo iniciando correctamente :D , ahora nos queda el asunto de la aceleración 3d... 

En teoría el driver debería estar cargando, probemos de nuevo el comando

> glxinfo | grep render

---

### Post by rockdrigo16 on 2012-05-10
ok, muchas gracias devuelta.
sigo en 2d.
te dejo la salida 
>  $ glxinfo | grep render

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

---

### Post by samigina on 2012-05-10
No esta detectando correctamente tu gráfica, reconfiguremos el servidor grafico.

Si tienes un archivo xorg.conf, borrálo, eso era necesario hace un tiempo, pero ya no se usa, luego:

sudo dpkg-reconfigure xserver-xorg

Y reinicia.

---

### Post by rockdrigo16 on 2012-05-10
lo hice pero no funciono.
sigo en modo 2d :/

---

### Post by samigina on 2012-05-11
Vamos más profundo entonces:

```
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rockdrigo16 on 2012-05-22
bueno gente, les agradezco mucho y perdon la demora en responder.
es que cambie de compu y termine formatenado la otra, en la nueva no tuve problema y la vieja lo arregle fácil. Siguiendo pasos que me dijeron ustedes. Se ve que fue algún problema de la actualización de ubuntu 10 a 12 aca. Y cuando lo instale desde 0 no paso, les dejo lo que hice pa solucionarlo

Ejecuta en una consola:

```
gksudo gedit /etc/default/grub
```
Se te abrirá un archivo de texto, editar la linea que dice
[HTML]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/HTML]
por 
[HTML][PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset cpi_osi="Linux"" [/PHP][/HTML]
Guarda y cierra.

Ejecuta en consola:
```
sudo update-grub
```
Reinicia.

y pronto quedo todo funcionado! muchas gracias :D

---

