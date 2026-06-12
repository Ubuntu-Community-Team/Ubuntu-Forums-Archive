---
title: "Ultra2 workstation - Feisty 7.04 install from CDROM - Cannot find hard disc driver"
date: 2007-04-19
forum: Sun Sparc Users
---

### Post by sandpiper on 2007-04-19
Hi  Thought  I would do a fresh install of Feisty on my old Sparc Ultra 2 workstation . Historically have  successfully installed Dapper (server mode) on the same machine (with help from Marc). Downloaded iso image checked Checksum and booted disc from CD ROM . Everything was fine except when I got to the unexpected message cannot find hard drive. I selected the esp driver from the list of drivers (I checked the original dmesg listing for Dapper)  but still Feisty is not finding my scsi hardrive. What should I do?  Chris

---

### Post by erm67 on 2007-04-21
I installed xubunt one week ago on a ultra2 from cd without any problem. Maybe switch console and post the error messages you evntually find there (alt-ctrl-f4 I think)


I remember, I had an additional sbus esp scsi controller installed, and it could not find the drives, I removed it from the ultra2 and then it worked. Did not investigate the problem further however.

---

### Post by sandpiper on 2007-04-21
> **erm67 said:**
> 

I remember, I had an additional sbus esp scsi controller installed, and it could not find the drives, I removed it from the ultra2 and then it worked. Did not investigate the problem further however.

Hey, Thanks for the hint. Yes my Ultra 2 (which is a workstation - not a server) does have 2 additional SCSI controllers (supporting both wide and narrow SCSI external devices - tape drives, external harddisc array for for programmes) in addition to the staright otherboard one).   I will remove it and see if it allows me to progress and advise back...

Incidently this level of hardware profile was one of my reasons for perservering with Ubuntu and seeing if I can get the desktop running rather than just the server instance.  I have been struggling with Dapper to get it running in graphics mode with a TGX+ card. (From what I have learnt from this forum - I am a newbie to Linux , I may have a fundamental problem in that the Ultra 2 workstation does not have a PCI bus - only SBUS and Ubuntu cannot cope with this. Myself I have no idea whether this is fact or not ..) I thought I would try Feisty as one last attempt so as to get more error information on this non performing TGX+ card and diagnose the problem -   Thank for your help  Chris

---

### Post by sandpiper on 2007-04-23
Yep your suggestion worked!. I removed the 2 addtional SBUS based SCSI cards and got past the error message and now have Feisty running on the Ultra 2 workstation albeit in server mode  only.  Thanks for your help [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

I have now the challenge to get the Ubuntu desktop up and running  if I can .  I have since run fbset --info and have found the same issue with the device node as I had with Dapper. The SBUS graphics card is still seen at address 000000 in graphics mode when it is being addressed ok in console mode.. Real puzzle. I will try and see if hwinfo package can give me more info.  Thanks again Chris

---

### Post by erm67 on 2007-04-24
I have a Creator 3D and it works quite well, the annoyance rigth now is that hald crashes. Anyway xubuntu and xfce are more than adequate for the speed of a ultra2 :-)
I have 1280Mb ram and I can even run openoffice faster than on solaris 9. The only other problem is that dri and opengl accelleration is not enabled, but it was slow anyway.
The creator 3d and Elite3d sbus can be easily found on ebay for a few bucks if you have an older card maybe think about upgrading it.
I read that there are patches for the X server to compile and use the dri for the creator and it should work out of the box for the elite.

---

### Post by sandpiper on 2007-04-26
> **erm67 said:**
> I have a Creator 3D and it works quite well, the annoyance rigth now is that hald crashes. Anyway xubuntu and xfce are more than adequate for the speed of a ultra2 :-)
I have 1280Mb ram and I can even run openoffice faster than on solaris 9. The only other problem is that dri and opengl accelleration is not enabled, but it was slow anyway.
The creator 3d and Elite3d sbus can be easily found on ebay for a few bucks if you have an older card maybe think about upgrading it.
I read that there are patches for the X server to compile and use the dri for the creator and it should work out of the box for the elite.

Yes. Your comments about performance reinforces my determination to get the Ultra 2 workstation working with Ubuntu. I am contemplating sourcing a creative or Elite card because I "thought" these cards were "not" SBUS based  and plugged into the UPA socket of the Ultra 2 workstation. I thought the reason the TGX+ card doesn't work is because it "is" SBUS based".  While I gather from other contributors to this forum that the Creative card and elite cards "do" work I remain keen to establish "why" the TGX+ card doesn't work... Of course the diffculty I have is I am very new to Linux and hence am struggling so this approach is probably  not a wise use of my spare time. If you or someone can help me progress the diagnosis it would really be appreciated. Chris

---

### Post by erm67 on 2007-04-26
> **sandpiper said:**
>  I thought the reason the TGX+ card doesn't work is because it "is" SBUS based".  While I gather from other contributors to this forum that the Creative card and elite cards "do" work I remain keen to establish "why" the TGX+ card doesn't work... 

can you post your xorg.conf
and lsmod

---

### Post by sandpiper on 2007-04-27
> **erm67 said:**
> can you post your xorg.conf
and lsmod

Thanks!!   I will try and do better than that...The following is long so bear with me...! The first dump is from the utility fbset--info:  plus the output from the hwinfo utility that is long so I have cut some lines..  

