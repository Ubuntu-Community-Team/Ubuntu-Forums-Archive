---
title: "Ubuntu 14.04 / Xen 4.4 improved VGA passthrough for AMD cards"
date: 2014-04-14
forum: Virtualisation
---

### Post by heiko_s on 2014-04-14
I did some tests with Ubuntu 14.04 / Xen 4.4 regarding VGA passthrough. Here the hardware:

CPU: Intel i7 3930K (supporting VT-d)
M/B: Asus Sabertooth X79 with latest BIOS
dom0 graphics: AMD / ATI 7770
domU graphics: AMD / ATI 6450
dom0 OS: Ubuntu-Gnome 14.04 Beta2 64bit
domU OS: Windows 7 Professional 64bit
dom0 memory: 8GB
domU memory: 8GB
Toolstack: xl
Device model: device_model_version = 'qemu-xen-traditional'

Results:
Aside from some minor glitches like xtightvncviewer not accepting an empty password ](*,) and xvnc4viewer crashing more often than not, the new Xen 4.4 with the 3.13 kernel greatly improved the ability to pass through the AMD HD 6450 graphics card. Now xl can start and restart the domU without causing performance issues, or crashing dom0. It is no more necessary to use the xm toolstack for VGA passthrough.

EDIT 25.4.2014: [B]I tested my AMD HD 7770 with Ubuntu 14.04 (non-beta). First boot with VGA passthrough works fine, but rebooting the Windows domU with VGA passthrough doesn't activate the AMD GPU and gives a code 43 in the Windows Device manager:(.
In short: The guest reboot problem has NOT been solved![/B]

Below is my /etc/xen/guest.cfg file:
```
builder='hvm'
memory = 8192
name = 'win7'
vcpus=6
pae=1
acpi=1
apic=1
on_xend_stop='shutdown'
vif = [ 'mac=00:16:3e:68:e1:01,bridge=xenbr0' ]
disk = [ '/dev/mapper/guests-win7,raw,hda,rw' , '/home/user/ISOs/Win7.iso,raw,hdc,devtype=cdrom' ]
device_model_version = 'qemu-xen-traditional'
boot='cd'
sdl=0
vnc=1
vncpasswd='password'
stdvga=0
serial='pty'
tsc_mode='default'
viridian=1
usb=1
usbdevice='tablet'
gfx_passthru=0
pci=[ '02:00.0', '02:00.1' ]
localtime=1
pci_power_mgmt=1
```

In the past I had serious issues getting this AMD 6450 card passed through. I tried various releases of Linux Mint/Ubuntu 12.04/12.10/13.10 with Xen 4.1.2/4.1.3/4.2/4.3 and only Ubuntu 12.04 with an old kernel and Xen 4.1.2 (the original version) worked with the xm toolstack.

More on the experiments and results can be found [here (Linux Mint 13/Ubuntu 12.04 with Xen 4.1.2)]("http://forums.linuxmint.com/viewtopic.php?f=47&t=163317&start=20#p843410") and [here (Ubuntu 14.04 with Xen 4.4)]("http://forums.linuxmint.com/viewtopic.php?f=47&t=163317&start=20#p846076").

---

### Post by heiko_s on 2014-04-24
Yesterday I tested my AMD HD 7770 card for VGA passthrough, using the final Ubuntu 14.04 LTS release. It turns out that the guest reboot problem hasn't been solved. I can boot with VGA passthrough only once, after that when I reboot I get only a VNC screen and the Windows Device Manager shows a yellow triangle next to the AMD graphics card. See also my edit above.

What a pain in the neck this is!

---

### Post by Shocky_Han on 2014-05-15
hi,

I follows '[Linux Mint Forum - HOW-TO make dual-boot obsolete using XEN VGA passthrough]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013")' and it works.

