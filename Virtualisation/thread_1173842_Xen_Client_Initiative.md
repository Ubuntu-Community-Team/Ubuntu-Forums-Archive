---
title: "Xen Client Initiative"
date: 2009-05-30
forum: Virtualisation
---

### Post by coloured on 2009-05-30
Ok heres the deal. Lately I have been trying to create a successful build of the new Xen Client. For those of you who dont know what this is, its going to be the next big thing in virtualization for client devices.
Basically it will allow you to have a true type 1 hypervisor running on your laptop or pc. This means you will be able to run multiple OS's without having to do it inside another OS. It also means that these virtual machines will be hardware independent.
 I have been able to build it, but how shipping it off to a memory stick fails. I will be sending the log to the person mentioned in the HOWTO but I thought I would log it here too for those of you who are interested, and who knows we may possibly be able to solve it.

I have built a Debian Lenny x86 VM for the purpose of this project - building the Xen client is not currently supported on a x64 host.

This is the main build info including all the links needed for building.
[http://xenbits.xensource.com/xenclient/#](http://xenbits.xensource.com/xenclient/#)

and this is a better rendition of the about info, kudos to this guy he has done some leg work.
[http://www.vergenet.net/~horms/](http://www.vergenet.net/~horms/)

Now make sure you follow the directions carefully on that second link.
If you are going to try to build the usb stick installer I suggest you download a copy of the modified .config file I have created and attached to this post (it is in zip format and I have also renamed the file to dotconfig, extract and issue cp dotconfig .config at the command prompt). Basically the config file found in ./configs/ call xenclient_usb_config doesnt built the root fs. this new one does, I have basically copied all the options from the xenclient_config file.
Again, I am unsure whether this is the way it should be done, but it makes sense.
The build process does take a long time and one thing to look out for before you start ensure you have zlib installed including the zlibdev, else it will fail the build 2 hours into it.

That is about everything - mine compiled successfully and I ended up with both the rootfs.i686.ext2.bz2 file and rootfs.i686.cpio.gz
This is where I had to revert back to the HOWTO document in the top level of the build directory.
After disabling the automount feature using this guide btw
[http://linux-addiction.blogspot.com/2009/02/how-to-disable-automount-cd-dvd-and-usb.html](http://linux-addiction.blogspot.com/2009/02/how-to-disable-automount-cd-dvd-and-usb.html)
I ran scripts/usb_stick.sh /dev/sda from the top level of the build directory.
It wrote the partition table OK
then set out with
Creating initrd
Making file system
Mounting initrd image at /mnt
unrolling cpio archive
Error unrolling cpio archive.
Aborting.

and thats as far as I get.
I have had a look through the script, but I am unsure exactly what it is trying to do and why it is failing, there isn't a lot of info out there about this, hence the reason I'm posting all this here.
So if anyone has any great ideas please let me know..
I'm so close but yet so far away.

Post here too if you have any questions about anything I have done so far, I am more than happy to help anyone who would like to get this up and running for themselves, the more the merrier.

---

### Post by spiked on 2009-07-01
Hi coloured,

I've been trying to build XCI on Ubuntu 9.04 for the last couple of days, but I"ve been having a lot of trouble installing XCI on Ubuntu 9.04, seems noone's documented a successful installation (on Ubuntu) online. 

Just in case you know about this, the following error occurs after doing a make, (after installing all the programs required, so no dependency problems): (XCI running on Ubuntu 9.04) 

..... 
checking for getpeerucred... no 
checking for getpeereid... no 
checking abstract socket namespace... configure: error: cannot run test  program while cross compiling 
See `config.log' for more details. 
make: ***  [/home/spike/build.git/build/build/build_i686/dbus-glib-0.72/.configured]  Error 1 

There are about 40 different 'config.log's in the xen folder, and the path for this particular config.log is not given.

There are some solutions posted online for this error, but no luck trying them so far.

Did you encounter this error? Can you send me more specific details about how you installed XCI on Lenny? Or did you just follow the instructions on the vergenet link to the letter? Because even I followed the same instructions but it doesn't seem to work on Ubuntu (gave the same cross compiling error above).

I've contacted Xen Support, but no reply yet. I'm trying to install Xen 3.4 on Ubuntu now, because 3.4 has XCI present in it, but otherwise I'm running out of ideas. Any advice/ideas?

Thanks.

---

### Post by iInstallUnattended on 2009-07-01
I don't have it in front of me, but while trying to compile XCI on Ubuntu 8.10, I had what I think is the same error. I clearly remember the part about "Cross compiling", the rest, not positive.

---

### Post by dbaxps on 2009-07-02
> **spiked said:**
> Hi coloured,
I've contacted Xen Support, but no reply yet. I'm trying to install Xen 3.4 on Ubuntu now, because 3.4 has XCI present in it, but otherwise I'm running out of ideas. Any advice/ideas?
Thanks.
Setup Xen 3.4.1 Dom0 on top of Ubuntu 9.04 Server 
via Marc – A. Dahlhaus’s UDEV patch
[http://lxer.com/module/newswire/view/122253/index.html](http://lxer.com/module/newswire/view/122253/index.html)

---

### Post by coloured on 2009-08-04
Ok, I have recently compiled the XCi source again and this time will provide it to everyone to download...
here is the link - it is a bz2 remember to unpack it.
[http://www.filefactory.com/file/ahh3b54/n/rootfs_i686_ext2_bz2]("http://www.filefactory.com/file/ahh3b54/n/rootfs_i686_ext2_bz2")

here is a guide to getting it onto a VT enabled intel based pc.
REMEMBER this wont currently work with anything but an intel video chipset.

12) Burn a live Linux CD, I used this one.  Burn the Ubuntu 9.04 Live CD and put it into a computer you want to install Xen Client on.
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&mirror=&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&mirror=&arch=i386)

13) Once booted into the Ubuntu Live CD, use Gparted and make sure you have 3 Ext2 paritions setup like below.

sda1 = 10gb
sda2 = 10gb
sda3 = 128mb

14) Once that is completed, open up terminal and type…

sudo su
aptitude install lvm2
pvcreate /dev/sda3
vgcreate xenclient /dev/sda3
lvcreate –-name config –-size 12M /dev/xenclient
lvcreate –-name root –-size 100M /dev/xenclient
15) Now, we need that thumbdrive with the rootfs.i686.ext2 on it.  Plug the thumbdrive into your computer, it should mount and pop up on the screen.  Drag and drop the rootfs.i686.ext2 file to the desktop.

16) Go back to your terminal and type…

cd Desktop
dd if=rootfs.i686.ext2 of=/dev/xenclient/root
fsck -f /dev/xenclient/root
resize2fs /dev/xenclient/root
mkfs -t ext2 /dev/xenclient/config
mount /dev/xenclient/root /mnt
mount /dev/xenclient/config /mnt/config
mount –-bind /dev /mnt/dev
mount –-bind /proc /mnt/proc
chroot /mnt /bin/sh
/usr/share/xenclient/install-bootloader /dev/sda3 hd0,1
exit
With any luck, grub will boot you into a grub screen that says “Welcome to XenClient”  It will ask you to login…

xenclient login: root
Press the enter key, its a blank password.

More to come… I now have directions for the next step. I will try getting it working and document it shortly.

*** confirmed *** does not work on non-intel graphics computers.

and the original link - [http://joshlander.com/?p=22]("http://joshlander.com/?p=22")

Please post back here if you figure out how to get a para-virtualized VM up and running on this hypervisor.

and any other information/knowledge you gain :)

---

### Post by damtux on 2009-10-06
Hi [coloured]("http://ubuntuforums.org/member.php?u=377251"),

Thanks for your help on the XCI installation.
I did folow all your steps (Thanks a lot for your root file to download !) but I would be very interested to know if you sucessfully started a VM on your system.
I booted on XCI sucessfully but then in the command line, I can't any way to create VHD with the tool[FONT=monospace] [/FONT]vhd-util as mention in the document :
[http://wiki.xensource.com/xenwiki/XciGettingStarted](http://wiki.xensource.com/xenwiki/XciGettingStarted) 
Please let me know how you made it works 

Thanks a lot

---

### Post by coloured on 2009-10-11
damtux - I have the same problem as you, have you managed to find a solution?
After a little digging around, it seems vhd-util is part of libvhd, I have had a look through the config file and there is no mention of building that package into the client

---

### Post by damtux on 2009-10-12
Hi,
No I don't find anything around vhd-util.
I sucessfully compiled myself the build but I cann't use xenvm (there is nothing in xentop ..) and I don't know how to sucessfully use the --moinotr-dbus true function to have the VM on the screen ...
Is there anyone that sucessfully monitor VM on Xenclient ???
Thanks a lot guys !

---

### Post by coloured on 2009-10-13
This is just an update to this thread and where I am at with all this, basically I am having problems with VT-D... anyone have any answers here..? 
Here is an email I sent to a couple guys who were experiencing the same issues. Basically my VM boots but pci passthrough is borked

```
Hi Guys, sorry for grabbing your email address from the web, but I am having the same problem with VT-D as per this link
[http://article.gmane.org/gmane.comp.emulators.xen.devel/69989](http://article.gmane.org/gmane.comp.emulators.xen.devel/69989)
the VM starts up fine, the screen flickers and thats about it, it seems the VM continues to boot the windows xp cdrom in the background
this is the output of a xenops list_domains after it has started
# xenops list_domains
id |  state |    cpu_time |                                 uuid
 0 |     R  | 83061205715 | 00000000-0000-0000-0000-000000000000
 2 |      H | 19055698780 | 00000000-0000-0000-0000-000000000003

this is the VM's config file
# cat /etc/xen/winxp2.conf
uuid = 00000000-0000-0000-0000-000000000003
hvm = true
acpi = true
apic = true
nx = true
memory = 512
disk = /mnt/xp.img:file:hda:w:disk
disk = /dev/sr0:phy:hdd:r:cdrom
boot = dc
display = intel
pci = 0,bind,0000:00:02.0
nic = model=e1000,id=0,bridge=xenbr0,mac=vm

I will continue to search around to see if I can find some more info relating to this VT-D problem, it could be related to IRQ sharing with the USB devices?
here is a the output of a xenops dmesg ( I have bolded the VT-D stuff)
before I post that here is what is happening at the kernel layer (output from a regular dmesg)

[  182.615072] pciback 0000:00:02.0: seizing device
[  182.615161] pciback 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  182.615170] pciback 0000:00:02.0: PCI INT A disabled

xenops dmesg
(XEN) Bad console= option '/dev/null'
 __  __            _____ _  _    _            _____
 \ \/ /___ _ __   |___ /| || |  / |   _ __ __|___  |
  \  // _ \ '_ \    |_ \| || |_ | |__| '__/ __| / /
  /  \  __/ | | |  ___) |__   _|| |__| | | (__ / /
 /_/\_\___|_| |_| |____(_) |_|(_)_|  |_|  \___/_/

(XEN) Xen version 3.4.1-rc7 (root@mshr.edu.au) (gcc version 4.2.4) Thu Jul 30 12:14:36 CST 2009
(XEN) Latest ChangeSet: unavailable
(XEN) Command line: console=/dev/null dom0_mem=128M iommu=1
(XEN) Video information:
(XEN)  VGA is text mode 80x25, font 8x16
(XEN)  VBE/DDC methods: V2; EDID transfer time: 1 seconds
(XEN) Disc information:
(XEN)  Found 1 MBR signatures
(XEN)  Found 1 EDD information structures
(XEN) Xen-e820 RAM map:
(XEN)  0000000000000000 - 000000000009fc00 (usable)
(XEN)  000000000009fc00 - 00000000000a0000 (reserved)
(XEN)  00000000000e8000 - 0000000000100000 (reserved)
(XEN)  0000000000100000 - 000000007d2afe00 (usable)
(XEN)  000000007d2afe00 - 000000007d2b1ea0 (ACPI NVS)
(XEN)  000000007d2b1ea0 - 000000007e000000 (reserved)
(XEN)  00000000f4000000 - 00000000f8000000 (reserved)
(XEN)  00000000fec00000 - 00000000fed40000 (reserved)
(XEN)  00000000fed45000 - 0000000100000000 (reserved)
(XEN) System RAM: 2002MB (2050360kB)
(XEN) ACPI: RSDP 000E5C10, 0014 (r0 COMPAQ)
(XEN) ACPI: RSDT 7D2C1E40, 0044 (r1 HPQOEM SLIC-BPC 20070718             0)
(XEN) ACPI: FACP 7D2C1EE8, 0074 (r1 COMPAQ BEARLAKE        1             0)
(XEN) ACPI: DSDT 7D2C2427, A370 (r1 COMPAQ DSDT_PRJ        1 MSFT  100000E)
(XEN) ACPI: FACS 7D2C1E00, 0040
(XEN) ACPI: APIC 7D2C1F5C, 0084 (r1 COMPAQ BEARLAKE        1             0)
(XEN) ACPI: ASF! 7D2C1FE0, 0063 (r32 COMPAQ BEARLAKE        1             0)
(XEN) ACPI: MCFG 7D2C2043, 003C (r1 COMPAQ BEARLAKE        1             0)
(XEN) ACPI: TCPA 7D2C207F, 0032 (r1 COMPAQ BEARLAKE        1             0)
(XEN) ACPI: SLIC 7D2C20B1, 0176 (r1 HPQOEM SLIC-BPC        1             0)
(XEN) ACPI: HPET 7D2C2227, 0038 (r1 COMPAQ BEARLAKE        1             0)
(XEN) ACPI: DMAR 7D2C225F, 01A8 (r1 COMPAQ BEARLAKE        1             0)
(XEN) Domain heap initialised
(XEN) Processor #0 6:15 APIC version 20
(XEN) Processor #1 6:15 APIC version 20
(XEN) Processor #2 6:15 APIC version 20
(XEN) Processor #3 6:15 APIC version 20
(XEN) IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
(XEN) Enabling APIC mode:  Flat.  Using 1 I/O APICs
(XEN) Intel VT-d DMAR tables have been parsed.
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Detected 2394.049 MHz processor.
(XEN) VMX: Supported advanced features:
(XEN)  - APIC MMIO access virtualisation
(XEN)  - APIC TPR shadow
(XEN)  - Virtual NMI
(XEN)  - MSR direct-access bitmap
(XEN) HVM: VMX enabled
(XEN) CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
(XEN) Booting processor 1/1 eip 8c000
(XEN) CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
(XEN) Booting processor 2/2 eip 8c000
(XEN) CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
(XEN) Booting processor 3/3 eip 8c000
(XEN) CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
(XEN) Total of 4 processors activated.
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using new ACK method
(XEN) checking TSC synchronization across 4 CPUs: passed.
(XEN) Platform timer is 14.318MHz HPET
(XEN) Brought up 4 CPUs
(XEN) Intel VT-d Snoop Control not supported.
(XEN) Intel VT-d DMA Passthrough not supported.
(XEN) Intel VT-d Queued Invalidation not supported.
(XEN) Intel VT-d Interrupt Remapping not supported.
(XEN) I/O virtualisation enabled
(XEN) I/O virtualisation for PV guests disabled
(XEN) *** LOADING DOMAIN 0 ***
(XEN)  Xen  kernel: 64-bit, lsb, compat32
(XEN)  Dom0 kernel: 32-bit, PAE, lsb, paddr 0x100000 -> 0x67a000
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   0000000079000000->000000007a000000 (28672 pages to be allocated)
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: 00000000c0100000->00000000c067a000
(XEN)  Init. ramdisk: 00000000c067a000->00000000c090ac00
(XEN)  Phys-Mach map: 00000000c090b000->00000000c092b000
(XEN)  Start info:    00000000c092b000->00000000c092b4b4
(XEN)  Page tables:   00000000c092c000->00000000c0938000
(XEN)  Boot stack:    00000000c0938000->00000000c0939000
(XEN)  TOTAL:         00000000c0000000->00000000c0c00000
(XEN)  ENTRY ADDRESS: 00000000c0100000
(XEN) [VT-D]iommu.c:722: iommu_page_fault: iommu->reg = ffff828bfff54000
(XEN) [VT-D]iommu.c:691: iommu_fault_status: Fault Overflow
(XEN) [VT-D]iommu.c:694: iommu_fault_status: Primary Pending Fault
(XEN) [VT-D]iommu.c:676: iommu_fault:DMA Read: 0:1d.1 addr 7d2ce000 REASON 6 iommu->reg = ffff828bfff54000
(XEN) print_vtd_entries: iommu = ffff83007b7ab9e0 bdf = 0:1d:1 gmfn = 7d2ce
(XEN)     root_entry = ffff83007c644000
(XEN)     root_entry[0] = 7af6a001
(XEN)     context = ffff83007af6a000
(XEN)     context[e9] = 101_7d0b7001
(XEN)     l3 = ffff83007d0b7000
(XEN)     l3_index = 1
(XEN)     l3[1] = 7d255003
(XEN)     l2 = ffff83007d255000
(XEN)     l2_index = 1e9
(XEN)     l2[1e9] = 7af6b003
(XEN)     l1 = ffff83007af6b000
(XEN)     l1_index = ce
(XEN)     l1[ce] = 0
(XEN)     l1[ce] not present
(XEN) Dom0 has maximum 4 VCPUs
(XEN) Scrubbing Free RAM: ..................done.
(XEN) Xen trace buffers: disabled
(XEN) Std. Loglevel: Errors and warnings
(XEN) Guest Loglevel: Nothing (Rate-limited: Errors and warnings)
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen
(XEN) Freed 124kB init memory.
(XEN) xen_pminfo: @acpi_cpufreq_cpu_init,HARDWARE addr space
(XEN) CPU 0 initialization completed
(XEN) xen_pminfo: @acpi_cpufreq_cpu_init,HARDWARE addr space
(XEN) CPU 1 initialization completed
(XEN) xen_pminfo: @acpi_cpufreq_cpu_init,HARDWARE addr space
(XEN) CPU 2 initialization completed
(XEN) xen_pminfo: @acpi_cpufreq_cpu_init,HARDWARE addr space
(XEN) CPU 3 initialization completed
(XEN) [VT-D]iommu.c:722: iommu_page_fault: iommu->reg = ffff828bfff56000
(XEN) [VT-D]iommu.c:691: iommu_fault_status: Fault Overflow
(XEN) [VT-D]iommu.c:694: iommu_fault_status: Primary Pending Fault
(XEN) [VT-D]iommu.c:676: iommu_fault:DMA Write: 0:2.0 addr 7d800000 REASON 2 iom
(XEN) print_vtd_entries: iommu = ffff83007b7ab860 bdf = 0:2:0 gmfn = 7d800
(XEN)     root_entry = ffff83007c646000
(XEN)     root_entry[0] = 7af69001
(XEN)     context = ffff83007af69000
(XEN)     context[10] = 0_0
(XEN)     ctxt_entry[10] not present
```

---

### Post by Sanny78 on 2009-12-02
@coloured: You seem the have overcome the problem with not having vhd-util on the system. Do you mind sharing the solution for that so I can overcome the same problem on my install?

Thanks man!

Sander

---

### Post by rcmn on 2010-05-26
So where are we on that topic ? 

Because Citrix came out recently with the XenClient Trial version.

---