The reason I haven't included the Xorg  dump is because historically I have spent many months modifying and checking the entries with no progress. The fault sympthms are simply a black screen with a flashing cursor when attempting to go to graphics mode from text mode

 It was not until i did some reading around the framebuffer operation for linux and looked at the cg6 source (this appears to be default driver that is used in console mode) that I discovered that the common link to all framebuffer drivers is the "device node". ie  When ever a framebuffer driver (in graphics mode" wishes to access any graphics hardware card it uses the device node (or so I think!)   defined at linux kernel installation time to gain access to hardware registers for drawing the text or lines.  

Based on this understanding (whcih could be wrong!) I have pursed any utlity that would simulate this dataflow process .. Hence the reason why I have looked at the utlity fbset.. You will see that the address for the framebuffer is 00000. This cannot be right? unless of course this is some kind of offset address. 

What puzzles me is if you now look at the hwinfo dump you will see in the kernel log the frame buffer "is" being accessed ok in console mode so how come the graphics mode doesn't work. I have proven this failure by attempting to install Ubuntu with the command option "framebuffer on" at install time. (I have found that the default for the server install is "framebuffer" off" ). I simply get a black screen again and very early in the install process plus frozen keyboard.  Cannot do anything aprt from hitting the stop A sequence....

Can you or someone guide me please! to get greater clarity on the problem The obvious question is where is the kernel getting the address  0000 from when fbset asks for info on the graphics card. Surely if I make this correct my problem is solved?  I notice there are some SBUS erros in the hwinfo dump - not sure if this is a clue to the problem?  Any time/help/comments grate fully received. I am very much a newbie to linux and the way the kernel works ... Chris

 
Output from Fbset.....

mode "1152x900"
    geometry 1152 900 1152 900 8
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/0,8/0,8/0,0/0
endmode

Frame buffer device information:
    Name        : TGX+ sparc
    Address     : 0
    Size        : 0
    Type        : PACKED PIXELS
    Visual      : PSEUDOCOLOR
    XPanStep    : 0
    YPanStep    : 0
    YWrapStep   : 0
    LineLength  : 1152
    Accelerator : Sun cg6

The following dump is from the utiltiy hwinfo: as below  it is long....so I deleted stuff where i thought it not relevant...


============ start debug info ============
libhd version 13.11u (sparc)
using /var/lib/hardware
kernel version is 2.6
----- /proc/cmdline -----
  root=/dev/disk/by-uuid/45c63fea-47a2-4f1e-8c8c-d330206b0984 ro quiet splash
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x0000138fc4a8107ff9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip +isa +isa.isdn +isdn +kbd +prom +sbus +int -braille -braille.alva -braille.fhp -braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod -braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports=1 -bios.ddc.ports=2 -bios.ddc.ports=3 -bios.ddc.ports=4 -modules.pata -max -lxrc)
shm: attached segment 32768 at 0xf7bcc000
>> hal.1: read hal data
  hal: dbus_bus_get: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
