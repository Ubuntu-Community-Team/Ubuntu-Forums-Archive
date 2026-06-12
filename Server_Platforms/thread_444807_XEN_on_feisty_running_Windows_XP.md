---
title: "XEN on feisty running Windows XP"
date: 2007-05-15
forum: Server Platforms
---

### Post by bobdob on 2007-05-15
Anybody out there running Windows XP, Windows XP SP2 or Windows 2003 server in XEN 3.0.3 on Feisty
I have XEN setup on feisty Dom0 with a number of Ubuntu and Debian DomUs all working lovely

But it will not work for any windows version.The install gets as far as the blue "Setup is Starting Windows" screen. Intel VT extensions are enabled and the F5 trick makes no difference.

xm dmesg
(XEN) (GUEST: 43) ata0-0: PCHS=16383/16/63 translation=lba LCHS=1024/255/63
(XEN) (GUEST: 43) ata0 master: QEMU HARDDISK ATA-7 Hard-Disk (8192 MBytes)
(XEN) (GUEST: 43) ata0  slave: Unknown device
(XEN) (GUEST: 43) ata1 master: QEMU CD-ROM ATAPI-4 CD-Rom/DVD-Rom
(XEN) (GUEST: 43) ata1  slave: Unknown device
(XEN) (GUEST: 43)
(XEN) (GUEST: 43) Booting from Hard Disk...
(XEN) (GUEST: 43) unsupported PCI BIOS function 0x0E
(XEN) (GUEST: 43) int13_harddisk: function 15, unmapped device for ELDL=81

>config
kernel = "/usr/lib/xen-ioemu-3.0/boot/hvmloader"
builder = "hvm"
memory = "768"
name = "WindowsXP"
vcpus = "1"
disk = [ 'file:/etc/xen/winxp.img,ioemu:hda,w', 'file:/xen-iso/en_winxp_pro_with_sp2.iso,hdc:cdrom,r' ]
device_model = "/usr/lib/xen-ioemu-3.0/bin/qemu-dm"
ne2000=0
boot = "d"
vnc=1
vncviewer=1
serial='pty'
pae=0
acpi=0
apic=0
vif=['type=ioemu, mac=00:16:3e:01:01:25, bridge=xenbr1']

OR 
disk=['phy:/dev/vg-xen-fs/xen-winxp-test,ioemu:hda,w', 'file:/xen-iso/en_winxp_pro_with_sp2.iso,hdc:cdrom,r']

---

### Post by paperdrip on 2007-05-17
I am also on the same boat without finding any resolution. From the xend.log, I noticed an exception in looking up device number for hdc. But I am not sure if it has anything to do with the hanging.

---

### Post by bobdob on 2007-05-17
actually had'nt noticed that error in my logs, but i see it now, not sure what that means.
DEBUG (blkif:24) exception looking up device number for hdc: [Errno 2] No such file or directory: '/dev/hdc'

---

### Post by m3lmsteen on 2007-05-18
Hi, my HVMXen start but before "Windows License Agreement" gone in black screen/death

my cfg:

kernel = '/usr/lib/xen-ioemu-3.0/boot/hvmloader'
builder = 'hvm'
memory = 512
name = "xen-winxp"
vif = [ 'type=ioemu, bridge=xenbr0' ]
disk = [ 'file:/home/francesco/xen/fsvm/winxp.img,ioemu:sda,w','phy:/dev/hde,ioemu:hdc:cdrom,r' ]
device_model = '/usr/lib/xen-ioemu-3.0/bin/qemu-dm'
boot='d'
sdl=1
vnc=0

