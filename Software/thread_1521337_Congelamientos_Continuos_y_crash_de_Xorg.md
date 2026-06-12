---
title: "Congelamientos Continuos y crash de Xorg"
date: 2010-06-30
forum: Software
---

### Post by NickCis on 2010-06-30
Bueno, recientemente instale ubuntu en una pc (probe ubuntu 10.04). Cuando lo instalaba se me congelaba la pc (no podia mover mouse, no reaccionaba el teclado nada, no me cambiaban ni las luces de los caps, estas quedaban como estaban antes del lock, pero si qeria sacar el num lock, al tocar la tecla, la lucecita seguia prendida) y siempre me hacia volver a arrancar la isntalacion. Tonces instale por modo alternate. La instalacion fue un exito. 
Pero al entrar al sistema los errores volvieron. Se seguia congelando de manera aleatoria despues de un tiempo de que este prendida la pc. Hasta a veces logeaba en el gdm y envez de entrar al usuario, me empezaba a aparecer el escritorio, tiraba pantalla negra y volvia al gdm.

Probe con le live cd de ubuntu 9.10. Mismo error, despues de un tiempo x de uso, se freezeaba la pc.

Alguna ayuda?.
Saludos y muchas gracias.

P.D.:
Mientras la maquina responde, anda todo, hasta el sonido, pero despues se congela. Ahora la estoy probando con el live cd de 9.04, por ahora anda, no se por cuanto tiempo.
Posteo la devolucion de mas comando (lspci y lsmod).
Devolucion de comando sudo lshw (copiado en el poco tiempo qe la pc estaba viva):
  
```

ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: M825VXX
    vendor: ECS
    version: 3.1
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: M825VXX
       vendor: ECS
       physical id: 0
       version: 3.1
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.0
          slot: Socket-A
          size: 1667MHz
          capacity: 3GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 479MiB
     *-pci
          description: Host bridge
          product: VT8375 [KM266/KL266] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: VT8375 [ProSavage8 KM266/KL266]
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: latency=32 maxlatency=255 mingnt=4
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                capabilities: audio
                configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-disk
                description: ATA Disk
                product: WDC WD400LB-00DN
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 77.0
                serial: WD-WCAH81017533
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c7f4903a
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 5ec078b2-e0a9-7546-90fd-fb65881d318a
                   size: 10150MiB
                   capacity: 10150MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-06-02 10:32:37 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: 8d8ce071-b3ea-47d3-9c0d-a6c743881d6a
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-06-29 21:29:14 filesystem=ext4 lastmountpoint=/(-&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;y&#1856;\9&#1812;~&#65533;&#65533;&#65533;g &#65533;-]/&#65533;&#65533;~&#65533;&#65533;&#65533;!&#65533;0&#65533;f&#65533;0&#65533;f&#1856;&#65533;&#65533;&#65533;~&#65533;&#1328;~&#65533;&#1293;j modified=2010-06-30 20:35:53 mounted=2010-06-30 21:00:01 state=clean
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 07284b58-6951-472a-9de2-a7ac551afb59
                   size: 1066MiB
                   capacity: 1066MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0a:e6:a4:1c:9b
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.8.16.2 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:e9:cd:24:76:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$

```

Lspci:
```

ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ubuntu@ubuntu:~$ 

```
lsmod:
```

ubuntu@ubuntu:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
savage                 39168  2 
drm                    96296  3 savage
lp                     17156  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
snd_via82xx            32152  3 
gameport               19340  1 snd_via82xx
snd_ac97_codec        112292  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15104  1 snd_via82xx
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
i2c_viapro             15892  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
via_ircc               32660  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  197180  1 via_ircc
psmouse                61972  0 
snd                    62628  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13316  0 
pcspkr                 10496  0 
ppdev                  15620  0 
crc_ccitt              10112  1 irda
soundcore              15200  1 snd
via_agp                16256  1 
agpgart                42696  2 drm,via_agp
shpchp                 40212  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
nls_cp437              13696  1 
isofs                  39844  1 
via_rhine              30856  0 
mii                    13312  1 via_rhine
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache
ubuntu@ubuntu:~$ 

```

---

