---
title: "Quick boot Linux that loads a hypervisor once booted"
date: 2009-06-30
forum: Virtualisation
---

### Post by spiked on 2009-06-30
Hey guys,

  I've got a couple of questions.

  Do you know of any Linux distros or hacked Linux versions which can : 1) boot up soon, and 2) once done booting, can load another OS in the background(I need it to be a hypervisor like xen, which can itself pull up a Windows or Linux image) ?

  I know of XCI, which is a xen hypervisor for client devices, that can be installed on most Linux distros. But are there any others out there? (And if anyone has any info on the performance of XCI, I would really appreciate it, can't find any online.)

  I'm quite new to Linux and Ubuntu Forums, so if this post is missing some info, please let me know. Any info will be greatly appreciated. I tried finding out info online, but there really isn't much about this that is readily available.

  If this isn't the right place for this post, could anyone redirect me to the right category? 

Thanks in advance.

Running: Ubuntu 9.04 (no dual boot)
Intel(R) Pentium(R) M processor 1.73GHz
1 GB RAM

---

### Post by bodhi.zazen on 2009-06-30
1. Openvz - See [Proxmox](http://pve.proxmox.com/wiki/Main_Page) OpenVZ will not do windows or BSD though.

2. Minimal install + KVM  + manager of choice (virt-manager, Convirt, etc).

---

### Post by juancarlospaco on 2009-06-30
**JeOS + KVM + SSH** on node

**Convirt** on Centralized Console

*you can build these with VM-Builder *:)

---

### Post by bodhi.zazen on 2009-06-30
Last time I looked JEOS was 32 bit and all KVM enabled processors are 64 bit so why not the 64 bit minimal CD ?

---

### Post by spiked on 2009-07-01
Thanks for the replies guys. But one problem here is that my laptop doesn't have hardware virtualization built in.. No Intel-VT on it. And KVM requires HW Virtualization, right.. So KVM's out of the picture. OpenVZ's gonna be my last resort, since it doesn't do Windows. 
I'm having a lot of trouble installing XCI on Ubuntu 9.04, seems noone's documented a successful installation online. 

Just in case anyone knows about this, the following error occurs after doing a make, (after installing all the programs required, so no dependency problems): (XCI running on Ubuntu 9.04) 

..... 
checking for getpeerucred... no 
checking for getpeereid... no 
checking abstract socket namespace... configure: error: cannot run test  program while cross compiling 
See `config.log' for more details. 
make: ***  [/home/spike/build.git/build/build/build_i686/dbus-glib-0.72/.configured]  Error 1 

There are about 40 different 'config.log's in the xen folder, and the path for this particular config.log is not given.

There are some solutions posted online for this error, but no luck trying them so far.

There's one person online who says he's installed XCI on Linux, but that's on Debian Lenny; I checked if the same steps might work on Ubuntu, but it didn't (gave the same cross compiling error above).

I've contacted Xen Support, but no reply yet. I'm trying to install Xen 3.4 on Ubuntu now, because 3.4 has XCI present in it, but otherwise I'm running out of ideas. Any advice/ideas?

Thanks.

---

### Post by spiked on 2009-07-01
Turns out there are a couple of added requirements now.. :)

The hypervisor has to be able to boot up both Windows and Linux images.. So OpenVZ is now out. 

No hardware virtualization support is present.. So anything that depends on Intel VT or AMD-v is gone.
Another option that I was considering was Oracle VM - but they say that without hardware support, they only support Enterprise Linux 4 and 5, no Windows.. So I guess even that's out.

Any ideas, anyone? I'm fast running out of them, for sure. But from what I see, XCI seems to be my best bet, assuming that it builds successfully on my machine, which it isn't, yet.

Thanks a lot.

---

### Post by juancarlospaco on 2009-07-01
> **bodhi.zazen said:**
> Last time I looked JEOS was 32 bit and all KVM enabled processors are 64 bit so why not the 64 bit minimal CD ?

**[SIZE="3"]No.[/SIZE]**
The NEW JeOS, 9.04 version of JeOS, check ubuntu server docs at ubuntu.com

---

### Post by bodhi.zazen on 2009-07-01
> **juancarlospaco said:**
> **[SIZE=3]No.[/SIZE]**
The NEW JeOS, 9.04 version of JeOS, check ubuntu server docs at ubuntu.com

Ah, thanks for the update on that. +1 on JEOS then.

---

### Post by bodhi.zazen on 2009-07-01
Well, looking at the server page and mirrors , I can not find a 64 bit JEOS.

All the JEOS .iso images are 32 bit, for 64 bit it is a minimal install as I suggested, either from the server install CD or use the minimal CD.

The minimal CD is a smaller download and is a net install, so no 700 Mb download only to have another 400 mb of updates.

> 
**With version 8.10:**

  Either: 
 
[LIST]
[*]Download the [server ISO image]("http://www.ubuntu.com/getubuntu/download"), boot from it, press F4 on the first screen and select "Install a minimal virtual machine",
[*]Or create your virtual machine using python-vm-builder (see [tutorial]("https://help.ubuntu.com/community/JeOSVMBuilder")).
[/LIST]
So , yes there is a 32 bit installer for JEOS, which has a number of features including a customized kernel, but for 64 bit Arch it is simply a minimal install (the 64 bit kernel is already optimized, so, unlike the 32 bit version, no need for a custom kernel).

And JEOS is optimized for virtualization, ie to be run as a guest, not host. It does not matter so much on 64 bit but there is a difference on the 32 bit version where there are differences and so if you run JeOS as a HOST on 32 bit your performance *may* be suboptimal.

So again, for KVM (64 bit host) do a minimal install from either the server CD or the minimal CD (not JeOS).

For the guest you can do 32 bit (JEOS) or 64 bit minimal install (the general consensus I have seen is 32 bit guests are lighter and faster).

---

### Post by juancarlospaco on 2009-07-01
**[9.04 JeOS & VM Builder]("https://help.ubuntu.com/9.04/serverguide/C/jeos-and-vmbuilder.html")**

*VMWare people uses these...*

Utils:

[2Mb ful featured Free web-based file manager]("http://www.ajaxplorer.info/about/")

[700Kb X Server]("http://www.pps.jussieu.fr/~jch/software/kdrive.html")

:)

---

### Post by bodhi.zazen on 2009-07-01
> **juancarlospaco said:**
> **[9.04 JeOS & VM Builder]("https://help.ubuntu.com/9.04/serverguide/C/jeos-and-vmbuilder.html")**

*VMWare people uses these...*
:)

We are talking apples and oranges here.

Your posts are in regards to JEOS as a **guest** and they are somewhat accurate, although incomplete in terms of 64 bit guests. You can use vmbuilder to install "JEOS", 32 or 64 bit.

However ...

The OP is asking about what to install on the host. Or are you suggesting the OP use vmbuilder to install 64 bit JEOS on the host ?

And you seem to be missing this point as well.

Last, as I said earlier, there is no 64 bit JEOS .iso. If you do not wish to use vmbuilder and prefer to install a minimal 64 bit guest from an iso , you need to use the minimal cd or server cd, there is no 64 bit JEOS cd.

Last I think you are also missing JEOS is a "custom spin" on a 32 bit guest. It is a minimal install + a custom 32 bit kernel + some vmware packages (such as vmmouse) which is why the vmware people use it. On a 64 bit guest is simply a minimal install, and not a custom spin.

---

### Post by juancarlospaco on 2009-07-01
These VMWare packages still present in Ubuntu Repos, VMWare employees uses these version,
i see that at an IT presentation of VMWare inc, past month.

*The concept of VM-Builder is to create custom spins too.*

---