My setup:
CPU: intel i7-3770
M/B: asrock z77 pro4
[COLOR=#000000]dom0 graphics: intel integrated[/COLOR]
[COLOR=#000000]domU graphics: AMD Radeon HD6750[/COLOR]
[COLOR=#000000]dom0 OS: Ubuntu Server 14.04 + Gnome Desktop + Virtualization[/COLOR]
[COLOR=#000000]domU OS: Windows 7 Professional 64bit (with Catalist Control Center, No GPLPV drivers)[/COLOR]
[COLOR=#000000]dom0 memory: 8GB[/COLOR]
[COLOR=#000000]domU memory: 8GB[/COLOR]
[COLOR=#000000]Toolstack: xl[/COLOR]
[COLOR=#000000]Device model: device_model_version = 'qemu-xen-traditional'

/etc/default/grub:
[/COLOR]```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_XEN="iommu=1 dom0_mem=2048M"

```

/etc/initramfs-tools/modules:
```

xen-pciback passthrough=1 hide=(01:00.0)(01:00.1)

```

/etc/xen/win7.cfg:
```

builder='hvm'
memory = 8192
name = 'windows7'
vcpus=6
pae=1
acpi=1
apic=1
on_xend_stop='shutdown'
on_poweroff='destroy'
on_reboot='restart'
on_crash='restart'
vif = [ 'mac=00:16:3e:68:e1:01,bridge=virbr0' ]
disk = [ 'file:/guest/windows7/disk.img,ioemu:hda,w' , 'file:/guest/windows7/windows7.iso,ioemu:hdc:cdrom,r' ]
device_model_version='qemu-xen-traditional'
boot='dc'
sdl=0
vnc=1
#vncpasswd=''
vnccolsole=0
vncused=0
vncdisplay=2    
stdvga=0
serial='pty'
tsc_mode='default'
viridian=1
usb=1
usbdevice='tablet'
gfx_passthru=0
pci=[ '01:00.0', '01:00.1' ] 
localtime=1
pci_power_mgmt=1
xen_platform_pci=1
pci_msitranslate=1
hpet=1

```

[COLOR=#000000]
Everything goes fine except Windows 7 booting is [/COLOR]seemed a lot slower than normal.
There's no guest reboot problem at all.
But guest has a problem for the Standard VGA Graphics Adapter and I wonder it is normal under VGA passthrough or not.

I hope this helps.

Shocky

---

### Post by heiko_s on 2014-05-19
@Shocky_Han: Sorry for the late reply. Thanks for sharing your success story and configuration. Indeed it helps!

The slower than normal Windows boot time is normal with secondary passthrough. In my system - using a SSD for Windows and Linux - it takes Windows 7 around 20 seconds to get to the login. From there on its fast.

I also tested Ubuntu 14.04 with kvm and I managed to run primary passthrough with my AMD Radeon HD 7770 card, which reduced the boot time as there is no secondary (virtual) graphics adapter. I hope to write a how-to when I become more familiar with kvm and time permit. Still, if you managed to run Xen with VGA passthrough, don't bother switching to kvm.

The yellow triangle next to the Standard VGA graphics adapter is normal, as far as I remember. You can disable the Standard VGA adapter via the Windows Device Manager.

If you have a Linux Mint account, please post the Passmark performance under the thread I linked to - see the end of the how-to. If not, can you post it here? (I try to gather some performance data - if you happen to have a copy of Windows installed natively on your machine, i.e. bare metal, it would be great to compare the performance.)

---

### Post by Shocky_Han on 2014-05-21
@heiko_s,
It's a greate idea collecting some performance data.
Because I don't have any LM account, I upload the passmark base line here. 
This is the only thing I can save in the PerframnceTest 8.0 Evaluation version.
Also I upload my baseline to web and you can see it from [http://www.passmark.com/baselines/V8/display.php?id=24178651031](http://www.passmark.com/baselines/V8/display.php?id=24178651031)
FYI, my overoll rating is 242 and it's very slower than I thought.

---

### Post by heiko_s on 2014-06-29
> **Shocky_Han said:**
> @heiko_s,
It's a greate idea collecting some performance data.
Because I don't have any LM account, I upload the passmark base line here. 
This is the only thing I can save in the PerframnceTest 8.0 Evaluation version.
Also I upload my baseline to web and you can see it from [http://www.passmark.com/baselines/V8/display.php?id=24178651031](http://www.passmark.com/baselines/V8/display.php?id=24178651031)
FYI, my overoll rating is 242 and it's very slower than I thought.

Have been a little busy these days. Your result is indeed not impressive. For starters, using a file instead of LVM does slow down disk I/O performance in the VM, which also helps explain the slow Windows boot time.

However, the most disturbing thing is the graphics performance - something is wrong here. Below are my benchmarks for the AMD 7770 running in a VM under KVM. There shouldn't be much of a difference - if any - for VGA passthrough between Xen and KVM.

[ATTACH=CONFIG]254323[/ATTACH]            [ATTACH=CONFIG]254322[/ATTACH]

The 2D benchmark (summary) is 613, the 3D benchmark is 2147. This is far from your results!

---

### Post by sjhupp on 2014-07-24
Oh, wow, glad I found this thread!
I'm trying to pass through an AMD card under Ubuntu 14.04 server running Xen using xl to Windows7.
Currently I have a primary HD5450 to play with, but if I can get something working I'll whack in a HD7770 secondary to use.
My setup has issues with IOMMU though, so appreciate any help.

Should add I have a gigabyte X58 board with a L5520 cpu, and both should support this.

Have enabled virtualisation in the BIOS, and can see:

simon@cavetroll:~$ sudo dmesg | grep -e DMAR -e IOMMU
[    2.810272] Intel-IOMMU: enabled

Yet Xen doesn't agree:

simon@cavetroll:~$ sudo xl dmesg |grep virtualisation
(XEN) I/O virtualisation disabled

and

simon@cavetroll:~$ cat /proc/cpuinfo| egrep "vmx|svm"
simon@cavetroll:~$

Any suggestions? Feel like I'm failing at the first hurdle!
I did try adding to grub:

# trying to force IOMMU on as hardware does support it
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on"


But I don't have pci-back compiled in the kernel I assume (did you do anything special?)

simon@cavetroll:~$ sudo xl pci-assignable-list
libxl: error: libxl_pci.c:376:libxl_device_pci_assignable_list: Looks like pciback driver not loaded

can modprobe it, and make devices pci-assignable, but still won't work.

Do I need to try something with initramfs next to load, and hide devices first?
I had issues booting Ubuntu, and at one stage had the cpu showing support, but I've since changed some AHCI/legacy settings in BIOS. Could that impact?

Open for any suggestions. Would love to get this working.
Thanks.

---

### Post by Teo_En_Ming on 2014-09-12
Dear heiko_s,

Thank you very much for the information which you have provided. I have got Xen VGA Passthrough to work with my Sapphire AMD Radeon HD 6450. Here are the details:

Software Configuration:
Host operating system dom0: Ubuntu 14.04 LTS
Linux kernel: 3.16.1 (self-compiled)
Xen hypervisor: 4.4.1 (self-compiled)
Guest operating system domU: Windows 7 Ultimate HVM domU
Sapphire AMD Radeon HD 6450 Driver DVD: INSTALLED

Hardware Configuration:
Processor: Intel Core i5-4430 CPU @ 3.00GHz (Quad Core)
Motherboard: Asrock B85M Pro4 LGA 1150 Motherboard
Memory: 32 GB DDR3-1600
PCI-E x16 Display Card: Sapphire AMD Radeon HD 6450 1 GB DDR3
VT-x: Enabled in UEFI BIOS
VT-d: Enabled in UEFI BIOS


I have written detailed and comprehensive installation guides for Xen VGA Passthrough newbies.

If you need the installation guides, you can get them here.

(1) Building and Installing Xen 4.x and Linux Kernel 3.x on Ubuntu and Debian Linux

Download link: [http://www.mediafire.com/view/ok8ps8e4hipssp5/Building_and_Installing_Xen_4.x_and_Linux_Kernel_3.x_on_Ubuntu_and_Debian_Linux_-_Version_2.4_-_REDUCED.pdf](http://www.mediafire.com/view/ok8ps8e4hipssp5/Building_and_Installing_Xen_4.x_and_Linux_Kernel_3.x_on_Ubuntu_and_Debian_Linux_-_Version_2.4_-_REDUCED.pdf)

(2) Xen VGA Passthrough with AMD Display Cards

Download link: [http://www.mediafire.com/view/hrquhznwnooxicn/Xen_VGA_Passthrough_with_AMD_Display_Cards_-_Version_1.6.pdf](http://www.mediafire.com/view/hrquhznwnooxicn/Xen_VGA_Passthrough_with_AMD_Display_Cards_-_Version_1.6.pdf)

You will need to follow the above installation guides in sequence.


Teo En Ming
Singapore

---

### Post by sjhupp on 2014-09-12
Is there any chance of getting this working with nvidia yet (with a standard GTX750 or similar?)
I did have some success with a HD7770 under EXSi and kvm, but nothing with nvidia yet.

---

### Post by Teo_En_Ming on 2014-09-14
Hi,

Please watch the 6-min Youtube video on Xen VGA Passthrough with AMD  Radeon HD 6450 here: [http://www.youtube.com/watch?v=C8ZjddNbQIE](http://www.youtube.com/watch?v=C8ZjddNbQIE)



Software Configuration:

Host operating system dom0: Ubuntu 14.04 LTS
Linux kernel: 3.16.1 (self-compiled)
Xen hypervisor: 4.4.1 (self-compiled)
Guest operating system domU: Windows 8.1 Enterprise HVM domU
Display card driver installed: Catalyst 14.4

Hardware Configuration:

Processor: Intel Core i5-4430 CPU @ 3.00GHz (Quad Core)
Motherboard: Asrock B85M Pro4 LGA 1150 Motherboard
Memory: 32 GB DDR3-1600
PCI-E x16 Display Card: Sapphire AMD Radeon HD 6450 1 GB DDR3
VT-x: Enabled in UEFI BIOS
VT-d: Enabled in UEFI BIOS

--
Yours sincerely,

Teo En Ming
Singapore

---

### Post by heiko_s on 2014-09-15
@sjhupp: You need to make absolutely certain that you enabled VT-d in the BIOS!!! If not, or if only VT-x is enabled, it won't work!

I have written a how-to on VGA passthrough using Linux Mint as the basis. See here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013").

All of the steps should be valid for Ubuntu too. You can find some detailed information there, as well as lots of links to additional sources of information.

The only drawback: I wrote this how-to using the xm toolstack, and for a good reason I believe. While Ubuntu 14.04 and Xen 4.4 improves matters in many ways, there are still plenty of unresolved issues with the xl toolstack that can make VGA passthrough a challenge. I'm currently using LM 16 with Xen 4.3 and the xl toolstack and it works just fine with my Nvidia Quadro 2000 graphics card, but then the Quadro usually behaves nice with VGA passthrough. I also posted the different guest configuration file for the xl toolstack.

While I personally prefer Xen at the moment, you should also consider KVM. See both my Xen how-to and this thread: [http://ubuntuforums.org/showthread.php?t=2229929&page=2]("http://ubuntuforums.org/showthread.php?t=2229929&page=2").

Hope this gives you some idea how to proceed.

---

### Post by heiko_s on 2014-09-15
@Teo_En_Ming: Thanks for your post. I've read your Xen VGA passthrough guides but for me they were a little too advanced. I prefer not to compile my kernel but rather use precompiled standard kernels from Ubuntu or Debian based distributions. My favourite is Linux Mint and since there wasn't a how-to available for that distro (and actually also no useful how-to for Ubuntu), I wrote my own Xen VGA passthrough how-to which can be found here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013").

Xen has a lot going for it, but also a lot of quirks, in particular with regard to Nvidia cards (the non-multi-OS ones; i.e. the non-professional ones). Most of the quirks are actually not Xen's fault, but the vendors strategy to make some extra bucks on expensive pro cards. However, the KVM developers have done a nice job in addressing some of these VGA passthrough issues. For example, Nvidia cards work nicely with a Linux host and KVM while they need extra effort to make them work with Xen on dom0. On the VM side, it seems that KVM seems to gain ground on VGA passthroughs with Nvidia (and AMD), as of late. Unfortunately I still haven't found any really useful KVM documentation except the thread by nbhs at the Arch Linux forum, which I believe is THE source of information on VGA passthrough using KVM.

---

### Post by heiko_s on 2014-09-15
> **Teo_En_Ming said:**
> Hi,

Please watch the 6-min Youtube video on Xen VGA Passthrough with AMD  Radeon HD 6450 here: [http://www.youtube.com/watch?v=C8ZjddNbQIE](http://www.youtube.com/watch?v=C8ZjddNbQIE)



Software Configuration:

Host operating system dom0: Ubuntu 14.04 LTS
Linux kernel: 3.16.1 (self-compiled)
Xen hypervisor: 4.4.1 (self-compiled)
Guest operating system domU: Windows 8.1 Enterprise HVM domU
Display card driver installed: Catalyst 14.4

Hardware Configuration:

Processor: Intel Core i5-4430 CPU @ 3.00GHz (Quad Core)
Motherboard: Asrock B85M Pro4 LGA 1150 Motherboard
Memory: 32 GB DDR3-1600
PCI-E x16 Display Card: Sapphire AMD Radeon HD 6450 1 GB DDR3
VT-x: Enabled in UEFI BIOS
VT-d: Enabled in UEFI BIOS

--
Yours sincerely,

Teo En Ming
Singapore

When I started this thread I was hoping to see some improvements with Xen's compatibility with AMD graphics cards (and perhaps Nvidia cards too). I had a spare AMD 6450 card laying around so I tested with this card. But let's face it: this won't knock any gamers off their chairs.

There may be some VGA passthrough cases for a AMD 6450, but the only practical use I could find for a 6450 is for a XBMC media center application (it works actually nicely with 1080 HD video). For all other applications I found this card to be totally underpowered. Most of the users interested in VGA passthrough would be gamers, as Linux has little to offer compared to MS Windows in that area. I'm using Windows to be able to process photos with Adobe software (it should be to their discredit that I have to suffer Windows, or pay a big premium on Apple hardware). Bottom line: most VGA passthrough users would want to run high(er) end graphics cards on their Windows guest VM.

Some of the Xen users reported success with high-end AMD cards, unfortunately there aren't many Nvidia non-pro cards that work with Xen (yet). Do you have any success stories with Nvidia or higher end AMD cards?

---

### Post by Teo_En_Ming on 2014-09-16
> **heiko_s said:**
> When I started this thread I was hoping to see some improvements with Xen's compatibility with AMD graphics cards (and perhaps Nvidia cards too). I had a spare AMD 6450 card laying around so I tested with this card. But let's face it: this won't knock any gamers off their chairs.

There may be some VGA passthrough cases for a AMD 6450, but the only practical use I could find for a 6450 is for a XBMC media center application (it works actually nicely with 1080 HD video). For all other applications I found this card to be totally underpowered. Most of the users interested in VGA passthrough would be gamers, as Linux has little to offer compared to MS Windows in that area. I'm using Windows to be able to process photos with Adobe software (it should be to their discredit that I have to suffer Windows, or pay a big premium on Apple hardware). Bottom line: most VGA passthrough users would want to run high(er) end graphics cards on their Windows guest VM.

Some of the Xen users reported success with high-end AMD cards, unfortunately there aren't many Nvidia non-pro cards that work with Xen (yet). Do you have any success stories with Nvidia or higher end AMD cards?

Dear heiko_s,
[SIZE=2][FONT=arial]
Kelly Zytaruk from AMD said that AMD Radeon R9 200 family works with Xen VGA Passthrough[/FONT][/SIZE]. Have you bought it yet?

Check out the latest updated Xen VGA Passthrough Tested Adapters wiki page.

[http://wiki.xen.org/wiki/Xen_VGA_Passthrough_Tested_Adapters](http://wiki.xen.org/wiki/Xen_VGA_Passthrough_Tested_Adapters)

Teo En Ming
Singapore

---

### Post by redger on 2014-09-19
I have written a guide to VGA Passhtrough using KVM on Ubuntu 14.04 (Trusty) .... which includes kernel Updates (recommedned but not entirely necessary if you accept screen corruption on the host) and use of LibVirt in unpriveleged mode. It also describes how to set virtualisation up so you can start the VM under your own name (direct Qemu command). The drawbacks are (a) its 16 pages of Open Office "Write" (b) it's a bit raw, needs a good edit and cleanup of layout (c) includes gratuitous instructions for ABI based kernel compile (d) doesn't include much discussion of qemu commands or libvirt xml ... but there are manuals for those

Additionally, I have played with LXC and managed to create "unprivileged" virtual desktops with LXC .... which is very convenient. Have some instructions for that also.

The question is, where to post these "documents" . Any advice ?

---

### Post by Teo_En_Ming on 2014-09-19
> **redger said:**
> I have written a guide to VGA Passhtrough using KVM on Ubuntu 14.04 (Trusty) .... which includes kernel Updates (recommedned but not entirely necessary if you accept screen corruption on the host) and use of LibVirt in unpriveleged mode. It also describes how to set virtualisation up so you can start the VM under your own name (direct Qemu command). The drawbacks are (a) its 16 pages of Open Office "Write" (b) it's a bit raw, needs a good edit and cleanup of layout (c) includes gratuitous instructions for ABI based kernel compile (d) doesn't include much discussion of qemu commands or libvirt xml ... but there are manuals for those

Additionally, I have played with LXC and managed to create "unprivileged" virtual desktops with LXC .... which is very convenient. Have some instructions for that also.

The question is, where to post these "documents" . Any advice ?

You can upload your documents to [https://www.mediafire.com](https://www.mediafire.com)

Teo En Ming
Singapore

---

### Post by redger on 2014-09-19
thanks for the suggestion. My concern is that it might go un-noticed unless it's indexed by major search engines ... which is where "blogs" and fora are effective. Problem is I couldn't find an appropriate place

If I post on Mediafire or Dropbox, would the document by indexed by Google et. al. ?

---

### Post by Teo_En_Ming on 2014-09-20
> **redger said:**
> thanks for the suggestion. My concern is that it might go un-noticed unless it's indexed by major search engines ... which is where "blogs" and fora are effective. Problem is I couldn't find an appropriate place

If I post on Mediafire or Dropbox, would the document by indexed by Google et. al. ?

You might want to send an email to Linux-KVM mailing list and attach your document in the email. In that way, your document would be indexed by Google. This is provided the Linux-KVM mailing list accepts email attachments. But I have not subscribed to Linux-KVM mailing list before.

---

### Post by heiko_s on 2014-09-24
> **redger said:**
> I have written a guide to VGA Passhtrough using KVM on Ubuntu 14.04 (Trusty) .... which includes kernel Updates (recommedned but not entirely necessary if you accept screen corruption on the host) and use of LibVirt in unpriveleged mode. It also describes how to set virtualisation up so you can start the VM under your own name (direct Qemu command). The drawbacks are (a) its 16 pages of Open Office "Write" (b) it's a bit raw, needs a good edit and cleanup of layout (c) includes gratuitous instructions for ABI based kernel compile (d) doesn't include much discussion of qemu commands or libvirt xml ... but there are manuals for those

Additionally, I have played with LXC and managed to create "unprivileged" virtual desktops with LXC .... which is very convenient. Have some instructions for that also.

The question is, where to post these "documents" . Any advice ?

This is great news! I suggest you publish the tutorial in the "Tutorial" section, or here under "Virtualisation". If you publish in the Tutorial section, make sure to start a discussion thread here, with a link to the tutorial. Otherwise it might go unnoticed.

Since your tutorial is long, divide it into several posts. I have done this with my Xen tutorial on Linux Mint [here]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013") and I can't complain about getting unnoticed.

Please use links to information that is not included, or that might come in helpful. For example, a link to a qemu or libvirt manual describing the commands. (Please post them here too, as I've been looking for them.)

Hope to see the how-to soon!

---

### Post by heiko_s on 2014-09-24
> **Teo_En_Ming said:**
> Dear heiko_s,
[SIZE=2][FONT=arial]
Kelly Zytaruk from AMD said that AMD Radeon R9 200 family works with Xen VGA Passthrough[/FONT][/SIZE]. Have you bought it yet?

Check out the latest updated Xen VGA Passthrough Tested Adapters wiki page.

[http://wiki.xen.org/wiki/Xen_VGA_Passthrough_Tested_Adapters](http://wiki.xen.org/wiki/Xen_VGA_Passthrough_Tested_Adapters)

Teo En Ming
Singapore

Thanks for the information. No, I haven't tested them so far, and am not sure if and when I will be able to do. I haven't checked out the xen.org passthrough tested adapters for a while, but hope that users are updating it (my contribution is the Nvidia Quadro 2000 part).

---

### Post by tuxinteger on 2014-12-29
Just a quick finding on the ati pci passthorugh and Xen .

Reduce ram to 6098Gb or less in the config.
Reduce your ram speed to 1333Mhz .

The amd /ati drivers do seem to like any o/c within the host.


You might find it all works !.

The mem limit is somewhat more complex to work around,is this the Intel fx emulation limitation ?.

HTH

---

### Post by tuxinteger on 2015-01-04
> **tuxinteger said:**
> Just a quick finding on the ati pci passthorugh and Xen .

Reduce ram to 6098Gb or less in the config.
Reduce your ram speed to 1333Mhz .


The amd /ati drivers do seem to like any o/c within the host.


You might find it all works !.

The mem limit is somewhat more complex to work around,is this the Intel fx emulation limitation ?.

HTH


Also reduce video card memory clock to 1330Mhz if it is higher as this helps mitigate the atikmdag and driver issues.

---

### Post by redger on 2015-02-26
I finally created a passthrough guide for UEFI Windows guests under KVM & libvirt
[http://ubuntuforums.org/showthread.php?t=2266916&p=13235279#post13235279]("http://ubuntuforums.org/showthread.php?t=2266916&p=13235279#post13235279")

much of the complexity comes from trying to run everything as a normal user (as opposed to root), though it does make for some interesting changes in libvirt and apparmor configurations

gratefulfor any feedback and/or advice

vga passthrough using KVM seems to work best with AMD graphics - NVIDIA's Windows drivers are causing problems ... and the easiest / most stable form is to use UEFI to boot the guest (doesn't mean the host needs to be booted via UEFI) as this avoids the whole legacy VGA mess. It also means that most things can be done with libvirt / virt-manager - even on Ubuntu Trusty LTS

---

### Post by noriss on 2015-09-05
After using 6-7 month VGA passthrough my windows amd drivers boke windows 7. I was using 15.2 beta drivers  because, it was only version that work that the time.

Anyone else having same problem?

hardware:
GPU: ATI Radeon R9 270 DD
CPU: AMD FX 8320
motherboard: Gigabyte GA-990XA-UD3 990X AM3+ ATX

---