my guide: [http://www.planetjoel.com/viewarticle/568/HOWTO%3A+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper](http://www.planetjoel.com/viewarticle/568/HOWTO%3A+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper)

anyone have my problem ?

bye ! :guitar:

---

### Post by m3lmsteen on 2007-05-18
this is my #xen dmesg

(XEN) (GUEST: 29) HVM Loader
(XEN) (GUEST: 29) Detected Xen v3.0.3-0
(XEN) (GUEST: 29) Writing SMBIOS tables ...
(XEN) (GUEST: 29) Loading ROMBIOS ...
(XEN) (GUEST: 29) Loading Cirrus VGABIOS ...
(XEN) (GUEST: 29) Loading VMXAssist ...
(XEN) (GUEST: 29) VMX go ...
(XEN) (GUEST: 29) VMXAssist (Mar 24 2007)
(XEN) (GUEST: 29) Memory size 512 MB
(XEN) (GUEST: 29) E820 map:
(XEN) (GUEST: 29) 0000000000000000 - 000000000009F000 (RAM)
(XEN) (GUEST: 29) 000000000009F000 - 00000000000A0000 (Reserved)
(XEN) (GUEST: 29) 00000000000A0000 - 00000000000C0000 (Type 16)
(XEN) (GUEST: 29) 00000000000F0000 - 0000000000100000 (Reserved)
(XEN) (GUEST: 29) 0000000000100000 - 000000001FFF0000 (RAM)
(XEN) (GUEST: 29) 000000001FFF0000 - 000000001FFFA000 (ACPI Data)
(XEN) (GUEST: 29) 000000001FFFA000 - 000000001FFFD000 (ACPI NVS)
(XEN) (GUEST: 29) 000000001FFFD000 - 000000001FFFE000 (Type 19)
(XEN) (GUEST: 29) 000000001FFFE000 - 000000001FFFF000 (Type 18)
(XEN) (GUEST: 29) 000000001FFFF000 - 0000000020000000 (Type 17)
(XEN) (GUEST: 29) 00000000FEC00000 - 0000000100000000 (Type 16)
(XEN) (GUEST: 29) 
(XEN) (GUEST: 29) Start BIOS ...
(XEN) (GUEST: 29) Starting emulated 16-bit real-mode: ip=F000:FFF0
(XEN) (GUEST: 29)  rombios.c,v 1.138 2005/05/07 15:55:26 vruppert Exp $
(XEN) (GUEST: 29) Remapping master: ICW2 0x8 -> 0x20
(XEN) (GUEST: 29) Remapping slave: ICW2 0x70 -> 0x28
(XEN) (GUEST: 29) VGABios $Id: vgabios.c,v 1.61 2005/05/24 16:50:50 vruppert Exp $
(XEN) (GUEST: 29) HVMAssist BIOS, 1 cpu, $Revision: 1.138 $ $Date: 2005/05/07 15:55:26 $
(XEN) (GUEST: 29) 
(XEN) (GUEST: 29) ata0-0: PCHS=16383/16/63 translation=lba LCHS=1024/255/63
(XEN) (GUEST: 29) ata0 master: QEMU HARDDISK ATA-7 Hard-Disk (10240 MBytes)
(XEN) (GUEST: 29) ata0  slave: Unknown device
(XEN) (GUEST: 29) ata1 master: QEMU CD-ROM ATAPI-4 CD-Rom/DVD-Rom
(XEN) (GUEST: 29) ata1  slave: Unknown device
(XEN) (GUEST: 29) 
(XEN) (GUEST: 29) Booting from CD-Rom...
(XEN) (GUEST: 29) unsupported PCI BIOS function 0x0E
(XEN) (GUEST: 29) int13_harddisk: function 15, unmapped device for ELDL=81
(XEN) (GUEST: 29) KBD: int09h_handler(): unknown scancode read!

---

### Post by ricrac on 2007-05-18
Excerpt from... [http://www.planetjoel.com/viewarticle/568/HOWTO:+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper+Drake](http://www.planetjoel.com/viewarticle/568/HOWTO:+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper+Drake)
...If you do not see a VMXON message then Xen has not detected that VT support and you will not be able to install Windows....

I would not dissuade anyone from using this and helping to get it stable. However,
from my experience stable release Xen is not quite ready for daily use of a Windows client.

It works wonderfully for Linux, and I would recommend it for core use for that purpose.

As of today, the free vmware player is available in Ubuntu repositories. This allows hotplugging USB devices, wacom pressure sensitivity in XP inside of Linux, audio, snapshots, easy remapping of virtual networks and has been stable for quite some time.  

I use one machine with Xen for Linux's and one machine with vmware for Windows both Linux based.

Windows in Xen appears to be working for some but still needs tweaking of the base package installs.  With vmplayer and easyvmx [http://www.easyvmx.com/](http://www.easyvmx.com/) ,  install vmplayer, copy vmx file, start client with cdom in drive, install xp, run.

Vmware server and player are free.  Ubuntu has many components that are not opensource already.

I can't use it for windows because my amd64 is pre-VT.  Is this not an issue anymore?

---

### Post by paperdrip on 2007-05-19
My original plan is to have all the virtualization performed by a single application (Xen in this case). Preventing wasting the resources for 2 application of the same kind. But sounds like I might need to stick with VMWare in this sense.

---

### Post by ricrac on 2007-05-19
You'd want two machines, one for Xen and one for vmware, not both on the same machine.

Right now I'd request everyone use Xen or KVM to test and stabalize it, but for production I would only recommend vmware if you require a win based client.

---

### Post by bobdob on 2007-05-21
have to agree with the production aspect....I eventually removed XEN from my feisty server, installed VMWARE htttp://www.vmware.com/download/server/ a few tweaks, 1 hour later, have windows/ubuntu/debian/knoppix images working on my feisty server ready for production.

..and it is free, so really don't see the point of XEN now, apart from the slight performance gain and the good of the community. 

Might give Xen 3.1 a go in a few weeks when i have time, anybody know when the offical (apt-get) packages for ubuntu will be released ?

---

### Post by paperdrip on 2007-05-22
Good for you. I have just tried to install VMWare Server but not sure why it throws me a seg fault when I try to start a newly created VM instance. It was a breeze to install in the other machine but I am not sure why it has such an issue on my new one.

Maybe I will just get another machine running VMware or forget about Windows totally.

---

### Post by tregeagle on 2007-06-04
Any reason no-one here is suggesting [Virtualbox]("http://www.virtualbox.org/") for running windows. I'm just curious as I'm trying to choose something......  all this just to get round IE6 bugs ... gnnnnn

---