>> floppy.1: get nvram
>> floppy.2: klog info
>> sys.1: cpu
>> misc.9: kernel log
----- kernel log -----
  <4>[    0.000000] ARCH: SUN4U
  <4>[    0.000000] Ethernet address: 08:00:20:80:ec:80
  <4>[    0.000000] PROM: Built device tree with 31911 bytes of memory.
  <7>[    0.000000] On node 0 totalpages: 96949
  <7>[    0.000000]   DMA zone: 1007 pages used for memmap
  <7>[    0.000000]   DMA zone: 0 pages reserved
  <7>[    0.000000]   DMA zone: 95942 pages, LIFO batch:15
  <7>[    0.000000]   Normal zone: 0 pages used for memmap
  <4>[    0.000000] CPU[0]: Caches D[sz(16384):line_sz(32)] I[sz(16384):line_sz(32)] E[sz(2097152):line_sz(64)]
  <4>[    0.000000] Built 1 zonelists.  Total pages: 95942
  <5>[    0.000000] Kernel command line: root=/dev/disk/by-uuid/45c63fea-47a2-4f1e-8c8c-d330206b0984 ro quiet splash
  <4>[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
  <4>[   44.350588] Console: colour dummy device 80x25
  <4>[   44.356050] Dentry cache hash table entries: 131072 (order: 7, 1048576 bytes)
  <4>[   44.361097] Inode-cache hash table entries: 65536 (order: 6, 524288 bytes)
  <4>[   44.420994] Memory: 767936k available (2520k kernel code, 1072k data, 152k init) [fffff80000000000,0000000047f46000]
  <4>[   44.497915] Calibrating delay using timer specific routine.. 592.35 BogoMIPS (lpj=1184703)
  <6>[   44.498297] Security Framework v1.0.0 initialized
  <6>[   44.498350] SELinux:  Disabled at boot.
  <4>[   44.498462] Mount-cache hash table entries: 512
  <6>[   44.501092] NET: Registered protocol family 16
  <4>[   44.509131] PCI: Probing for controllers.
  <4>[   44.514488] SYSIO: UPA portID 1f, at 000001fe00000000
  <4>[   44.519835] sbus0: Clock 25.0 MHz
  <4>[   44.523990] dma0: HME DVMA gate array 
  <6>[   44.524281] usbcore: registered new interface driver usbfs
  <6>[   44.524516] usbcore: registered new interface driver hub
  <6>[   44.524801] usbcore: registered new device driver usb
  <6>[   44.525626] AUXIO: Found device at /sbus@1f,0/auxio@f,1900000
  <6>[   44.525885] /sbus@1f,0/eeprom@f,1200000: Clock regs at 000001fff1200000
  <6>[   44.527938] NET: Registered protocol family 2
  <4>[   44.566201] IP route cache hash table entries: 8192 (order: 3, 65536 bytes)
  <4>[   44.566922] TCP established hash table entries: 32768 (order: 5, 262144 bytes)
  <4>[   44.568124] TCP bind hash table entries: 16384 (order: 4, 131072 bytes)
  <6>[   44.568829] TCP: Hash tables configured (established 32768 bind 16384)
  <6>[   44.568852] TCP reno registered
  <6>[   44.578552] checking if image is initramfs... it is
  <4>[   48.114889] Freeing initrd memory: 5785k freed
  <6>[   48.116538] audit: initializing netlink socket (disabled)
  <5>[   48.116601] audit(1177715511.772:1): initialized
  <4>[   48.116911] Total HugeTLB memory allocated, 0
  <5>[   48.117526] VFS: Disk quotas dquot_6.5.1
  <4>[   48.117642] Dquot-cache hash table entries: 1024 (order 0, 8192 bytes)
  <6>[   48.117990] io scheduler noop registered
  <6>[   48.118011] io scheduler anticipatory registered
  <6>[   48.118029] io scheduler deadline registered
  <6>[   48.118101] io scheduler cfq registered (default)
  <4>[   48.146017] Console: switching to colour frame buffer device 144x56
  <4>[   48.171078] /sbus@1f,0/cgsix@0,0: CGsix [TGX+ sparc] at 0:1ff00000000
  <3>[   48.348709] rtc_init: no PC rtc found
  <6>[   48.348987] [drm] Initialized drm 1.1.0 20060810
  <6>[   48.349737] f005bbcc: ttyS0 at MMIO 0x1fff1100000 (irq = 9) is a zs
  <6>[   48.350220] f005bbcc: ttyS1 at MMIO 0x1fff1100004 (irq = 9) is a zs
  <6>[   48.351039] f005d06c: Keyboard at MMIO 1fff1000000 (irq = 9) is a zs
  <6>[   48.351066] f005d06c: Mouse at MMIO 1fff1000004 (irq = 9) is a zs
  <6>[   48.352534] mice: PS/2 mouse device common for all mice
  <6>[   49.004801] input: Sun Type 5 keyboard as /class/input/input0
  <6>[   49.005593] input: Sun Mouse as /class/input/input1
  <4>[   49.009737] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
  <6>[   49.011585] loop: loaded (max 8 devices)
  <6>[   49.011876] sunhme.c:v3.00 June 23, 2006 David S. Miller (davem@davemloft.net)
  <6>[   49.013146] eth0: HAPPY MEAL (SBUS) 10/100baseT Ethernet 08:00:20:80:ec:80 
  <6>[   49.014107] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
  <6>[   49.014140] ide: Assuming 50MHz system bus speed for PIO modes; override with idebus=xx
  <4>[   49.014768] rtc_sun_init: Registered Mostek RTC driver.
  <6>[   49.015098] usbcore: registered new interface driver libusual
  <6>[   49.016006] TCP cubic registered
  <6>[   49.016054] NET: Registered protocol family 1
  <6>[   49.016091] NET: Registered protocol family 17
  <5>[   50.137491] SCSI subsystem initialized
  <4>[   50.143924] esp0: IRQ 10 SCSI ID 7 Clk 40MHz CCYC=25000 CCF=8 TOut 167 NCR53C9XF(espfast)
  <6>[   50.144779] scsi0 : Sparc ESP366-HME
  <6>[   50.180134] Capability LSM initialized
  <5>[   50.947467] scsi 0:0:0:0: Direct-Access     SEAGATE  ST34371W SUN4.2G 7462 PQ: 0 ANSI: 2
  <5>[   50.964588] scsi 0:0:1:0: Direct-Access     SEAGATE  ST32550W SUN2.1G 0418 PQ: 0 ANSI: 2
  <5>[   52.011513] scsi 0:0:6:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1401 1007 PQ: 0 ANSI: 2
  <6>[   54.113133] esp0: target 0 [period 100ns offset 15 20.00MHz FAST-WIDE SCSI-II]
  <5>[   54.178657] SCSI device sda: 8385121 512-byte hdwr sectors (4293 MB)
  <5>[   54.183780] sda: Write Protect is off
  <7>[   54.183801] sda: Mode Sense: cf 00 10 08
  <5>[   54.201156] SCSI device sda: write cache: disabled, read cache: enabled, supports DPO and FUA
  <5>[   54.203960] SCSI device sda: 8385121 512-byte hdwr sectors (4293 MB)
  <5>[   54.209117] sda: Write Protect is off
  <7>[   54.209138] sda: Mode Sense: cf 00 10 08
  <5>[   54.214329] SCSI device sda: write cache: disabled, read cache: enabled, supports DPO and FUA
  <6>[   54.214359]  sda: sda1 sda2 sda3 sda4
  <5>[   54.234258] sd 0:0:0:0: Attached scsi disk sda
  <6>[   54.236938] esp0: target 1 [period 100ns offset 15 20.00MHz FAST-WIDE SCSI-II]
  <5>[   54.274209] sdb: Unit Not Ready, sense:
  <6>[   54.274227] : <<DEFERRED>> [descriptor]: sense key=0xf
  <6>[   54.274249]     <<vendor>> ASC=0xf8 ASCQ=0x0ASC=0xf8 ASCQ=0x0
  <5>[   54.315597] sdb : READ CAPACITY failed.
  <4>[   54.315609] sdb : status=1, message=00, host=0, driver=08 
  <6>[   54.315630] sd: <<DEFERRED>> [descriptor]: sense key=0xf
  <6>[   54.315650]     <<vendor>> ASC=0xf8 ASCQ=0x0ASC=0xf8 ASCQ=0x0
  <4>[   54.359406] sdb: test WP failed, assume Write Enabled
  <3>[   54.374577] sdb: asking for cache data failed
  <3>[   54.374805] sdb: assuming drive cache: write through
  <5>[   54.375245] sd 0:0:1:0: Attached scsi disk sdb
  <5>[   54.410325] sd 0:0:0:0: Attached scsi generic sg0 type 0
  <5>[   54.410446] sd 0:0:1:0: Attached scsi generic sg1 type 0
  <5>[   54.410598] scsi 0:0:6:0: Attached scsi generic sg2 type 5
  <6>[   54.442223] esp0: target 6 asynchronous
  <4>[   54.474302] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
  <6>[   54.474330] Uniform CD-ROM driver Revision: 3.20
  <7>[   54.474603] sr 0:0:6:0: Attached scsi CD-ROM sr0
  <6>[   55.397596] kjournald starting.  Commit interval 5 seconds
  <6>[   55.397647] EXT3-fs: mounted filesystem with ordered data mode.
  <5>[   65.231432] eth0: Auto-Negotiation unsuccessful, trying force link mode
  <6>[   69.102652] Adding 240952k swap on /dev/disk/by-uuid/124ac01b-3a48-4cd3-b331-1d0dc406c2bc.  Priority:-1 extents:1 across:240952k
  <6>[   69.433866] EXT3 FS on sda2, internal journal
  <6>[   70.062161] kjournald starting.  Commit interval 5 seconds
  <6>[   70.065312] EXT3 FS on sda1, internal journal
  <6>[   70.065339] EXT3-fs: mounted filesystem with ordered data mode.
  <6>[   73.630339] eth0: Link has been forced up using internal transceiver at 10Mb/s, Half Duplex.
  <6>[   76.945831] NET: Registered protocol family 10
  <6>[   76.946279] lo: Disabled Privacy Extensions
  <7>[   86.972527] eth0: no IPv6 routers present
  <3>[   99.792754] sr0: CDROM (ioctl) error, command: <6>cdb[0]=0x0 00 00 00 00 00 00
  <6>[   99.793402] sr: <<DEFERRED>> [descriptor]: sense key=0xf
  <6>[   99.793424]     <<vendor>> ASC=0xf8 ASCQ=0x0ASC=0xf8 ASCQ=0x0
  <3>[   99.817003] sr0: CDROM (ioctl) error, command: <6>cdb[0]=0x0 00 00 00 00 00 00
  <6>[   99.817638] sr: <<DEFERRED>> [descriptor]: sense key=0xf
  <6>[   99.817659]     <<vendor>> ASC=0xf8 ASCQ=0x0ASC=0xf8 ASCQ=0x0
----- kernel log end -----
>> misc.1: misc data
>> misc.1.2: open parallel
>> misc.2.1: io
>> misc.2.2: dma
>> misc.2.3: irq
----- /proc/ioports -----
  1ffe8800000-1ffe880000f : dma
  1ffe8810000-1ffe881003f : ESP Registers
  1ffe8c00000-1ffe8c0010f : HME Global Regs
  1ffe8c02000-1ffe8c02033 : HME TX Regs
  1ffe8c04000-1ffe8c0401f : HME RX Regs
  1ffe8c06000-1ffe8c0635f : HME BIGMAC Regs
  1ffe8c07000-1ffe8c0701f : HME Tranceiver Regs
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:      31904     <NULL>  timer
    1:          0      sun4u  SYSIO UE
    2:          0      sun4u  SYSIO CE
    3:          0      sun4u  SYSIO SBUS Error
    9:        252      sun4u  zs
   10:      14502      sun4u  ESP SCSI
   11:         32      sun4u  eth0
----- /proc/interrupts end -----
----- /proc/dma -----
   4: cascade
----- /proc/dma end -----
>> misc.3: FPU
>> misc.3.1: DMA
>> misc.3.2: PIC
>> misc.3.3: timer
>> misc.3.4: RTC
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  cpu		: TI UltraSparc II  (BlackBird)
  fpu		: UltraSparc II integrated FPU
  prom		: OBP 3.11.2 1997/12/05 10:25
  type		: sun4u
  ncpus probed	: 1
  ncpus active	: 1
  D$ parity tl1	: 0
  I$ parity tl1	: 0
  Cpu0Bogo	: 592.35
  Cpu0ClkTck	: 0000000011a4a1c0
  MMU Type	: Spitfire
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x47f46000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0x2f45c000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0xfaf4564974d68479) -----
              sr: /devices/sbus0/sbus[f006661c]/host0/target0:0:6/0:0:6:0
              sd: /devices/sbus0/sbus[f006661c]/host0/target0:0:1/0:0:1:0
              sd: /devices/sbus0/sbus[f006661c]/host0/target0:0:0/0:0:0:0
        sermouse: /devices/root/f005b27c/f005d06c/serio1
          sunkbd: /devices/root/f005b27c/f005d06c/serio0
             esp: /devices/sbus0/sbus[f006661c]
             hme: /devices/sbus0/sbus[f006d018]
              zs: /devices/root/f005b27c/f005d06c
              zs: /devices/root/f005b27c/f005bbcc
             cg6: /devices/root/f005b27c/f0074c24
           clock: /devices/root/f005b27c/f005bb18
           auxio: /devices/root/f005b27c/f005b88c
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
sysfs: no such bus: pci
---------- PCI raw data ----------
---------- PCI raw data end ----------
>> pci.4: build list
>> pci.3: macio
sysfs: no such bus: macio
>> pci.3: vio
sysfs: no such bus: vio
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- serial info -----
----- serial info end -----
>> serial.2: build list
>> misc.5: misc data
----- misc resources -----
i/o:0 0x1ffe8800000 - 0x1ffe880000f (0x10) "dma"
i/o:0 0x1ffe8810000 - 0x1ffe881003f (0x40) "ESP Registers"
i/o:0 0x1ffe8c00000 - 0x1ffe8c0010f (0x110) "HME Global Regs"
i/o:0 0x1ffe8c02000 - 0x1ffe8c02033 (0x34) "HME TX Regs"
i/o:0 0x1ffe8c04000 - 0x1ffe8c0401f (0x20) "HME RX Regs"
i/o:0 0x1ffe8c06000 - 0x1ffe8c0635f (0x360) "HME BIGMAC Regs"
i/o:0 0x1ffe8c07000 - 0x1ffe8c0701f (0x20) "HME Tranceiver Regs"
irq:0  0 (    31904) "<NULL>  timer"
irq:0  1 (        0) "sun4u  SYSIO UE"
irq:0  2 (        0) "sun4u  SYSIO CE"
irq:0  3 (        0) "sun4u  SYSIO SBUS Error"
irq:0  9 (      252) "sun4u  zs"
irq:0 10 (    14502) "sun4u  ESP SCSI"
irq:0 11 (       32) "sun4u  eth0"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/modprobe parport_pc" -----
  WARNING: Error inserting parport (/lib/modules/2.6.20-15-sparc64/kernel/drivers/parport/parport.ko): Operation not permitted
  FATAL: Error inserting parport_pc (/lib/modules/2.6.20-15-sparc64/kernel/drivers/parport/parport_pc.ko): Operation not permitted
