---
title: "lucid - tc electronic konnekt 6 via expresscard - issues"
date: 2010-05-13
forum: Ubuntu Studio
---

### Post by matthus on 2010-05-13
I'm aware that the konnekt 6 is not officially supported yet, it is reported to work though.
Here is what I have done today and the outcome

svn checkout [http://subversion.ffado.rg/ffado/trunk/lib/libffado](http://subversion.ffado.rg/ffado/trunk/lib/libffado) ffaso-svn
then sudo svn update in the downloaded directory

ubuntu studio controlla enabled memlock = 50
raw1394 access enabled
enabled nice -10
in advanced under users and groups -user privalleges - audio devices and video devices enabeled
jack audio connection kit 
driver - firwewire
interface - hw:0
audio - duplex
input channels - default
output channels default
priority - 70
frames/period - 128
sample rate - 44100
port mXIMUM - 256
timout - 500MS
start delay - 2 seconds
server  path jackd
realtime - ticked

> Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.[QUOTE]23:49:56.743 Patchbay deactivated.
23:49:56.792 Statistics reset.
23:49:56.858 ALSA connection graph change.
23:49:57.300 ALSA connection change.
23:53:14.987 Startup script...
23:53:14.988 artsshell -q terminate
sh: artsshell: not found
23:53:15.392 Startup script terminated with exit status=32512.
23:53:15.392 JACK is starting...
23:53:15.393 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
23:53:15.422 JACK was started with PID=2148.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2320836
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
00651188785: [31mError (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
[0m00651661650: [31mError (avc_avdevice.cpp)[  88] probe: Subunit info command failed
[0mfirewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
23:53:17.216 JACK was stopped successfully.
23:53:17.217 Post-shutdown script...
23:53:17.217 killall jackd
jackd: no process found
23:53:17.652 Post-shutdown script terminated with exit status=256.
23:53:18.490 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/QUOTE]

I beg for mercy and er guidance?

---

### Post by matthus on 2010-05-13
ok dumb me didn't do the installation part now uninstalled old ffado done the scon thing get

> dangorously@Fire-fly:~/ffado/ffaso-svn$ sudo scons
scons: Reading SConscript files ...

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/dangorously/ffado/ffaso-svn/SConstruct", line 38, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/dangorously/ffado/ffaso-svn/SConstruct", line 43, in <module>

scons: warning: The PathOption() function is deprecated; use the PathVariable() function instead.
File "/home/dangorously/ffado/ffaso-svn/SConstruct", line 45, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/home/dangorously/ffado/ffaso-svn/SConstruct", line 73, in <module>
Checking for a working C-compiler yes
Checking for a working C++-compiler yes
Checking for pkg-config (at least version 0.0.0)... yes
Checking for C header file expat.h... no
Checking for XML_ExpatVersion() in C library expat... no
Checking for libraw1394 (1.3.0 or higher)... 	no
Checking for libxml++-2.6 (2.13.0 or higher)... 	no
Checking for libiec61883 (1.1.0 or higher)... 	no

(At least) One of the dependencies is missing. I can't go on without it, please
install the needed packages for each of the lines saying "no".
(Remember to also install the *-devel packages!)

And remember to remove the cache with "rm -Rf .sconsign.dblite cache" so the
results above get rechecked.


with the exception of XML_Expatversion() which I am unaware of what it is or how to know if I have it I have the other supposed missing dependancies

jack gives me

> jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2320836
jackd: unknown driver 'firewire'
00:53:58.415 JACK was stopped with exit status=1.
00:53:58.415 Post-shutdown script...
00:53:58.416 killall jackd
jackd: no process found
00:53:58.824 Post-shutdown script terminated with exit status=256.
00:54:00.478 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by matthus on 2010-05-13
after some twiddling, uninstalling and reinstalling I now get this from jack 

> jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2320836
01:21:28.036 JACK was started with PID=2013.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
00237715861: [31mError (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
[0m00238190544: [31mError (avc_avdevice.cpp)[  88] probe: Subunit info command failed
[0mfirewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
01:21:29.814 JACK was stopped successfully.
01:21:29.815 Post-shutdown script...
01:21:29.815 killall jackd
jackd: no process found
01:21:30.225 Post-shutdown script terminated with exit status=256.
01:21:31.281 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info

---

### Post by matthus on 2010-05-15
er bump???

---

### Post by matthus on 2010-05-29
Am still no closer on this and am resorting to trying to sell it to buy an echo audio iox, any helpers?

---

### Post by MIJ-VI on 2010-07-14
Hi matthus.

Your notebook's express card slot controller chip and/or your FireWire express card's chip may not be suitable for digital audio.

With the FireWire express card plugged into your notebook, could you please run [FONT=Courier New]sudo lshw [/FONT]in Terminal and post the complete output here?

Doing so will allow us to see exactly which hardware components your notebook is comprised of.

Thank you.

--------

BTW. Someome else is having the same problem.

[ubuntu_studio] Firewire Expresscard
[http://ubuntuforums.org/showthread.php?t=1403731](http://ubuntuforums.org/showthread.php?t=1403731)

---

### Post by matthus on 2010-07-15
I can't do this right now as not at home, I shall in the next couple of weeks though, thankyou :0)

---

### Post by matthus on 2010-08-27
maternally                
    description: Computer
    product: M7X0SUN
    vendor: clevo
    version: Rev. A1
    serial: 12345678901234567
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0090F590-B9E6-0000-0000-000000000000
  *-core
       description: Motherboard
       product: M7X0SUN
       vendor: clevo
       physical id: 0
       version: Bottom
       serial: SI96A-55
       slot: Bottom
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00 (05/04/2009)
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: uPGA 479M
          size: 1200MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 2MiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM2
             size: 2GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:9000(size=4096) memory:d0000000-d2ffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98M [GeForce G 105M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff(prefetchable) memory:d0000000-d1ffffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1080(size=16)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:d3404000-d3404fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:d3405000-d3405fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:d3406000-d3406fff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:90:f5:90:b9:e6
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
             resources: irq:19 memory:d3407000-d340707f ioport:1000(size=128)
        *-storage
             description: SATA controller
             product: AHCI IDE Controller (0106)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:17 ioport:10c8(size=8) ioport:10bc(size=4) ioport:10c0(size=8) ioport:10b8(size=4) ioport:10a0(size=16) memory:d3407400-d34075ff
           *-disk
                description: ATA Disk
                product: FUJITSU MJA2500B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K92PT9829UYA
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000dc011
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ab0e34ce-8103-480a-9a83-c3af9245e5d8
                   size: 457GiB
                   capacity: 457GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-08-16 18:06:45 filesystem=ext4 lastmountpoint=/&#65533;O&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;?&#65533;&#65533;&#65533;&#65533;&#65533;h &#65533;&#65533;h/&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]k modified=2010-08-23 01:09:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-08-27 12:36:09 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 8852MiB
                   capacity: 8852MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8852MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: BD ROM BC-5500S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.06
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=8192) memory:dc000000-dfffffff memory:d3200000-d33fffff(prefetchable)
           *-pci
                description: PCI bridge
                product: XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress bus_master cap_list
                resources: memory:dc000000-dc0fffff
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
                   vendor: Texas Instruments
                   physical id: 0
                   bus info: pci@0000:0a:00.0
                   version: 01
                   width: 32 bits
                   clock: 66MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                   resources: irq:16 memory:dc004000-dc0047ff memory:dc000000-dc003fff
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:d3100000-d31fffff memory:d3500000-d36fffff(prefetchable)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:d3100000-d31000ff memory:d3500000-d350ffff(prefetchable)
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d3100400-d31004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:d3100800-d31008ff
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:d3400000-d3403fff
     *-scsi
          physical id: 2
          bus info: usb@1:8
          logical name: scsi6
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@6:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /media/O2 USB Modem
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /media/O2 USB Modem
                capabilities: partitioned partitioned:mac
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 17KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   vendor: Mac OS X
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000001000
                   size: 31MiB
                   capacity: 31MiB
                   capabilities: hfsplus initialized
                   configuration: checked=1904-01-01 00:00:00 created=2009-06-10 15:09:19 filesystem=hfsplus lastmountedby=10.0 modified=2009-06-10 16:09:19 state=clean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@7:0.0.0
             logical name: /dev/sdb
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 1
       capabilities: inbound
matterchism@Maternally:/dev$

---

### Post by MIJ-VI on 2010-08-27
> **matthus said:**
> I'm aware that the konnekt 6 is not officially supported yet, it is reported to work though.
Here is what I have done today and the outcome

svn checkout [http://subversion.ffado.rg/ffado/trunk/lib/libffado](http://subversion.ffado.rg/ffado/trunk/lib/libffado) ffaso-svn
then sudo svn update in the downloaded directory

ubuntu studio controlla enabled memlock = 50
raw1394 access enabled
enabled nice -10
in advanced under users and groups -user privalleges - audio devices and video devices enabeled
jack audio connection kit 
driver - firwewire
interface - hw:0
audio - duplex
input channels - default
output channels default
priority - 70
frames/period - 128
sample rate - 44100
port mXIMUM - 256
timout - 500MS
start delay - 2 seconds
server  path jackd
realtime - ticked



I beg for mercy and er guidance?

Hi matthus.

Instead of trying to get an unsupported device to work with your Clevo M7X0SUN, why not take your notebook to a store and try a few FireWire audio interfaces? The Roland/Edirol FA-66 and the FA-101 are both supported by FFAD.

You could then sell the tc konnekt 6 to a Windows or Mac user.

Recording music > than fiddling with incompatible hardware.

---

### Post by AutoStatic on 2010-08-27
Hello matthus,

If you're using 10.04: [https://launchpad.net/~autostatic/+archive/ffado/+packages](https://launchpad.net/~autostatic/+archive/ffado/+packages)

It's a package of a recent checkout of the svn branch of FFADO and your device should work with it. All you need to do is download the libffado2 package and double-click the downloaded package. After installing it you should be able to set up JACK and get the Konnekt 6 running.

---

### Post by MIJ-VI on 2010-08-27
[IMG]http://www.talkbass.com/forum/images/smilies/colors/smile.gif[/IMG] ^

---

### Post by matthus on 2010-08-27
cool thankyou will try that, it may be my firewire expresscard, the mystery continues :0)

---

### Post by MIJ-VI on 2010-08-27
> **matthus said:**
> cool thankyou will try that, it may be my firewire expresscard, the mystery continues :0)

From what I can make your your lappy's lshw results your FW express card is using a Texas Instruments chipset (T.I. is the #1 chip choice for FireWire audio), but the express card slot is using a controller made by JMicron Technology Corp (generally these are regarded as being less desirable for FW audio use). However, I read somewhere a while ago that JMicron's newer chips are better for FireWire audio.

If AutoStatic's rescue gets your tc interface working please let us know.

---

### Post by AutoStatic on 2010-08-28
My notebook has a JMicron FireWire controller which works with FFADO and my soundcard. Don't know about the cardslot.

---

### Post by matthus on 2010-08-28
Well I have definitly made progress, thank you I had almost given up.
I wiped jack and ffado completly and started again with ffado then jack from the deb's you linked me to, then installed ffado and then jack
now from ffado-dbus-server and I get ------
[PHP]00090001905:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
00090050697: Debug (devicemanager.cpp)[ 358] discover: Starting discovery...
00090147367: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00090147444: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00090147477: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00090147490: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00090147510: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00090147520: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00090147649: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00090147672: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00090147690: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00090147701: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00090147715: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00090147728: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00090147829: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00090147842: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00090147857: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00090147866: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00090147883: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00090147892: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00090147986: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00090148035: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00090148072: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00090148085: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00090148103: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00090148111: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00090148211: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00090148225: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00090148244: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00090148253: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00090148270: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00090148279: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00090148577: Debug (devicemanager.cpp)[ 620] discover: driver found for device 0
00090148661: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00090148680: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00090148690: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00090148704: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00090148713: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00090148729: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00090177508: Error (dice_avdevice.cpp)[1718] readReg: Could not read from node 0xFFC0 addr 0xFFFFE0200000
00090177555: Error (dice_eap.cpp)[ 113] init: Device does not support EAP
00090177574: Warning (dice_avdevice.cpp)[ 171] discover: Could not init EAP
00090177696: Debug (devicemanager.cpp)[ 657] discover: discovery of node 0 on port 0 done...
00090177714: Debug (devicemanager.cpp)[ 665] discover: Discovery finished...
00090177742: Debug (devicemanager.cpp)[1252] showDeviceInfo: ===== Device Manager =====
00090177754: Debug (Element.cpp)[ 121] show: Element DeviceManager
00090177767: Debug (devicemanager.cpp)[1260] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00090177817: Debug (devicemanager.cpp)[1270] showDeviceInfo: --- Device  0 ---
00090177828: Debug (dice_avdevice.cpp)[ 623] showDevice: Device is a DICE device
00090177845: Debug (ffadodevice.cpp)[ 214] showDevice: Attached to port.......: 0 (ohci1394)
00090177853: Debug (ffadodevice.cpp)[ 215] showDevice: Node...................: 0
00090177869: Debug (ffadodevice.cpp)[ 217] showDevice: Vendor name............: TC Electronic
00090177878: Debug (ffadodevice.cpp)[ 219] showDevice: Model name.............: DesktopKonnekt6
00090177901: Debug (ffadodevice.cpp)[ 221] showDevice: GUID...................: 0001660409002053
00090177923: Debug (ffadodevice.cpp)[ 226] showDevice: Assigned ID....: 0001660409002053
00090177950:  (dice_avdevice.cpp)[ 626] showDevice:  DICE Parameter Space info:
00090177961:  (dice_avdevice.cpp)[ 627] showDevice:   Global  : offset=0x0028 size=0360
00090177974:  (dice_avdevice.cpp)[ 628] showDevice:   TX      : offset=0x0190 size=0568
00090177982:  (dice_avdevice.cpp)[ 629] showDevice:                 nb=   1 size=0280
00090177993:  (dice_avdevice.cpp)[ 630] showDevice:   RX      : offset=0x03C8 size=1128
00090178000:  (dice_avdevice.cpp)[ 631] showDevice:                 nb=   1 size=0280
00090178017:  (dice_avdevice.cpp)[ 632] showDevice:   UNUSED1 : offset=0x0830 size=0016
00090178024:  (dice_avdevice.cpp)[ 633] showDevice:   UNUSED2 : offset=0x0000 size=0000
00090178039:  (dice_avdevice.cpp)[ 635] showDevice:  Global param space:
00090179301:  (dice_avdevice.cpp)[ 638] showDevice:   Owner            : 0x00000000FFFF0000
00090180638:  (dice_avdevice.cpp)[ 641] showDevice:   Notification     : 0x00000000
00090183507:  (dice_avdevice.cpp)[ 644] showDevice:   Nick name        : DesktopKonnekt6
00090184874:  (dice_avdevice.cpp)[ 648] showDevice:   Clock Select     : 0x02 0x0C
00090186169:  (dice_avdevice.cpp)[ 652] showDevice:   Enable           : false
00090187431:  (dice_avdevice.cpp)[ 656] showDevice:   Clock Status     : locked 0x01
00090188743:  (dice_avdevice.cpp)[ 659] showDevice:   Extended Status  : 0x00000000
00090190055:  (dice_avdevice.cpp)[ 662] showDevice:   Samplerate       : 0x0000AC44 (44100)
00090191308:  (dice_avdevice.cpp)[ 665] showDevice:   Version          : 0x01000400
00090192616:  (dice_avdevice.cpp)[ 674] showDevice:   Version          : 0x01000400 (1.0.4.0)
00090194063:  (dice_avdevice.cpp)[ 677] showDevice:   Clock caps       : 0x1300007E
00090195652:  (dice_avdevice.cpp)[ 680] showDevice:   Clock sources    :
00090195681:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195697:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195704:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195714:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195721:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195741:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195748:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195763:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195770:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195787:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195794:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195806:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00090195812:  (dice_avdevice.cpp)[ 686] showDevice:     INTERNAL
00090195822:  (dice_avdevice.cpp)[ 689] showDevice:  TX param space:
00090195828:  (dice_avdevice.cpp)[ 690] showDevice:   Nb of xmit        : 1
00090195846:  (dice_avdevice.cpp)[ 692] showDevice:   Transmitter 0:
00090197123:  (dice_avdevice.cpp)[ 695] showDevice:    ISO channel       :  -1
00090198443:  (dice_avdevice.cpp)[ 697] showDevice:    ISO speed         :   2
00090199730:  (dice_avdevice.cpp)[ 700] showDevice:    Nb audio channels :   6
00090201032:  (dice_avdevice.cpp)[ 702] showDevice:    Nb midi channels  :   0
00090202308:  (dice_avdevice.cpp)[ 705] showDevice:    AC3 caps          : 0x00000000
00090203672:  (dice_avdevice.cpp)[ 707] showDevice:    AC3 enable        : 0x00000000
00090205220:  (dice_avdevice.cpp)[ 710] showDevice:    Channel names     :
00090205253:  (dice_avdevice.cpp)[ 715] showDevice:      ch 1
00090205261:  (dice_avdevice.cpp)[ 715] showDevice:      ch 2
00090205272:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00090205279:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00090205289:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00090205295:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00090205308:  (dice_avdevice.cpp)[ 719] showDevice:  RX param space:
00090205321:  (dice_avdevice.cpp)[ 720] showDevice:   Nb of recv        : 1
00090205343:  (dice_avdevice.cpp)[ 722] showDevice:   Receiver 0:
00090206480:  (dice_avdevice.cpp)[ 725] showDevice:    ISO channel       :  -1
00090207773:  (dice_avdevice.cpp)[ 727] showDevice:    Sequence start    :   0
00090209066:  (dice_avdevice.cpp)[ 730] showDevice:    Nb audio channels :   6
00090210362:  (dice_avdevice.cpp)[ 732] showDevice:    Nb midi channels  :   0
00090211657:  (dice_avdevice.cpp)[ 735] showDevice:    AC3 caps          : 0x00000000
00090212942:  (dice_avdevice.cpp)[ 737] showDevice:    AC3 enable        : 0x00000000
00090214562:  (dice_avdevice.cpp)[ 740] showDevice:    Channel names     :
00090214583:  (dice_avdevice.cpp)[ 745] showDevice:      main out 1
00090214591:  (dice_avdevice.cpp)[ 745] showDevice:      main out 2
00090214602:  (dice_avdevice.cpp)[ 745] showDevice:      phones out 1
00090214609:  (dice_avdevice.cpp)[ 745] showDevice:      phones out 2
00090214623:  (dice_avdevice.cpp)[ 745] showDevice:       - 
00090214630:  (dice_avdevice.cpp)[ 745] showDevice:       - 
00090214673: Debug (devicemanager.cpp)[1273] showDeviceInfo: Clock sync sources:
00090220110: Debug (devicemanager.cpp)[1282] showDeviceInfo:  Type: Compound Syt Match, Id:  8, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00090220147: Debug (devicemanager.cpp)[1282] showDeviceInfo:  Type: Compound Syt Match, Id:  9, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00090220157: Debug (devicemanager.cpp)[1282] showDeviceInfo:  Type: Internal          , Id: 12, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: INTERNAL
00090231144:  (ffado-dbus-server.cpp)[ 328] main: DBUS service running
00090231195:  (ffado-dbus-server.cpp)[ 329] main: press ctrl-c to stop it & exit
00090231226: Debug (ffado-dbus-server.cpp)[ 332] main: dispatching...
[/PHP]
Although the ffado mixer will not load from the program menu and has no icon as it did before.
Also from jackd I get the following message when trying to initialise
[PHP]12:48:45.647 JACK was stopped with exit status=255.
12:48:45.648 Post-shutdown script...
12:48:45.648 killall jackd
jackd: no process found
12:48:46.057 Post-shutdown script terminated with exit status=256.
12:48:54.776 Startup script...
12:48:54.777 artsshell -q terminate
sh: artsshell: not found
12:48:55.179 Startup script terminated with exit status=32512.
12:48:55.179 JACK is starting...
12:48:55.180 /usr/bin/jackd -r -dfreebob -dhw:0 -r44100 -p128 -n4 -D
12:48:55.182 JACK was started with PID=1872.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2320836
no message buffer overruns
jackd: unknown driver 'freebob'
12:48:55.326 JACK was stopped with exit status=1.
12:48:55.327 Post-shutdown script...
12:48:55.327 killall jackd
jackd: no process found
12:48:55.736 Post-shutdown script terminated with exit status=256.
12:48:57.246 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
[/PHP]
Any advice on getting the ffado mixer going would be appreciated, and also on jack settings and any other thing you may feel is relevent.
And once again thanks for helping me progress this far :0)

---

### Post by AutoStatic on 2010-08-28
The mixer in my package doesn't work as stated on my FFADO PPA page.
And you should use the 'firewire' driver in QjackCtl or -dfirewire on the command line, not 'freebob' or -dfreebob.
And I have no JACK packages in my PPA, which version did you install now?

---

### Post by matthus on 2010-08-28
cool thanks, will try than and report back :0) is on a non net partition so has been a bit fiddly going back and forth

---

### Post by MIJ-VI on 2010-08-28
> **AutoStatic said:**
> My notebook has a JMicron FireWire controller which works with FFADO and my soundcard. Don't know about the cardslot.

4 pin or 6 pin? Could you please post the identity of this JMicron FireWire controller?

What's the make and model number of your notebook and sound card?

A few members of TalkBass are trying to multi-track record audio onto HP notebooks with JMicron FireWire controllers.

---

### Post by AutoStatic on 2010-08-28
Hello MIJ-VI,

4-pin on a HP DV7-1070ed.

**lspci | grep 1394**:
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller

Soundcard is a Focusrite Saffire Pro 10 IO.

---

### Post by matthus on 2010-08-28
I finally got some noise out of it however its quite unstable.
In windows it was easily interfered with by networking devices and usb.
I only seemed to get it working when I had unplugged my usb midi interface and in renoise it seemed to run quite smoothly, however the jack tool had said it had stopped even though renoise was still going with jack as its audio host. Also this does not allow for audio/midi routing in the patching part, I am going to try to run it from the terminal instead without the manager tool to see if that makes any difference. also I am going to try and cut off and uninstall any internet/modem based drivers. Do you have any advice on unessential backround things and how to turn them off like someone would in windows, my only real priority is audio for that partition. Thanks

---

### Post by AutoStatic on 2010-08-28
[http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

---

### Post by MIJ-VI on 2010-08-28
> **AutoStatic said:**
> Hello MIJ-VI,

4-pin on a HP DV7-1070ed.

**lspci | grep 1394**:
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller

Soundcard is a Focusrite Saffire Pro 10 IO.

Hi AutoStatic.

Well, well, well! [IMG]http://www.talkbass.com/forum/images/smilies/colors/smile.gif[/IMG] This is the *first* time I've heard of an HP 4-pin FW port working for audio! I'll relay this info to [TalkBass]("http://www.talkbass.com/forum/showthread.php?t=599271").

[Manuals for HP Pavilion dv7-1070ed Entertainment Notebook PC]("http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&product=3773703&")

Hmm... It seems that [Focusrite no longer offers the Saffire Pro 10 I/O]("http://www.focusrite.com/products/audio_interfaces/"). However...

[Saffire Pro 10 I/O product support page]("http://www.focusrite.com/support/saffire/saffire_pro_10_io").

[FFADO page showing Focusrite Saffire Pro 10 I/O: Full Support]("http://www.ffado.org/?q=devicesupport/list&page=1")

One more question if I may: does the Wi-Fi on your HP DV7-1070ed work out-of-the-box under Ubuntu Studio?

Thank you.

---

### Post by AutoStatic on 2010-08-29
> **MIJ-VI said:**
> One more question if I may: does the Wi-Fi on your HP DV7-1070ed work out-of-the-box under Ubuntu Studio?No, it's a Broadcom WiFi controller so it only works with the STA restricted driver. And I don't use NetworkManager, only wpa-supplicant otherwise I loose connection all the time.

Concerning FireWire and soundcards, the cause of why it probably doesn't work normally:```
cat /proc/interrupts | grep 1394
 16:        141      36475   IO-APIC-fasteoi   uhci_hcd:usb3, ohci1394, mmc0, eth1, jmb38x_ms:slot0, nvidia
```
So this IRQ probably holds the world-record of most crowded IRQ. An USB port, a cardreader, a networkdevice, the controller for the cardreader and the graphics card! All on one IRQ, no wonder it will never work. That's where rtirq comes in handy. And you need to disable eth1 (WiFi) and make sure you're not using the cardbus and the USB port. Only then it works. And no Compiz of course ;)

---

### Post by MIJ-VI on 2010-08-29
> **AutoStatic said:**
> No, it's a Broadcom WiFi controller so it only works with the STA restricted driver. And I don't use NetworkManager, only wpa-supplicant otherwise I loose connection all the time.

Concerning FireWire and soundcards, the cause of why it probably doesn't work normally:```
cat /proc/interrupts | grep 1394
 16:        141      36475   IO-APIC-fasteoi   uhci_hcd:usb3, ohci1394, mmc0, eth1, jmb38x_ms:slot0, nvidia
```So this IRQ probably holds the world-record of most crowded IRQ. An USB port, a cardreader, a networkdevice, the controller for the cardreader and the graphics card! All on one IRQ, no wonder it will never work. That's where rtirq comes in handy. And you need to disable eth1 (WiFi) and make sure you're not using the cardbus and the USB port. Only then it works. And no Compiz of course ;)

My Acer Aspire 5517-1536 (which doesn't have a FireWire port or an Express Card slot) uses a Broadcom (4312) Wi-Fi card via the STA driver as well. Fortunately it works with Network Manager.

I don't yet fully understand what IRQs are but I found a couple of threads, the links to which I'll post here in case anyone else is as bewildered about this subject as I am:

[Interrupt request]("http://en.wikipedia.org/wiki/Interrupt_request")

[manually change irqs]("http://ubuntuforums.org/showthread.php?t=474908")

[[ubuntu_studio] Yet another tweak for firewire audio - IRQ priorities]("http://ubuntuforums.org/showthread.php?t=1328175")

I suspect an intermittent IRQ conflict may be what's causing my 5517-1536's frequent inability to record audio via its on-board SBx00 Azalia (Intel HDA) audio unless a USB Wi-Fi adaptor is plugged in at boot time. (I've tried a USB hard drive and an additional USB mouse instead but nope, the audio recording ability only consistently works if a USB Wi-Fi adaptor is used.)

However, I've recently installed Canonical's new [FONT=Courier New]canonical-census[/FONT] package and since then my notebook's audio recording ability seems to work as it should without having to use a USB Wi-Fi adaptor. Weird.

I tried to find out which devices are using which IRQs on my notebook by typing...

 ```
cat /proc/interrupts | grep usb
 16:     135403   IO-APIC-fasteoi   ohci_hcd:usb2, ohci_hcd:usb3, eth1, HDA Intel
 17:          2   IO-APIC-fasteoi   ehci_hcd:usb1
```...but I don't understand the results so I'll have to learn more about auditing hardware in a more succinct manner than this:

```
john@john:~$ sudo lshw
john                      
    description: Notebook
    product: Aspire 5517
    vendor: Acer
    version: V1.09
    serial: LXPGZ020320034805B1601
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=66626132-3538-3735-6466-705AB62286B6
  *-core
       description: Motherboard
       product: Aspire 5517
       vendor: Acer
       physical id: 0
       version: V1.09
       serial: LXPGZ020320034805B1601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.09 (11/30/2009)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor TF-20
          vendor: Advanced Micro Devices [AMD]
          physical id: 20
          bus info: cpu@0
          version: AMD Athlon(tm) Processor TF-20
          serial: NotSupport
          slot: Socket S1G1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal write-through unified
        *-cache:1
             description: L1 cache
             physical id: 22
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: HYMP112S64CP6-S6
             vendor: Unknown
             physical id: 0
             serial: AD000000000000000109534F82712C
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: HYMP112S64CP6-S6
             vendor: Unknown
             physical id: 1
             serial: AD000000000000000109534F62712D
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR2 [empty]
             physical id: 2
             slot: DIMM2
        *-bank:3
             description: DIMM DDR2 [empty]
             physical id: 3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:7000(size=4096) memory:92100000-922fffff ioport:80000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:80000000-8fffffff(prefetchable) ioport:7000(size=256) memory:92200000-9220ffff memory:92100000-921fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=16384) memory:91100000-920fffff ioport:90000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: c4:17:fe:67:f3:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.180 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:91100000-91103fff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:91000000-910fffff
           *-network
                description: Ethernet interface
                product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: c0
                serial: 70:5a:b6:22:86:b6
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:91000000-9103ffff ioport:2000(size=128)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:27 ioport:8038(size=8) ioport:804c(size=4) ioport:8030(size=8) ioport:8048(size=4) ioport:8010(size=16) memory:92306000-923063ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXA0AB9W4750
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a4bb357c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 550a5d8e-6a16-4081-b999-ea59a64899d8
                   size: 131GiB
                   capacity: 131GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-15 09:26:17 filesystem=ext4 lastmountpoint=/8}zZ&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(}zZ&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;@e&#65533;i&#65533;&#65533;&#65533;L'm&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[&#65533;i&#65533; modified=2010-08-29 07:21:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-08-29 17:28:46 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 101GiB
                   capacity: 101GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 97GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4259MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7700S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.B0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:92305000-92305fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:92304000-92304fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:92306400-923064ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:92300000-92303fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:1000(size=4096)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
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
john@john:~$
```

---

### Post by matthus on 2010-08-30
After wiping my gnome due to being inattentive with the synaptic package manager and apt-get-install not working on the command line as I wanted it to I reinstalled ubuntustudio and started again, its working fine now although it ceases when I plug my usb midi interface in, having a hardware synth with no keyboard that maybe an issue although ~I'll leave that for another thread, thank you so much for your guidance and things :0)

---

### Post by AutoStatic on 2010-08-30
So it works? Great! Could you post the outcome of **cat /proc/interrupts** so we could try tackling the USB issue?

---

### Post by AutoStatic on 2010-08-30
> **MIJ-VI said:**
> ```
cat /proc/interrupts | grep usb
 16:     135403   IO-APIC-fasteoi   ohci_hcd:usb2, ohci_hcd:usb3, eth1, HDA Intel
```eth1 is probably your WiFi device and it shares an IRQ with your soundcard. So if you want to record with your soundcard try doing a **sudo ifdown eth1** first, followed by a **sudo modprobe -r wl** if necessary.

---

### Post by RaumTrug on 2010-08-30
a bit on a sidetrain, don't know if it's proper to post right here, but maybe relevant for audio stuff and this problem:

a common problem in realtime device driving is interrupt sharing. an interrupt means roughly: a device sends some signal to the interrupt controller, and this triggers the cpu to execute a software-handler to deal with the device that just triggered it. now I imagine the problem to be something like this (for example, I just made this up, I have no real detail knowledge about this): a wifi-chip sits on the same irq as a soundchip (-chain if usb or firewire). the wifi triggers the interrupt, and the kernel somehow knows which handler it is (from the same irq) for the wifi or audio, and executes its (the wifi's) handler. now the wifi-chip-irq-handler does some lengthy stuff, copying buffers to- and fro or whatever. during that time the audio card raises the same irq, but the kernel thinks "ah, that irq-number's handler is already on, and will handle itself if I put the request on a qeue!". so the audio-chip will not get proper handling in time, as stuff is blocked by wifi. anyone know how it really works? am I right or wrong?

my sollution was 'till now, having a mobo with a bios enabling me to choose an irq-number for almost every device I needed, to set the relevant devices irq's on different numbers, and also obey the "irq-priorities" for the hardware interrupt numbers given in the mobo's manual to put the soundcard to something "more important" than, for example, the gfx-board or the network card - worked fine for me, eleminating lots of probs I had before :)

...but, I still can't choose irq for different usb busses and other stuff, I can just try to evade conflicts the other way round, and try blindly which plugport is the one sitting on a lone irq......

however, I've heard of some phantom named "userspace interrupt handlers" (could be named different, but I can't remember), enabling the user to choose interrupt-numbers for _all_ devices manually right after boot-time via some kernel-config. iirc had something to do with "local apic", and is "hard to configure" ;). but maybe it's just software wrapping of hardware irq's, and would be no use to evade conflicts...?

anyone here know more about this? if it works like I imagine (optimistically) it could solve lots of hw-priority issues & such, expecially for audio/video real-time performance, and for people with poor interrupt configuration by hardware/bios & no means to circumvent them. if it's no legend, I'd really like to know about! thx for your pointers, links & such...

greets, T.F.

---

### Post by MIJ-VI on 2010-08-30
> **AutoStatic said:**
> eth1 is probably your WiFi device and it shares an IRQ with your soundcard. So if you want to record with your soundcard try doing a **sudo ifdown eth1** first, followed by a **sudo modprobe -r wl** if necessary.

Thanks AutoStatic. I've copied your post for future reference in case the audio recording issue on my 5517-1536 crops up again.

However my notebook's audio recording ability has been functioning as it should ever since installing [FONT="Courier New"]canonical-census[/FONT].., which, come to think of it, I did shortly after updating to Ubuntu 10.04.1 via Update Manager. Hmmm...

Anyway, the next 5517-1536 issue to tackle is its refusal to boot any *nix OS which has a real time or a preemptive kernel. I suspect that my notebook's optical drive may be a culprit in this. If I make any headway in resolving the issue I'll start a new thread.

Thanks again.

---

### Post by AutoStatic on 2010-08-31
canonical-census really has nothing to do with realtime audio or IRQ's. It must've been the update or something else.

---