### Post by NickCis on 2010-06-30
Instale ubuntu 9.04, en el live cd todo bien, la instalacion grafica tmb...
Lo termine de instalar, le puse el ppa de emesene, (ni llegue a actualizar los paquetes), y vuelves los congelamientos...

En algunos las luces de los locks se quedan titilando,, en otros, solo se cuelgan como estaban antes.

Alguna idea?


Edit: Los locks que titilan son el caps lock y el scrioll lock...

---

### Post by guillermolisi on 2010-07-01
para saber si es algun problema con el Xorg, nada mejor que ver su log en /var/log/Xorg.0.log

---

### Post by NickCis on 2010-07-01
/var/log/Xorg.0.log

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux oficina-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  2 00:08:06 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) S3 Inc. VT8375 [ProSavage8 KM266/KL266] rev 0, Mem @ 0xdfe80000/524288, 0xd0000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched savage from file name savage.ids
(==) Matched savage for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) SAVAGE: driver (version 2.2.1) for S3 Savage chipsets: Savage4,
	Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
	Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
	Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
	SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
	SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
	SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) SAVAGE(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(==) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(--) SAVAGE(0): Chip: id 8d04, "ProSavage DDR-K"
(--) SAVAGE(0): Engine: "ProSavageDDR"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using BusType PCI by default
(==) SAVAGE(0): Using PCI DMA
(==) SAVAGE(0): Will try command and vertex DMA mode
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  32768k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:E-EDID segment register" registered at address 0x60.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(--) SAVAGE(0): Detected current MCLK value of 14.318 MHz
(--) SAVAGE(0): 4096x1395 TFT LCD panel detected but not active
(--) SAVAGE(0): Found 13 modes at this depth:
    [10e] 320 x 200, 70Hz
    [133] 320 x 240, 72Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [11d] 640 x 400, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz, 160Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz
    [117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 100Hz, 130Hz
    [17a] 1280 x 768, 60Hz
    [14f] 1280 x 960, 60Hz, 85Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 100Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [122] 1600 x 1200, 60Hz
(II) SAVAGE(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) SAVAGE(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) SAVAGE(0): Unable to estimate virtual size
(II) SAVAGE(0): Clock range:  10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(II) SAVAGE(0): Not using default mode "640x400" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(II) SAVAGE(0): Not using default mode "320x200" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 75Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): Chose mode 14f at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (hsync out of range)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 14f at 85Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (hsync out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 85Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1792x1344 60Hz.
(II) SAVAGE(0): Not using default mode "1792x1344" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1856x1392 60Hz.
(II) SAVAGE(0): Not using default mode "1856x1392" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1440 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1440" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 59Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 60Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 70Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 70Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 74Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 74Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 84Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 85Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 99Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 100Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1360x768 59Hz.
(II) SAVAGE(0): Not using default mode "1360x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1360x768 59Hz.
(II) SAVAGE(0): Not using default mode "1360x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 60Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1440x900 59Hz.
(II) SAVAGE(0): Not using default mode "1440x900" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 59Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1600x1024 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1024" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 59Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 69Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 69Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 74Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 74Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 84Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 85Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1080 59Hz.
(II) SAVAGE(0): Not using default mode "1920x1080" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x540 59Hz.
(II) SAVAGE(0): Not using default mode "960x540" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 59Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 59Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Virtual size is 800x600 (pitch 800)
(**) SAVAGE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SAVAGE(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(II) SAVAGE(0): 3096 kB of Videoram needed for 3D; 32768 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmGetBusid returned ''
(II) [drm] loaded kernel module for "savage" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SAVAGE(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SAVAGE(0): [drm] framebuffer handle = 0xd0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [drm] installed DRM signal handler
(II) SAVAGE(0): [drm] aperture handle = 0xd2000000
(II) SAVAGE(0): [drm] PCI command DMA handle = 0x1c800000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x1c914000
(II) SAVAGE(0): [drm] Status page mapped at 0xb8079000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): virtualX:800,virtualY:600
(II) SAVAGE(0): bpp:16,tiledwidthBytes:1664,tiledBufferSize:1011712 
(II) SAVAGE(0): bpp:16,widthBytes:1664,BufferSize:999424 
(II) SAVAGE(0): videoRambytes:0x02000000 
(II) SAVAGE(0): textureSize:0x01afd000 
(II) SAVAGE(0): textureSize:0x01afd000 
(II) SAVAGE(0): textureOffset:0x004e2000 
(II) SAVAGE(0): depthOffset:0x003eb000,depthPitch:1664
(II) SAVAGE(0): backOffset:0x002f4000,backPitch:1664
(II) SAVAGE(0): Reserved back buffer at offset 0x2f4000
(II) SAVAGE(0): Reserved depth buffer at offset 0x3eb000
(II) SAVAGE(0): Reserved 27636 kb for textures at offset 0x4e2000
(II) SAVAGE(0): Using 1259 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Image Writes
	Setting up tile and stipple cache:
		30 128x128 slots
		6 256x256 slots
(==) SAVAGE(0): Backing store disabled
(II) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]	reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]	reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]	chipset:0x00000000
(II) SAVAGE(0): [junkers]	sgram:0x00000000
(II) SAVAGE(0): [junkers]	frontbufferSize:0x000f4000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	frontPitch:0x00000680
(II) SAVAGE(0): [junkers]	backbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]	backOffset:0x002f4000
(II) SAVAGE(0): [junkers]	backPitch:0x00000680
(II) SAVAGE(0): [junkers]	depthbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]	depthOffset:0x003eb000
(II) SAVAGE(0): [junkers]	depthPitch:0x00000680
(II) SAVAGE(0): [junkers]	textureOffset:0x004e2000
(II) SAVAGE(0): [junkers]	textureSize:0x01afd000
(II) SAVAGE(0): [junkers]	textureSize:0x01afd000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	agp:handle:0x00000000
(II) SAVAGE(0): [junkers]	agp:offset:0x00000000
(II) SAVAGE(0): [junkers]	agp:size:0x00000000
(II) SAVAGE(0): [junkers]	agp:map:0x00000000
(II) SAVAGE(0): [junkers]	registers:handle:0xdfe80000
(II) SAVAGE(0): [junkers]	registers:offset:0x00000000
(II) SAVAGE(0): [junkers]	registers:size:0x00080000
(II) SAVAGE(0): [junkers]	registers:map:0x00000000
(II) SAVAGE(0): [junkers]	status:handle:0x1c914000
(II) SAVAGE(0): [junkers]	status:offset:0x00000000
(II) SAVAGE(0): [junkers]	status:size:0x00001000
(II) SAVAGE(0): [junkers]	status:map:0xb8079000
(II) SAVAGE(0): [junkers]	agpTextures:handle:0x00000000
(II) SAVAGE(0): [junkers]	agpTextures:offset:0x00000000
(II) SAVAGE(0): [junkers]	agpTextures:size:0x00000000
(II) SAVAGE(0): [junkers]	apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:handle:0x1c800000
(II) SAVAGE(0): [junkers]	cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]	cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]	chipset:0x00000006
(II) SAVAGE(0): [junkers]	width:0x00000320
(II) SAVAGE(0): [junkers]	height:0x00000258
(II) SAVAGE(0): [junkers]	mem:0x02000000
(II) SAVAGE(0): [junkers]	cpp:2
(II) SAVAGE(0): [junkers]	zpp:2
(II) SAVAGE(0): [junkers]	agpMode:0
(II) SAVAGE(0): [junkers]	bufferSize:65536
(II) SAVAGE(0): [junkers]	frontbufferSize:0x000f4000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	backbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]	backOffset:0x002f4000
(II) SAVAGE(0): [junkers]	depthbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]	depthOffset:0x003eb000
(II) SAVAGE(0): [junkers]	textureOffset:0x004e2000
(II) SAVAGE(0): [junkers]	textureSize:0x01a00000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000015
(II) SAVAGE(0): [junkers]	agpTextureHandle:0x00000000
(II) SAVAGE(0): [junkers]	agpTextureSize:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000020
(II) SAVAGE(0): [junkers]	apertureHandle:0xd2000000
(II) SAVAGE(0): [junkers]	apertureSize:0x05000000
(II) SAVAGE(0): [junkers]	aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]	statusHandle:0x1c914000
(II) SAVAGE(0): [junkers]	statusSize:0x00001000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) AT Translated Set 2 keyboard: xkb_layout: "es"
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0