----- return code: ? -----
----- exec: "/sbin/modprobe lp" -----
  WARNING: Error inserting parport (/lib/modules/2.6.20-15-sparc64/kernel/drivers/parport/parport.ko): Operation not permitted
  FATAL: Error inserting lp (/lib/modules/2.6.20-15-sparc64/kernel/drivers/char/lp.ko): Operation not permitted
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
----- parallel info end -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide_cd " -----
  FATAL: Error inserting ide_cd (/lib/modules/2.6.20-15-sparc64/kernel/drivers/ide/ide-cd.ko): Operation not permitted
----- return code: ? -----
----- exec: "/sbin/modprobe st " -----
  FATAL: Error inserting st (/lib/modules/2.6.20-15-sparc64/kernel/drivers/scsi/st.ko): Operation not permitted
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom
----- /proc/sys/dev/cdrom/info -----
drive name:		sr0
drive speed:		40
drive # of slots:	1
Can close tray:		1
Can open tray:		1
Can lock tray:		1
Can change speed:	1
Can select disk:	0
Can read multisession:	1
Can read MCN:		1
Reports media changed:	1
Can play audio:		1
Can write CD-R:		0
Can write CD-RW:	0
Can read DVD:		1
Can write DVD-R:	0
Can write DVD-RAM:	0
Can read MRW:		1
Can write MRW:		1
Can write RAM:		1
----- /proc/sys/dev/cdrom/info end -----
>> block.4: partition
----- /proc/partitions -----
     8     0    4192560 sda
     8     1      96390 sda1
     8     2    3847567 sda2
     8     3    4184932 sda3
     8     4     240975 sda4
