---
title: "problem with setting my SATA HDD in DMA mode"
date: 2008-04-01
forum: Server Platforms
---

### Post by dkosc on 2008-04-01
Hi

I need help from some ubuntu guru with my SATA hdd :)
I have Ubuntu 6.06 LTS server edition i would like to set hdd to work in DMA mode, also to enable DMA with default kernel modules (I'm not experienced in kernel configurating and compiling)
Here is some information if you need anything else just ask :)

here is error:
hdparm -d1 /dev/hdc 
[B][COLOR="sienna"]/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)[/B][/COLOR]

My motherboard is BloodIron P35-T2RL ( [http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=5495&CATEGORY_TYPE=INFINITY&SITE=US](http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=5495&CATEGORY_TYPE=INFINITY&SITE=US) )

other info:
uname -a:
[COLOR="sienna"]Linux collin 2.6.15-51-server #1 SMP Tue Feb 12 17:12:18 UTC 2008 i686 GNU/Linux[/COLOR]

hdparm -tT /dev/hdc     
[COLOR="sienna"]/dev/hdc:
 Timing cached reads:   4628 MB in  2.00 seconds = 2314.00 MB/sec
 Timing buffered disk reads:   22 MB in  3.16 seconds =   6.96 MB/sec[/COLOR]

lspci
[COLOR="sienna"]0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29c0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29c1 (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2937 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2938 (rev 02)
0000:00:1a.2 USB Controller: Intel Corporation: Unknown device 2939 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 293c (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 293e (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 2940 (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2948 (rev 02)
0000:00:1c.5 PCI bridge: Intel Corporation: Unknown device 294a (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2934 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2935 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2936 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 293a (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2916 (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2920 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 2930 (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2926 (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d3 (rev a1)
0000:03:00.0 IDE interface: Unknown device 197b:2368
0000:04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 22)[/COLOR]

hdparm -i /dev/hdc 
[COLOR="sienna"]/dev/hdc:
 Model=MAXTOR STM3320820AS, FwRev=3.AAE, SerialNo=6QF3N3V1
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7[/COLOR]

hdparm /dev/hdc   
[COLOR="sienna"]/dev/hdc:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38913/255/63, sectors = 625142448, start = 0[/COLOR]

---

### Post by mrsteveman1 on 2008-04-01
The kernel says you are already using UDMA2 here:

```
UDMA modes: udma0 udma1 *udma2 
```

However, that 6mb/s figure from the buffered read is really, really low, so I'm not sure whats going on.

Try running the command to turn DMA on using sudo before it like this:

```
sudo hdparm -d1 /dev/hdc 
```

Then run the buffered read again

---

### Post by dkosc on 2008-04-01
here:

sudo hdparm -d1 /dev/hdc
Password:

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)


since I'm lazy i do this:
sudo bash
so no need for sudo every time :)

---

### Post by prshah on 2008-04-01
> **dkosc said:**
> Hi

I need help from some ubuntu guru with my SATA hdd :)


SATA drives live at /dev/sdX... are you by any chance trying to enable DMA on your CDROM drive? hdc?

```
sudo fdisk -l
``` will give us more helpful information.

---

### Post by dkosc on 2008-04-01
weried, I assemble computer and it's definitlly SATA disks
In fact I have 2 identcal disk /dev/hdb and /dev/hdc

system is on /dev/hdb

sudo mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hdc1 on /media/hdc type ext3 (rw)

sudo fdisk -l
Password:

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       38156   306488038+  83  Linux
/dev/hdb2           38157       38913     6080602+   5  Extended
/dev/hdb5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       38913   312568641   83  Linux


I use /dev/hdc for test

but if I do:
sudo hdparm -d1 /dev/hdb

/dev/hdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

same as /dev/hdc
sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

---

### Post by mrsteveman1 on 2008-04-01
I've seen some versions of the Linux kernel switch around disk naming between hdX and sdX for some reason.

The output he posted did say its a maxtor drive, so its not the cdrom, though I'm not sure why it would refuse DMA.

Is this a performance problem? Is it acting too slow to use? That buffered read test seems to suggest it's quite slow.

---

### Post by dkosc on 2008-04-02
whole problem is when I start to copy large amount of data (through ftp/sftp/samba) I get around 4MB/s and load average is 3 even nothing else is running on linux box.

I red that HDIO_SET_DMA failed: Operation not permitted means there is no compiled support in kernel for my chipset so disk falls back to PIO mode.

If I get it right, my ata chipset is ICH9

I use "original" ubuntu6.06 LTS disk and now using generic kernel which was installed with distro.

CPU is CoreDuo and I hope it not some SMP problem :)

---

### Post by mrsteveman1 on 2008-04-02
As far as i remember, ICH9 chipsets came out in 2007, while the 2.6.15 kernel came out in the first quarter of 2005. Its possible that the developers have added support to the older kernel, they do update the 6.06 LTS kernel frequently. But since it doesn't seem to be working right, this is likely not the case.

The only real solution is to update the system to gutsy or hardy i suppose, unfortunate i know, but with Linux there is no other way to update drivers unless the distro developers backport them, and they don't seem to have done that here.

If you really want to you can just grab the newest kernel from kernel.org and compile it, leaving the rest of the system alone, that will give you the newer drivers.

---

### Post by dkosc on 2008-04-02
damn, that's what I was trying to avoid :)
OK if only solution is to learn how to compile kernel then it seems that I have no other choice :(

Hmm, Ubuntu linux 6.06 LTS is supported till 2011, if in 2008 you buy new PC and you don't have support in kernel for hardware it means that for all new PC in 2009 this distro will be quite useless 'cos on new SATA DVD (or even BluRay) you won't be able to install distro anyway? Or I just don't have luck and new kernel for 6.06LTS will be out soon and there will be no problem at all :)

---

### Post by mrsteveman1 on 2008-04-02
6.06 is supported by Canonical until 2011 or something, but it won't continue to work on new hardware. The assumption is that people bought hardware when 6.06 came out and want to continue using it as-is until Canonical stops releasing updates for the OS etc.

The limitation here is that almost every driver on a Linux system comes with the kernel, and they can't be easily swapped around due to the way the kernel is built, so in order to get new drivers for an old kernel you have to rely on the distro to backport them.

You can compile a new kernel pretty easily, its no more than a few commands and even after installing a new kernel you can boot into the old one if you need to without changing anything.

---

### Post by dkosc on 2008-04-02
OK thanks everyone for help.
kernel.org here I come :)

---