```

---

### Post by NickCis on 2010-07-02
Alguna idea de en que logs me puedo fijar?,,
Estoy re perdido, y el problema es demaciado general para usar google =S...

Ahora los freezes, son sin el parpadeo de las lucecitas. La computadora cuelga y no responde a nada, ni al alt + print pant + b =S...

Muchas Gracias.

---

### Post by alfplayer on 2010-07-02
Con Google se puede buscar si funciona ese chip de video con linux.

---

### Post by guillermolisi on 2010-07-03
El problema no pasa por el X-server ni por la placa de video. El inicio del X-server, salvo dos o tres detalles menores, es correcto.

---

### Post by NickCis on 2010-07-03
Okey, tonces el problema con la placa descartado.
Como podria averiguar que esta causando los cuelgues?.
Vi que hay mas logs, pero no se cual mirar y que debo mirar de ellos.. =S...

Muchas gracias.

---

### Post by guillermolisi on 2010-07-04
/var/log/dmesg y /var/log/messages, por lo pronto.

---

### Post by NickCis on 2010-07-04
Posteo los logs.
Adjunto "var/log/messages" (lo adjunto comprimido ya que era muy pesado como para postearlo), tmb estaba messages.0 
Solo adjunte messages.

Para el "/var/log/dmesg", encontre qe tmb estaban dmesg.0, dmesg.1.gz, dmesg.2.gz, dmesg.4.gz.
Yo posteo solo /var/log/dmesg:
```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  modified: 000000001dff0000 - 000000001dff8000 (ACPI data)
[    0.000000]  modified: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1dff0000 @ 10000-16000
[    0.000000] RAMDISK: 1d8ac000 - 1dfdf72d
[    0.000000] ACPI: RSDP 000FA760, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1DFF0000, 0028 (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 1DFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 1DFF0120, 2E11 (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1DFF8000, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dff0000
[    0.000000]   low ram: 00000000 - 1dff0000
[    0.000000]   bootmap 00012000 - 00015c00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [001d8ac000 - 001dfdf72d]          RAMDISK ==> [001d8ac000 - 001dfdf72d]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dff0
[    0.000000]   HighMem  0x0001dff0 -> 0x0001dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001dff0
[    0.000000] On node 0 totalpages: 122751
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 928 pages used for memmap
[    0.000000]   Normal zone: 117840 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121791
[    0.000000] Kernel command line: root=UUID=975fd774-f007-416f-8c58-a772c350276c ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1666.390 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2456960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 469020k/491456k available (4126k kernel code, 21788k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xde7f0000 - 0xff3fe000   ( 524 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3332.78 BogoMIPS (lpj=6665560)
[    0.004053] Security Framework initialized
[    0.004067] SELinux:  Disabled at boot.
[    0.004113] AppArmor: AppArmor initialized
[    0.004128] Mount-cache hash table entries: 512
[    0.004366] Initializing cgroup subsys ns
[    0.004373] Initializing cgroup subsys cpuacct
[    0.004376] Initializing cgroup subsys memory
[    0.004383] Initializing cgroup subsys freezer
[    0.004403] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004407] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004432] Checking 'hlt' instruction... OK.
[    0.020642] SMP alternatives: switching to UP code
[    0.204217] Freeing SMP alternatives: 18k freed
[    0.204226] ACPI: Core revision 20080926
[    0.206961] ACPI: Checking initramfs for custom DSDT
[    0.558381] ACPI: setting ELCR to 0200 (from 0820)
[    0.558822] weird, boot CPU (#0) not listedby the BIOS.
[    0.558825] SMP motherboard not detected.
[    0.558830] Local APIC not detected. Using dummy APIC emulation.
[    0.558833] SMP disabled
[    0.559345] Brought up 1 CPUs
[    0.559349] Total of 1 processors activated (3332.78 BogoMIPS).
[    0.559375] CPU0 attaching NULL sched-domain.
[    0.559965] net_namespace: 776 bytes
[    0.559983] Booting paravirtualized kernel on bare hardware
[    0.560366] Time: 21:43:12  Date: 07/04/10
[    0.560375] regulator: core version 0.5
[    0.560451] NET: Registered protocol family 16
[    0.560668] EISA bus registered
[    0.560697] ACPI: bus type pci registered
[    0.565489] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[    0.565493] PCI: Using configuration type 1 for base access
[    0.567312] ACPI: EC: Look up EC in DSDT
[    0.574471] ACPI: Interpreter enabled
[    0.574478] ACPI: (supports S0 S1 S4 S5)
[    0.574501] ACPI: Using PIC for interrupt routing
[    0.580271] ACPI: No dock devices found.
[    0.580286] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.580371] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.580444] pci 0000:00:01.0: supports D1
[    0.580504] pci 0000:00:10.0: reg 20 io port: [0xe400-0xe41f]
[    0.580521] pci 0000:00:10.0: supports D1 D2
[    0.580524] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.580530] pci 0000:00:10.0: PME# disabled
[    0.580575] pci 0000:00:10.1: reg 20 io port: [0xe800-0xe81f]
[    0.580592] pci 0000:00:10.1: supports D1 D2
[    0.580595] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.580599] pci 0000:00:10.1: PME# disabled
[    0.580644] pci 0000:00:10.2: reg 20 io port: [0xec00-0xec1f]
[    0.580661] pci 0000:00:10.2: supports D1 D2
[    0.580663] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.580668] pci 0000:00:10.2: PME# disabled
[    0.580700] pci 0000:00:10.3: reg 10 32bit mmio: [0xdfffff00-0xdfffffff]
[    0.580732] pci 0000:00:10.3: supports D1 D2
[    0.580734] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.580739] pci 0000:00:10.3: PME# disabled
[    0.580800] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.580811] pci 0000:00:11.0: quirk: region 0800-087f claimed by vt8235 PM
[    0.580816] pci 0000:00:11.0: quirk: region 0400-040f claimed by vt8235 SMB
[    0.580869] pci 0000:00:11.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.580923] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.580958] pci 0000:00:11.5: supports D1 D2
[    0.580990] pci 0000:00:12.0: reg 10 io port: [0xdc00-0xdcff]
[    0.580997] pci 0000:00:12.0: reg 14 32bit mmio: [0xdffffe00-0xdffffeff]
[    0.581027] pci 0000:00:12.0: supports D1 D2
[    0.581029] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.581034] pci 0000:00:12.0: PME# disabled
[    0.581086] pci 0000:01:00.0: reg 10 32bit mmio: [0xdfe80000-0xdfefffff]
[    0.581093] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.581112] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfe70000-0xdfe7ffff]
[    0.581120] pci 0000:01:00.0: supports D1 D2
[    0.581157] pci 0000:00:01.0: bridge 32bit mmio: [0xdfd00000-0xdfefffff]
[    0.581162] pci 0000:00:01.0: bridge 32bit mmio pref: [0xcfc00000-0xdfbfffff]
[    0.581170] bus 00 -> node 0
[    0.581179] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.583177] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.583345] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.583507] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.583669] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.583778] ACPI: Power Resource [URP1] (off)
[    0.583825] ACPI: Power Resource [URP2] (off)
[    0.583877] ACPI: Power Resource [FDDP] (off)
[    0.583924] ACPI: Power Resource [LPTP] (off)
[    0.584045] ACPI: WMI: Mapper loaded
[    0.584420] SCSI subsystem initialized
[    0.584503] libata version 3.00 loaded.
[    0.584590] usbcore: registered new interface driver usbfs
[    0.584617] usbcore: registered new interface driver hub
[    0.584664] usbcore: registered new device driver usb
[    0.584855] PCI: Using ACPI for IRQ routing
[    0.584976] Bluetooth: Core ver 2.13
[    0.584976] NET: Registered protocol family 31
[    0.584976] Bluetooth: HCI device and connection manager initialized
[    0.584976] Bluetooth: HCI socket layer initialized
[    0.584976] NET: Registered protocol family 8
[    0.584976] NET: Registered protocol family 20
[    0.584976] NetLabel: Initializing
[    0.584976] NetLabel:  domain hash size = 128
[    0.584976] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.584976] NetLabel:  unlabeled traffic allowed by default
[    0.584976] AppArmor: AppArmor Filesystem Enabled
[    0.584976] pnp: PnP ACPI init
[    0.584976] ACPI: bus type pnp registered
[    0.590195] pnp: PnP ACPI: found 12 devices
[    0.590198] ACPI: ACPI bus type pnp unregistered
[    0.590205] PnPBIOS: Disabled by ACPI PNP
[    0.625023] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.625027] pci 0000:00:01.0:   IO window: disabled
[    0.625033] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    0.625038] pci 0000:00:01.0:   PREFETCH window: 0x000000cfc00000-0x000000dfbfffff
[    0.625057] pci 0000:00:01.0: setting latency timer to 64
[    0.625063] bus: 00 index 0 io port: [0x00-0xffff]
[    0.625066] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.625068] bus: 01 index 0 mmio: [0x0-0x0]
[    0.625071] bus: 01 index 1 mmio: [0xdfd00000-0xdfefffff]
[    0.625074] bus: 01 index 2 mmio: [0xcfc00000-0xdfbfffff]
[    0.625076] bus: 01 index 3 mmio: [0x0-0x0]
[    0.625094] NET: Registered protocol family 2
[    0.625275] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.625659] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.625986] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.626316] TCP: Hash tables configured (established 16384 bind 16384)
[    0.626320] TCP reno registered
[    0.626515] NET: Registered protocol family 1
[    0.626748] checking if image is initramfs... it is
[    1.128202] Switched to high resolution mode on CPU 0
[    1.419021] Freeing initrd memory: 7373k freed
[    1.419193] cpufreq: No nForce2 chipset.
[    1.419456] audit: initializing netlink socket (disabled)
[    1.419495] type=2000 audit(1278279792.416:1): initialized
[    1.429010] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.430750] VFS: Disk quotas dquot_6.5.1
[    1.430828] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.431681] fuse init (API version 7.10)
[    1.431791] msgmni has been set to 930
[    1.432174] alg: No test for stdrng (krng)
[    1.432193] io scheduler noop registered
[    1.432196] io scheduler anticipatory registered
[    1.432199] io scheduler deadline registered
[    1.432220] io scheduler cfq registered (default)
[    1.432245] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.432342] pci 0000:01:00.0: Boot video device
[    1.436878] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.436891] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.437095] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.437099] ACPI: Power Button (FF) [PWRF]
[    1.437156] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.437160] ACPI: Power Button (CM) [PWRB]
[    1.437231] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.437240] ACPI: Sleep Button (CM) [SLPB]
[    1.437434] processor ACPI_CPU:00: registered as cooling_device0
[    1.437439] ACPI: Processor [CPU1] (supports 16 throttling states)
[    1.440184] isapnp: Scanning for PnP cards...
[    1.794056] isapnp: No Plug & Play device found
[    1.795965] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.796137] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.796545] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.797688] brd: module loaded
[    1.798151] loop: module loaded
[    1.798282] Fixed MDIO Bus: probed
[    1.798291] PPP generic driver version 2.4.2
[    1.798387] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.798446] Driver 'sd' needs updating - please use bus_type methods
[    1.798459] Driver 'sr' needs updating - please use bus_type methods
[    1.799144] pata_via 0000:00:11.1: version 0.3.3
[    1.799172] pata_via 0000:00:11.1: can't derive routing for PCI INT A
[    1.799530] scsi0 : pata_via
[    1.799718] scsi1 : pata_via
[    1.802276] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.802280] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.956617] ata1.00: ATAPI: 50X CD-ROM, VER 5.3A, max UDMA/33
[    1.964295] ata1.00: configured for UDMA/33
[    2.129393] ata2.00: ATA-6: WDC WD400LB-00DNA0, 77.07W77, max UDMA/100
[    2.129397] ata2.00: 78165360 sectors, multi 16: LBA48 
[    2.129422] ata2.00: limited to UDMA/33 due to 40-wire cable
[    2.145264] ata2.00: configured for UDMA/33
[    2.145662] scsi 0:0:0:0: CD-ROM                     50X CD-ROM       5.3A PQ: 0 ANSI: 5
[    2.148215] sr0: scsi3-mmc drive: 1x/40x cd/rw xa/form2 cdda tray
[    2.148220] Uniform CD-ROM driver Revision: 3.20
[    2.148418] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.148519] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.148632] scsi 1:0:0:0: Direct-Access     ATA      WDC WD400LB-00DN 77.0 PQ: 0 ANSI: 5
[    2.148778] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.148804] sd 1:0:0:0: [sda] Write Protect is off
[    2.148807] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.148846] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.148934] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.148956] sd 1:0:0:0: [sda] Write Protect is off
[    2.148959] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.148995] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.149002]  sda: sda1 sda2 sda3
[    2.206199] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.206260] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.206497] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.206867] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    2.206872] PCI: setting IRQ 11 as level-triggered
[    2.206880] ehci_hcd 0000:00:10.3: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.206928] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    2.207037] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    2.207118] ehci_hcd 0000:00:10.3: irq 11, io mem 0xdfffff00
[    2.216065] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    2.216171] usb usb1: configuration #1 chosen from 1 choice
[    2.216222] hub 1-0:1.0: USB hub found
[    2.216245] hub 1-0:1.0: 6 ports detected
[    2.216397] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.216424] uhci_hcd: USB Universal Host Controller Interface driver
[    2.216789] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    2.216794] PCI: setting IRQ 5 as level-triggered
[    2.216801] uhci_hcd 0000:00:10.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    2.216813] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.216889] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.216919] uhci_hcd 0000:00:10.0: irq 5, io base 0x0000e400
[    2.217031] usb usb2: configuration #1 chosen from 1 choice
[    2.217065] hub 2-0:1.0: USB hub found
[    2.217086] hub 2-0:1.0: 2 ports detected
[    2.217424] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    2.217429] uhci_hcd 0000:00:10.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    2.217437] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.217498] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.217519] uhci_hcd 0000:00:10.1: irq 5, io base 0x0000e800
[    2.217632] usb usb3: configuration #1 chosen from 1 choice
[    2.217673] hub 3-0:1.0: USB hub found
[    2.217691] hub 3-0:1.0: 2 ports detected
[    2.218008] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    2.218013] uhci_hcd 0000:00:10.2: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    2.218021] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.218082] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.218103] uhci_hcd 0000:00:10.2: irq 5, io base 0x0000ec00
[    2.218233] usb usb4: configuration #1 chosen from 1 choice
[    2.218263] hub 4-0:1.0: USB hub found
[    2.218280] hub 4-0:1.0: 2 ports detected
[    2.218448] usbcore: registered new interface driver libusual
[    2.218513] usbcore: registered new interface driver usbserial
[    2.218529] USB Serial support registered for generic
[    2.218546] usbcore: registered new interface driver usbserial_generic
[    2.218550] usbserial: USB Serial Driver core
[    2.218618] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.218984] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.219001] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.219203] mice: PS/2 mouse device common for all mice
[    2.219436] rtc_cmos 00:02: RTC can wake from S4
[    2.219502] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.219535] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.219668] device-mapper: uevent: version 1.0.3
[    2.219856] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.219946] device-mapper: multipath: version 1.0.5 loaded
[    2.219950] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.220151] EISA: Probing bus 0 at eisa.0
[    2.220195] EISA: Detected 0 cards.
[    2.220247] cpuidle: using governor ladder
[    2.220250] cpuidle: using governor menu
[    2.220950] TCP cubic registered
[    2.221075] NET: Registered protocol family 10
[    2.221614] lo: Disabled Privacy Extensions
[    2.222031] NET: Registered protocol family 17
[    2.222058] Bluetooth: L2CAP ver 2.11
[    2.222061] Bluetooth: L2CAP socket layer initialized
[    2.222065] Bluetooth: SCO (Voice Link) ver 0.6
[    2.222067] Bluetooth: SCO socket layer initialized
[    2.222115] Bluetooth: RFCOMM socket layer initialized
[    2.222132] Bluetooth: RFCOMM TTY layer initialized
[    2.222135] Bluetooth: RFCOMM ver 1.10
[    2.222164] powernow-k8: Processor cpuid 680 not supported
[    2.222199] IO APIC resources could be not be allocated.
[    2.222260] Using IPI No-Shortcut mode
[    2.222424] registered taskstats version 1
[    2.222550]   Magic number: 2:219:752
[    2.222600] tty ttyS3: hash matches
[    2.222742] rtc_cmos 00:02: setting system clock to 2010-07-04 21:43:14 UTC (1278279794)
[    2.222746] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.222749] EDD information not available.
[    2.224111] Freeing unused kernel memory: 532k freed
[    2.224276] Write protecting the kernel text: 4128k
[    2.224326] Write protecting the kernel read-only data: 1532k
[    2.255158] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.744302] Floppy drive(s): fd0 is 1.44M
[    2.766447] FDC 0 is a post-1991 82077
[    2.920000] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.920152] via-rhine 0000:00:12.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    2.925183] eth0: VIA Rhine II at 0xdffffe00, 00:0a:e6:a4:1c:9b, IRQ 5.
[    2.925894] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link cde1.
[    3.612348] PM: Starting manual resume from disk
[    3.612356] PM: Resume from partition 8:3
[    3.612358] PM: Checking hibernation image.
[    3.612734] PM: Resume from disk failed.
[    3.646384] EXT4-fs: barriers enabled
[    3.666744] kjournald2 starting.  Commit interval 5 seconds
[    3.666767] EXT4-fs: delayed allocation enabled
[    3.666769] EXT4-fs: file extents enabled
[    3.671898] EXT4-fs: mballoc enabled
[    3.671907] EXT4-fs: mounted filesystem with ordered data mode.
[    8.987727] udev: starting version 141
[    9.150677] Linux agpgart interface v0.103
[    9.193685] agpgart: Detected VIA PM266/KM266 chipset
[    9.199450] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    9.231035] parport_pc 00:09: reported by Plug and Play ACPI
[    9.231139] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.242503] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.401214] irda_init()
[    9.401250] NET: Registered protocol family 23
[    9.625047] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.706678] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.123659] psmouse serio1: ID: 10 00 64<6>ppdev: user-space parallel port driver
[   10.541206] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   10.541355] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   10.599137] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   11.250132] lp0: using parport0 (interrupt-driven).
[   11.402979] Adding 1092412k swap on /dev/sda3.  Priority:-1 extents:1 across:1092412k
[   11.985704] EXT4 FS on sda2, internal journal on sda2:8
[   13.327217] type=1505 audit(1278290605.601:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1822
[   13.414092] type=1505 audit(1278290605.689:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1826
[   13.414537] type=1505 audit(1278290605.689:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1826
[   13.414657] type=1505 audit(1278290605.689:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1826
[   13.414770] type=1505 audit(1278290605.689:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1826
[   13.660441] type=1505 audit(1278290605.937:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1831
[   13.660999] type=1505 audit(1278290605.937:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1831
[   13.715125] type=1505 audit(1278290605.989:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1835
[   16.206347] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.206356] Bluetooth: BNEP filters: protocol multicast
[   16.236538] Bridge firewalling registered

```
[LIST]
[/LIST]
Muchas gracias :P

---

### Post by guillermolisi on 2010-07-05
Confirmando una de las sospechas, esa maquina tiene algun problema con APIC y su BIOS.

Los mensajes mas significativos para mi son:

> [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.558830] Local APIC not detected. Using dummy APIC emulation.
[    0.558833] SMP disabled
[    0.583778] ACPI: Power Resource [URP1] (off)
[    0.583825] ACPI: Power Resource [URP2] (off)
[    0.583877] ACPI: Power Resource [FDDP] (off)
[    0.583924] ACPI: Power Resource [LPTP] (off)

Probaria de agregar acpi=lapic en la linea de boot del kernel en Grub para ver que efecto tiene.

El procesador de esa maquina tiene un solo nucleo ?

---

### Post by NickCis on 2010-07-06
Ahora cuando pueda pruebo lo que me dijiste de editar la entrada del grub.
Si, es una maquina de un solo nucleo =P.
Habia posteado la devolucion del comando "lshw" en mi primer post, por si se nececita mas información de la pc =P.

Saludos y muchas gracias.

---

### Post by guillermolisi on 2010-07-06
Ok. Preguntaba por la linea que deshabilita la funcionalidad SMP que se usa cuando el procesador tiene mas de un nucleo (o Hyperthreading).

---