----- /proc/partitions end -----
disks:
  sda
partitions:
  sda1
  sda2
  sda3
  sda4
>> block.5: get sysfs block dev data
  block: name = ram0, path = /block/ram0
    dev = 1:0
    range = 1
  block: name = ram1, path = /block/ram1
    dev = 1:1
    range = 1
  block: name = ram2, path = /block/ram2
    dev = 1:2
    range = 1
  block: name = ram3, path = /block/ram3
    dev = 1:3
    range = 1
  block: name = ram4, path = /block/ram4
    dev = 1:4
    range = 1
  block: name = ram5, path = /block/ram5
    dev = 1:5
    range = 1
  block: name = ram6, path = /block/ram6
    dev = 1:6
    range = 1
  block: name = ram7, path = /block/ram7
    dev = 1:7
    range = 1
  block: name = ram8, path = /block/ram8
    dev = 1:8
    range = 1
  block: name = ram9, path = /block/ram9
    dev = 1:9
    range = 1
  block: name = ram10, path = /block/ram10
    dev = 1:10
    range = 1
  block: name = ram11, path = /block/ram11
    dev = 1:11
    range = 1
  block: name = ram12, path = /block/ram12
    dev = 1:12
    range = 1
  block: name = ram13, path = /block/ram13
    dev = 1:13
    range = 1
  block: name = ram14, path = /block/ram14
    dev = 1:14
    range = 1
  block: name = ram15, path = /block/ram15
    dev = 1:15
    range = 1
  block: name = loop0, path = /block/loop0
    dev = 7:0
    range = 1
  block: name = loop1, path = /block/loop1
    dev = 7:1
    range = 1
  block: name = loop2, path = /block/loop2
    dev = 7:2
    range = 1
  block: name = loop3, path = /block/loop3
    dev = 7:3
    range = 1
  block: name = loop4, path = /block/loop4
    dev = 7:4
    range = 1
  block: name = loop5, path = /block/loop5
    dev = 7:5
    range = 1
  block: name = loop6, path = /block/loop6
    dev = 7:6
    range = 1
  block: name = loop7, path = /block/loop7
    dev = 7:7
    range = 1
  block: name = sda, path = /block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 0:0:0:0 driver = sd
      path = /devices/sbus0/sbus[f006661c]/host0/target0:0:0/0:0:0:0
    vendor = SEAGATE
    model = ST34371W SUN4.2G
    rev = 7462
    type = 0
>> block.5: /dev/sda
  block: name = sdb, path = /block/sdb
    dev = 8:16
    range = 16
    block device: bus = scsi, bus_id = 0:0:1:0 driver = sd
      path = /devices/sbus0/sbus[f006661c]/host0/target0:0:1/0:0:1:0
    vendor = SEAGATE
    model = ST32550W SUN2.1G
    rev = 0418
    type = 0
>> block.5: /dev/sdb
  block: name = sr0, path = /block/sr0
    dev = 11:0
    range = 1
    block device: bus = scsi, bus_id = 0:0:6:0 driver = sr
      path = /devices/sbus0/sbus[f006661c]/host0/target0:0:6/0:0:6:0
    vendor = TOSHIBA
    model = DVD-ROM SD-M1401
    rev = 1007
    type = 5
>> block.5: /dev/sr0
>> block.5.1: /dev/sr0 cache
  scsi cache: 0x00
>> scsi.1: scsi modules
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:0:0 driver = sd
      path = /devices/sbus0/sbus[f006661c]/host0/target0:0:0/0:0:0:0
  scsi: name = sg1, path = /class/scsi_generic/sg1
    dev = 21:1
    scsi device: bus_id = 0:0:1:0 driver = sd
      path = /devices/sbus0/sbus[f006661c]/host0/target0:0:1/0:0:1:0
  scsi: name = sg2, path = /class/scsi_generic/sg2
    dev = 21:2
    scsi device: bus_id = 0:0:6:0 driver = sr
      path = /devices/sbus0/sbus[f006661c]/host0/target0:0:6/0:0:6:0
>> usb.1: sysfs drivers
>> usb.2: usb
sysfs: no such bus: usb
>> usb.3.1: joydev mod
----- exec: "/sbin/modprobe joydev " -----
  FATAL: Module joydev not found.
----- return code: ? -----
>> usb.3.2: evdev mod
>> usb.3.3: input
  input: name = mouse0, path = /class/input/input1/mouse0
    dev = 13:32
    input device: bus = serio, bus_id = serio1 driver = sermouse
      path = /devices/root/f005b27c/f005d06c/serio1
  input: name = event0, path = /class/input/input0/event0
    dev = 13:64
    input device: bus = serio, bus_id = serio0 driver = sunkbd
      path = /devices/root/f005b27c/f005d06c/serio0
  input: name = event1, path = /class/input/input1/event1
    dev = 13:65
    input device: bus = serio, bus_id = serio1 driver = sermouse
      path = /devices/root/f005b27c/f005d06c/serio1
>> usb.3.4: lp
sysfs: no such class: usb
>> usb.3.5: serial
>> modem.1: serial
******  started child process 3616 (15s/120s)  ******
******  stopped child process 3616 (120s)  ******
>> mouse.2: serial
******  started child process 3617 (20s/20s)  ******
******  stopped child process 3617 (20s)  ******
>> sbus.1: sun sbus
>> input.1: joydev mod
----- exec: "/sbin/modprobe joydev " -----
  FATAL: Module joydev not found.
----- return code: ? -----
>> input.1.1: evdev mod
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0013 Vendor=0010 Product=0005 Version=0100
  N: Name="Sun Type 5 keyboard"
  P: Phys=zs/serio0/input0
  S: Sysfs=/class/input/input0
  H: Handlers=kbd event0 
  B: EV=160003
  B: KEY=7ff e09ffffd01cfffff fffffffffffffffe
  B: LED=f
  B: SND=3
  
  I: Bus=0013 Vendor=0002 Product=0001 Version=0100
  N: Name="Sun Mouse"
  P: Phys=zs/serio1/input0
  S: Sysfs=/class/input/input1
  H: Handlers=mouse0 event1 
  B: EV=7
  B: KEY=70000 0 0 0 0
  B: REL=3
  
----- /proc/bus/input/devices end -----
bus = 19, name = Sun Type 5 keyboard
  handlers = kbd event0
  key = 000007ffffffffffffffffff
  mouse buttons = 0
  mouse wheels = 0
bus = 19, name = Sun Mouse
  handlers = mouse0 event1
  key = 0007000000000000000000000000000000000000
  rel = 00000003
  mouse buttons = 0
  mouse wheels = 0
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  cpu		: TI UltraSparc II  (BlackBird)
  fpu		: UltraSparc II integrated FPU
  prom		: OBP 3.11.2 1997/12/05 10:25
  type		: sun4u
  ncpus probed	: 1
  ncpus active	: 1
  D$ parity tl1	: 0
  I$ parity tl1	: 0
  Cpu0Bogo	: 592.35
  Cpu0ClkTck	: 0000000011a4a1c0
  MMU Type	: Spitfire
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> kbd.1: sun kbd
>> fb.1: read info
>> net.1: get network data
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    hw_addr = 08:00:20:80:ec:80
    net device: path = /devices/sbus0/sbus[f006d018]
    net driver: name = hme, path = /bus/sbus/drivers/hme
  net interface: name = lo, path = /class/net/lo
    type = 772
    hw_addr = 00:00:00:00:00:00
  eth0: GLINK ethtool error: Operation not permitted
  lo: GLINK ethtool error: Operation not permitted
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
eth0: socket failed: Operation not permitted
>> wlan.1: detecting wlan features
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/sda
  read_block0: open(/dev/sda) failed
>> int.4.2: /dev/sdb
  read_block0: open(/dev/sdb) failed
>> int.4: floppy
>> int.6: mouse
>> int.7: hdb
>> int.7.1: modules
>> int.8: usbscsi
>> int.9: hotplug
>> int.10: modem
>> int.11: wlan
>> int.12: udev
-----  udevinfo -----
  P: /block/loop0
  N: loop0
  L: 0
  
  P: /block/loop1
  N: loop1
  L: 0

some deleted .....

P: /block/sr0
  N: scd0
  L: 0
  S: sr0
  S: cdrom
  S: dvd
  E: ID_CDROM=1
  E: ID_CDROM_DVD=1
  E: ID_CDROM_MRW=1
  E: ID_CDROM_MRW_W=1
  E: ID_CDROM_RAM=1
  E: ID_VENDOR=TOSHIBA
  E: ID_MODEL=DVD-ROM_SD-M1401
  E: ID_REVISION=1007
  E: ID_SERIAL=
  E: ID_SERIAL_SHORT=
  E: ID_TYPE=cd
  E: ID_BUS=scsi
  
  P: /class/graphics/fb0
  N: fb0
  L: 0
  some other stuff deleted

=========== end debug info ============
01: None 00.0: 10107 System
  [Created at sys.59]
  Unique ID: rdCR.vmcEgiNKFp3
  Hardware Class: system
  Model: "System"
  SystemType: "sun4u"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.1U7kMMuA8l4
  Hardware Class: unknown
  Model: "DMA controller"
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.Sg+U8CCNfvC
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0x2f45bfff (rw)
  Memory Size: 768 MB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: SCSI 00.0: 10600 Disk
  [Created at block.218]
  Unique ID: 0549.IlbFVFw1+n4
  SysFS ID: /block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/sbus0/sbus[f006661c]/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "SEAGATE ST34371W SUN4.2G"
  Vendor: "SEAGATE"
  Device: "ST34371W SUN4.2G"
  Revision: "7462"
  Driver: "esp", "sd"
  Device File: /dev/sda (/dev/sg0)
  Device Files: /dev/sda, /dev/disk/by-id/scsi-SSEAGATE_ST34371W_SUN4.2JDN193320E79ZE, /dev/disk/by-uuid/29d2e4b1-0b9e-46b0-be80-927d73a3f313
  Device Number: block 8:0-8:15 (char 21:0)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 11300 Partition
  [Created at block.387]
  Unique ID: 1tKY.iRIkxq5hwXF
  Parent ID: 0549.IlbFVFw1+n4
  SysFS ID: /block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/scsi-SSEAGATE_ST34371W_SUN4.2JDN193320E79ZE-part1, /dev/disk/by-uuid/29d2e4b1-0b9e-46b0-be80-927d73a3f313
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (Disk)

07: None 00.0: 11300 Partition
  [Created at block.387]
  Unique ID: U2bc.iRIkxq5hwXF
  Parent ID: 0549.IlbFVFw1+n4
  SysFS ID: /block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/scsi-SSEAGATE_ST34371W_SUN4.2JDN193320E79ZE-part2, /dev/disk/by-uuid/45c63fea-47a2-4f1e-8c8c-d330206b0984
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (Disk)

08: None 00.0: 11300 Partition
  [Created at block.387]
  Unique ID: xDrg.iRIkxq5hwXF
  Parent ID: 0549.IlbFVFw1+n4
  SysFS ID: /block/sda/sda3
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda3
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (Disk)

09: None 00.0: 11300 Partition
  [Created at block.387]
  Unique ID: OP5l.iRIkxq5hwXF
  Parent ID: 0549.IlbFVFw1+n4
  SysFS ID: /block/sda/sda4
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda4
  Device Files: /dev/sda4, /dev/disk/by-id/scsi-SSEAGATE_ST34371W_SUN4.2JDN193320E79ZE-part4, /dev/disk/by-uuid/124ac01b-3a48-4cd3-b331-1d0dc406c2bc
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (Disk)

10: SCSI 01.0: 10600 Disk
  [Created at block.229]
  Unique ID: TGKD.S9T6iOoA0p6
  SysFS ID: /block/sdb
  SysFS BusID: 0:0:1:0
  SysFS Device Link: /devices/sbus0/sbus[f006661c]/host0/target0:0:1/0:0:1:0
  Hardware Class: disk
  Model: "SEAGATE ST32550W SUN2.1G"
  Vendor: "SEAGATE"
  Device: "ST32550W SUN2.1G"
  Revision: "0418"
  Driver: "esp", "sd"
  Device File: /dev/sdb (/dev/sg1)
  Device Files: /dev/sdb, /dev/disk/by-id/scsi-SSEAGATE_ST32550W_SUN2.100000000
  Device Number: block 8:16-8:31 (char 21:1)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: SCSI 06.0: 10602 CD-ROM (DVD)
  [Created at block.222]
  Unique ID: vAV0.MtNMY6E71qB
  SysFS ID: /block/sr0
  SysFS BusID: 0:0:6:0
  SysFS Device Link: /devices/sbus0/sbus[f006661c]/host0/target0:0:6/0:0:6:0
  Hardware Class: cdrom
  Model: "TOSHIBA DVD-ROM SD-M1401"
  Vendor: "TOSHIBA"
  Device: "DVD-ROM SD-M1401"
  Revision: "1007"
  Driver: "esp", "sr"
  Device File: /dev/sr0 (/dev/sg2)
  Device Files: /dev/sr0, /dev/scd0, /dev/cdrom, /dev/dvd
  Device Number: block 11:0 (char 21:2)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Drive Speed: 40

12: PS/2 00.0: 10800 Keyboard
  [Created at input.139]
  Unique ID: pjEi.bJNsqxw9pJE
  Hardware Class: keyboard
  Model: "Sun Type 5 keyboard"
  Vendor: int 0x0211 
  Device: int 0x0001 "Sun Type 5 keyboard"
  Device File: /dev/input/event0
  Device Number: char 13:64
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.159]
  Unique ID: yLPQ.8eaO1XU_9zD
  Hardware Class: mouse
  Model: "Sun Mouse"
  Vendor: int 0x0210 
  Device: int 0x0000 "Sun Mouse"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event1
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 0
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: None 00.0: 10103 CPU
  [Created at cpu.228]
  Unique ID: rdCR.L5Xer5eMNu7
  Hardware Class: cpu
  Arch: UltraSparc (64)
  Model: 0.0.0 "TI UltraSparc II  (BlackBird)"
  Platform: "sun4u"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: None 00.0: 10701 Ethernet
  [Created at net.119]
  Unique ID: usDW.vnwWAn0UAo4
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/sbus0/sbus[f006d018]
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "hme"
  Device File: eth0
  HW Address: 08:00:20:80:ec:80
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: None 00.0: 10700 Loopback
  [Created at net.119]
  Unique ID: ZsBS.0NPNTtaUSp9
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Config Status: cfg=new, avail=yes, need=no, active=unknown


End of HWinfo dump

---

### Post by erm67 on 2007-04-28
> **sandpiper said:**
> 
Based on this understanding (whcih could be wrong!) I have pursed any utlity that would simulate this dataflow process .. Hence the reason why I have looked at the utlity fbset.. You will see that the address for the framebuffer is 00000. This cannot be right? unless of course this is some kind of offset address. 

It looks like many have the same problem as you ....

Xorg relies on a device in the kernel to access the main functions of the card this is the source:
[http://www.gelato.unsw.edu.au/lxr/source/drivers/video/cg6.c](http://www.gelato.unsw.edu.au/lxr/source/drivers/video/cg6.c)
0000000 should be the physical address, this is probably a bug in the linux kernel, and considering the age of the card probably nobody will fix it. it seems the card worked with kernels 2.4.x but ubuntu doesn't work without a kernel 2.6. I think Debian still supports a 2.4 kernel so you migth try that.

dmesg |grep cg

kernel 2.6.x
cg6: CGSix [TGX+ sparc] at 1ff: 000000000
kernel 2.4.x
fb0: cgsix at 1ff 30000000 TEC Rev 4 CPU sparc Rev b [TGX+]

Besides, are  you aware that the cg6 grafic card can only support 8bit grafich i.e. 256 colours? Even if you get it work you desktop will be almost useless.

---

### Post by sandpiper on 2007-04-29
> **erm67 said:**
> It looks like many have the same problem as you ....

Xorg relies on a device in the kernel to access the main functions of the card this is the source:
[http://www.gelato.unsw.edu.au/lxr/source/drivers/video/cg6.c](http://www.gelato.unsw.edu.au/lxr/source/drivers/video/cg6.c)
0000000 should be the physical address, this is probably a bug in the linux kernel, and considering the age of the card probably nobody will fix it. it seems the card worked with kernels 2.4.x but ubuntu doesn't work without a kernel 2.6. I think Debian still supports a 2.4 kernel so you migth try that.

dmesg |grep cg

kernel 2.6.x
cg6: CGSix [TGX+ sparc] at 1ff: 000000000
kernel 2.4.x
fb0: cgsix at 1ff 30000000 TEC Rev 4 CPU sparc Rev b [TGX+]

Besides, are  you aware that the cg6 grafic card can only support 8bit grafich i.e. 256 colours? Even if you get it work you desktop will be almost useless.

Thanks. Yes you have confirmed my suspicions! - wasn't sure being a newbie. (I presume there is  a bug in the 2.6 version of the hardware probing routines ).Thanks for taking the time to respond on this. 

Going forward I think I have the following options:
 
1) escalate the bug to ? (I don't know the process) . Perhaps investigate the source around the sysfs though with limited programming experience I would not be able to recognise the fault if I saw it! As you say I may be a "lone voice" here. 

Just wondering if anybody else who may by chance  be reading this from the SPARC user community may have an opinion......?????. Naturally I wouuld be happy  to be the guinea pig to contribute status reports. While you say the the TGX card is albeit "useless" I only wish basic desktop functionality so I can interact with Ubuntu a little easier. So I am keen to pusue this option if the consensus is that it "is" viable particularly when it is seen in the context of 2.4 to 2.6 transition. 

One thought I had was could I recreate the fb0: device node or create a new one fb1: that looks to the graphics card. I have tried MAKEDEV but this got me nowhere?

2) Source an alternative graphics card for the workstation that is confirmed to work as you have already suggested. My recent visit to e-bay gave me only TGX cards (as probably I would have expected). Do you know of anyone willing to sell or anywhere I could source such cards as the Creative or Elite prefereably close to New Zealand to keep the postal costs down. I have tried SUN here in New Zealand with no luck

3) Put the money I would have paid out to an alternative card towards a new intel platform and install Ubuntu (I confess not my preferred option)

4) Pursue the setting up of a separate Xwindows on separate intel based hardware and link to the server session on the Sparc. This way I can still utilise the SUN hardware and disc arrays and tape hardware (that was the main driver for looking at the SPARC in the first place)  Not the ideal 

5) Simply install Solaris version 10. Given the following and growth profile of Ubuntu I am not sure whether this is a wise move (ie not sure where Solaris 10 is going). The added complication is I need to patch the SCSI DVD ROM drive to recognise the media!.  Certainly I seem to be frustrated every way I turn... 

Appreciate any comments that you have... Chris

---

### Post by erm67 on 2007-04-29
> **sandpiper said:**
> 
1) escalate the bug to ? (I don't know the process) .
(davem@redhat.com) is the developer who actually mantains ther driver, but it could be hard to get his attention. Also here [http://bugzilla.kernel.org](http://bugzilla.kernel.org) but they will reject your report if you have not tested it against the mainline kernel 2.6.21, so maybe first download the latest vanilla kernel compile it and test.

> **sandpiper said:**
> One thought I had was could I recreate the fb0: device node or create a new one fb1: that looks to the graphics card. I have tried MAKEDEV but this got me nowhere?
Devices file are simply "placeholder" created by the mknod utility and simply contains the major and minor number of the device, and these day are dinamically created by a daemon anyway. To effectively reinitialize the driver you have to rmmod it from the kernel and modprobe it  gain. Try also modinfo cg6 it will show the available options for the driver.

> **sandpiper said:**
> 2) Source an alternative graphics card for the workstation that is confirmed to work as you have already suggested. 
I would suggest a creator 3d 3 series, easyer to find and cheaper than a elite horizontal. There are always many for sale usually in USA or Germany if you live in Europe, for down under I don't know. I think they cost around 40 USD+shipping.

> **sandpiper said:**
> 3) Put the money I would have paid out to an alternative card towards a new intel platform and install Ubuntu (I confess not my preferred option)with 40usd+shipping you cannot buy a good intel machine, well maybe if they ship from north pole :)


> **sandpiper said:**
> 4) Pursue the setting up of a separate Xwindows on separate intel based hardware and link to the server session on the Sparc. 
remote X over 100Mbit link can be slow to run i.e. KDE, maybe a 1Gb link but than you have the problem of finding a 1Gb sbus card for the Ultra ... a solution many adopts I think.

> **sandpiper said:**
> 5) Simply install Solaris version 10. Given the following and growth profile of Ubuntu I am not sure whether this is a wise move (ie not sure where Solaris 10 is going). The added complication is I need to patch the SCSI DVD ROM drive to recognise the media!.  Certainly I seem to be frustrated every way I turn...  I ordered the media kit a few days ago but still has not arrived, what problems have you had with the dvd?

Solution 6:
I don't say it too loud here but [http://www.debian.org/ports/sparc/index.en.html](http://www.debian.org/ports/sparc/index.en.html) and install it with a kernel 2.4.x, it is still a supported option by debian, and is rumored to work. I will test this configuration next week because of my scsi problems.

---

### Post by sandpiper on 2007-04-29
Thanks for the comments on each of the options.  

Regarding the bug escalation  have no experience in Linux programming or compiling so I think I would get lost if i downloaded the latest vanilla kernel and tried to compile it. I thought that given Sun has a strategic relationship with Ubuntu I had the idea to focus my escalation efforts within the ubuntu forums/bug arena. (though I suspect the relationship is more at the server rather than desktop level).

I will also check again but I recall the cg6 is not a discrete module so will not respond to "modinfo" commands . I will investigate....

Thanks for the comments about the Creative card and approx cost... Will pursue this in parallel

> **erm67 said:**
> (davem@redhat.com) i
 
 I ordered the media kit a few days ago but still has not arrived, what problems have you had with the dvd?

Solution 6:
I don't say it too loud here but [http://www.debian.org/ports/sparc/index.en.html](http://www.debian.org/ports/sparc/index.en.html) and install it with a kernel 2.4.x, it is still a supported option by debian, and is rumored to work. I will test this configuration next week because of my scsi problems.

My DVD-ROM drive is a Toshiba SD-M1401 with firmware revision 1007. Your kerrnel log will show this.... When I placed the DVD media in the drive and typed "boot cdrom" I got the error message: "Bad magic number in disk label. Cannot open disk label package. Cannot open root device". From googling I discovered that  I need to update the drive's firmware by applying a patch. This is mentioned on the sun site for early media problems for  Solaris 9: 
[http://docs.sun.com/source/817-4190-10/lbnews.html](http://docs.sun.com/source/817-4190-10/lbnews.html)

I was hoping I could do this update using the Ubuntu server from the command line. Have not found out how to do this firmware upgrade yet. The "plan B" is to obviously buy another more modern SCSI DVD ROM drive. Here in New Zealand they are not available! More  expense... Hope you have more  luck....

Certainly interested in your success with 2.4. I haven't investigated yet whether an earlier verson of Ubuntu uses the 2.4 kernel. This could be an option for me..... Chris

---

