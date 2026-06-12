---
title: "Welcome : Links to get started with Virtualization"
date: 2007-10-20
forum: Virtualisation
---

### Post by bodhi.zazen on 2007-10-20
[CENTER][IMG]http://www.geekday.com/images/virtualization.jpg[/IMG][/CENTER]

Welcome. As [virtualization]("http://en.wikipedia.org/wiki/Virtualization") is becoming ever more popular we have decided to dedicate a forum to this topic.

Although a comprehensive over view is not possible in this limited space, this sticky hopefully hopefully provide a starting point for those seeking information and/or support.

Last, while I would assume most are familiar with Qemu (including KVM, Virtulabox, and Xen) and VMWare, I would like to bring OpenVZ and VServer to your attention.

[How-to Forge, Virtualization section]("http://www.howtoforge.com/taxonomy_menu/1/43") can be a good source of information. The Ubutu wiki will have Ubuntu specific information.

**[SIZE=4]Contents[/SIZE]**
[LIST=1]
[*]Qemu
[*]KVM
[*]Virtualbox
[*]Xen
[*]VMWare (server)
[*]OpenVZ
[*]Virtuozzo
[*]VServer
[*]General tips
[/LIST]

**[SIZE=4]Appendix[/SIZE]**
[LIST]
[*]Run Ubuntu / LInux on a Window host
[/LIST]

[SIZE=2]*If you have not seen the I,XEN page ...*[/SIZE]

[I,XEN : An OpenSkills guide to Xen installation and use on Suse 9.3]("http://openskills.info/release/i-xen/")

[OpenVZ vx. VServer]("http://www.fsfe.org/it/fellows/rca/from_out_there/from_zero_to_virtualization_linux_vserver_vs_openvz")


_[SIZE=4]Qemu[/SIZE]_

> QEMU is a generic and open source machine emulator and virtualizer.

When used as a machine emulator, QEMU can run OSes and programs made for one machine (e.g. an ARM board) on a different machine (e.g. your own PC). By using dynamic translation, it achieves very good performances.

When used as a virtualizer, QEMU achieves near native performances by executing the guest code directly on the host CPU. A host driver called the QEMU accelerator (also known as KQEMU) is needed in this case. The virtualizer mode requires that both the host and guest machine use x86 compatible processors.Qemu code is used by KVM, Virtualbox, and Xen.

[Home Page]("http://fabrice.bellard.free.fr/qemu/about.html")

_How-tos_
[LIST]
[*]Ubuntu wiki ~ [uwiki]WindowsXPUnderQemuHowTo[/uwiki]
[*]Ubuntu tutorials ~ [Setting up QEMU / KQEMU on Ubuntu 7.04 “Feisty”]("http://ubuntu-tutorials.com/2007/07/04/setting-up-qemu-kqemu-on-ubuntu-704-feisty/")
[/LIST]

_GUI front ends for qemu_ (Click on links ot go to home pages)
> 
[LIST]
[*][Q is a Mac OS X port]("http://www.kju-app.org/kju/") of QEMU with a nice GUI.
[*][QEMU Manager]("http://www.davereyn.co.uk/about.htm"), a GUI for the Windows port of QEMU.
[*][QEMU Launcher]("http://projects.wanderings.us/qemu_launcher"), a GTK front end for QEMU on Linux.
[*][QEMoon]("http://qemoon.org/"), a QEMU gui frontend for Linux and Windows in Java using the Eclipse framework.
[*][qemudo]("http://qemudo.sourceforge.net/"), QEMU Web Interface.
[*][QtEmu]("http://qtemu.org/"), a graphical user interface for QEMU written in Qt4 for Linux and Windows.
[/LIST]
[Qemu forums]("http://qemu-forum.ipi.fi/index.php")

**Gutsy (guest) bug fix** : [http://ubuntu-tutorials.com/2007/07/04/installing-ubuntu-710-gutsy-tribe-2-in-qemu-bug-fix/](http://ubuntu-tutorials.com/2007/07/04/installing-ubuntu-710-gutsy-tribe-2-in-qemu-bug-fix/)


_[SIZE=4]KVM (Kernel Virtual Machine)[/SIZE]_

> KVM (for Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V). It consists of a loadable kernel module, kvm.ko, that provides the core virtualization infrastructure and a processor specific module, kvm-intel.ko or kvm-amd.ko. KVM also requires a modified QEMU although work is underway to get the required changes upstream.

Using KVM, one can run multiple virtual machines running unmodified Linux or Windows images. Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter, etc.

The kernel component of KVM is included in mainline Linux, as of 2.6.20.

KVM is open source software.[Home page]("http://kvm.qumranet.com/kvmwiki")

_How-to_
[LIST]
[*][Ubuntu wiki KVM]("https://help.ubuntu.com/community/KVM")
[*][How to KVM (KVM wiki)]("http://kvm.qumranet.com/kvmwiki/HOWTO")
[/LIST]


_[SIZE=4]Virtualbox[/SIZE]_

> Innotek VirtualBox is a family of powerful x86 virtualization products for enterprise as well as home use. Not only is VirtualBox an extremely feature rich, high performance product for enterprise customers, it is also the only professional solution that is freely available as Open Source Software under the terms of the GNU General Public License (GPL). See "About VirtualBox" for an introduction; see "innotek" for more about our company.

Presently, VirtualBox runs on Windows, Linux and Macintosh hosts and supports a large number of guest operating systems including but not limited to Windows (NT 4.0, 2000, XP, Server 2003, Vista), DOS/Windows 3.x, Linux (2.4 and 2.6), and OpenBSD.

VirtualBox is being actively developed with frequent releases and has an ever growing list of features, supported guest operating systems and platforms it runs on. VirtualBox is a community effort backed by a dedicated company: everyone is encouraged to contribute while innotek ensures the product always meets professional quality criteria.[Home page]("http://www.virtualbox.org/")

_How to_
[LIST]
[*][Ubuntu Forums how to Virtualbox]("http://ubuntuforums.org/showthread.php?t=340113")
[*][UDSF How-to Virtualbox](http://gaming.gwos.org/doku.php/udsf:virtualbox)
[/LIST]

[Virtualbox Users Manuel (PDF)]("http://virtualbox.org/wiki/Downloads") *See the "User manual"*

[Virtualbox Forums]("http://forums.virtualbox.org/")

Virtualbox on a live CD: [MCNLive VirtualCity]("ftp://ftp.belnet.be/pub/mirror/urpmidev.mandrakeclub.nl/mcnlive/VirtualCity/"). Based on Mandriva, KDE desktop, Virtualbox Open source edition.

[[IMG]http://img525.imageshack.us/img525/4057/51233673jl8.th.png[/IMG]]("http://img525.imageshack.us/my.php?image=51233673jl8.png")

[MCN Live Home Page]("http://www.mcnlive.org/mcnlive.htm")



_[SIZE=4]Xen[/SIZE]_

> The XenSource v4 Product Family enables businesses to deploy high-performance Windows and Linux virtual machines rapidly and easily, and to manage them and their related storage and networking resources from a single easy-to-use management console.

The family includes three virtualization products that are fully compatible, with additional capacity and features enabled by license key. The products include:

[LIST]
[*]XenExpress™: a free starter package for bringing virtualization to every server
[*] XenServer™: high-performance rich-featured server virtualization with multi-server management, with capacity for most business-critical workloads
[*] XenEnterprise™: a powerful platform managing virtualization as a flexible aggregated pool of compute and storage re sources, for dynamic managed virtualization environments for the enterprise.
[/LIST]

The foundation of the XenSource v4 Family is the open source Xen™ hypervisor, an open, proven and fully supported engine for server virtualization.The Xen [Home page]("http://www.xensource.com/overview/Pages/overview.aspx") includes an "overview" of virtualization on a series nicely formatted pages. 

[Open source Home page]("http://www.xensource.com/Pages/DownloadProducts_4.0.0.aspx")

Xen is available in the Ubuntu repositories, and there is a metapackage available as well : [ubuntu-xen-server]("http://packages.ubuntu.com/feisty/base/ubuntu-xen-server") 

_How-to_
[LIST]
[*][Xen Ubuntu wiki]("https://help.ubuntu.com/community/Xen")
[*][Howto Forge : The Perfect Xen Setup For Debian And Ubuntu]("http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu")
[*][Howto forge : Installing Xen On An Ubuntu Feisty Fawn Server From The Ubuntu Repositories]("http://www.howtoforge.com/ubuntu_7.04_xen_from_repositories")
[*][Howto Forge : Managing Xen With Xen-Tools, Xen-Shell, And Argo]("http://www.howtoforge.com/xen_tools_xen_shell_argo")
[*][Howto Forge : Xen With Graphical User Interface On A Fedora 7 Desktop]("http://www.howtoforge.com/xen_gui_fedora_7_desktop")
[/LIST]

Live CD: The Xen project no longer maintains a live CD. There are tow independent projects, [Xenoppix]("http://unit.aist.go.jp/itri/knoppix/xen/index-en.html") which was renamed [VMKnopix]("http://unit.aist.go.jp/itri/knoppix/vmknoppix/index-en.html"). *Current VMKNOPPIX includes Xen 3.1.0 for x86 and x86_64*. 

Wiki: [Xen wiki]("http://wiki.xensource.com/xenwiki/")

Forums: The Xen project maintains forums for [commercial customers]("http://commercial%20customers"). Support of open source Xen is available via [Xen mailing lists]("http://lists.xensource.com/"). Last, there is a [Nabble Xen forum]("http://www.nabble.com/Xen-f935.html").


_[SIZE=4]VMWare (server)[/SIZE]_

> Optimize and manage your IT infrastructure, from the desktop to the data center, by virtualizing your computing, storage and networking systems with VMware software. VMware products provide enterprise-class virtual machines that increase server and other resource utilization, improve performance, increase security and minimize system downtime, reducing the cost and complexity of delivering enterprise services. By leveraging your existing technology, VMware enables the roll out of new applications with less risk and lower platform costs.While not Open Source, VMWare has made contributions to the open source community and VMWare server is freely available, although you need to register with VMWare to obtain a serial number.

[Home page]("http://www.vmware.com/")

[VMWare : Overview of Virtualization]("http://www.vmware.com/virtualization/")

_How-to_
[LIST]
[*][Ubuntu wiki ~ VMWare Server]("https://help.ubuntu.com/community/VMware/Server")
[*][Ubuntu wiki ~ How to install VMWare tools]("https://help.ubuntu.com/community/VMware/Tools")
[*][Howto Forge : VMware Server on Feisty (7.04)]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto")
[*]Igor website ~ [VMWare on Gutsy (7.10)]("http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html")
[/LIST]

[VMWare Communities (forums)]("http://communities.vmware.com/index.jspa")


_[SIZE=4]OpenVZ[/SIZE]_

> OpenVZ is an operating system-level virtualization technology based on the Linux kernel and operating system. OpenVZ allows a physical server to run multiple isolated operating system instances, known as Virtual Private Servers (VPS) or Virtual Environments (VE).

As compared to virtual machines such as VMware and paravirtualization technologies like Xen, OpenVZ is limited in that it requires both the host and guest OS to be Linux (although Linux distributions can be different in different VEs). However, OpenVZ claims a performance advantage; according to its website, there is only a 1-3% performance penalty for OpenVZ as compared to using a standalone server[1]. An independent performance evaluation[2] confirms this.

OpenVZ is a basis of Virtuozzo, a proprietary software product provided by SWsoft, Inc. OpenVZ is licensed under the GPL version 2.

The OpenVZ is divided into a custom kernel and user-level tools.[Home page]("http://openvz.org/")
[Interview with OpenVZ Project Manager Kir Kolyshkin]("http://www.montanalinux.org/openvz-kir-interview.html")

_How-to_ * The preferred base seems to be Centos (you can install on Fedora or Ubuntu/Debian, but you may need to use an older kernel).
[LIST]
[*][**How to : OpenVZ Ubuntu Host**]("http://ubuntuforums.org/showthread.php?t=617225")
[*][openvz on Debian 4.0]("http://debian.systs.org/howto/install-openvz-on-debian-etch/")
[*][OpenVZ On Debian Etch For Webservers]("http://www.howtoforge.com/debian_etch_openvz") * This is a very nice guide.
[*][Howto Forge : The Perfect Setup - OpenVZ with CentOS 4.4]("http://www.howtoforge.com/openvz_centos4.4")
[*][Ubuntu forums ~ HOWTO: install openvz]("http://ubuntuforums.org/showthread.php?t=492064")
[*][ OpenVZ wiki, Ubuntu guest]("http://wiki.openvz.org/Ubuntu_template")
[*][Linux.com :: A guide to running OpenVZ]("http://www.linux.com/articles/114214")
[/LIST]

_Screencasts_
[LIST]
[*][ Montana Linux Intro to OpenVZ]("http://www.montanalinux.org/openvz-intro-video.html")
[*][Montana Linux Migration of an installed OS -> OpenVZ]("http://www.montanalinux.org/openvz-live-migration-demo.html")
[/LIST]

You can download a VM from OpenVZ:
[LIST]
[*][OpenVZ OS templates]("http://download.openvz.org/template/precreated/")
[*][Commuinity submitted OS templates]("http://download.openvz.org/contrib/template/precreated/")
[/LIST]

Or [Make your own]("http://wiki.openvz.org/VE_creation") * Make a [template cache]("http://wiki.openvz.org/OS_template_cache") first.

[OpenVZ wiki]("http://wiki.openvz.org/Main_Page")

[OpenVZ forums]("http://forum.openvz.org/")

[Home page Openvz Live CD]("http://www.livedistro.org/release-announcements/gnu/linux-releases/openvz-live-cd-2007-01-04")

[Download page, Knoppix or Centos base]("http://download.openvz.org/livecd/")

Screen shot: (Knoppix live cd, Booting)
[[IMG]http://img145.imageshack.us/img145/1054/29867847yw6.th.png[/IMG]]("http://img145.imageshack.us/my.php?image=29867847yw6.png")


_[SIZE=4]Virtuozzo[/SIZE]_

* Virtuozzo is built on OpenVZ

> SWsoft Virtuozzo is a patented OS virtualization solution. Virtuozzo creates isolated virtual environments (VE) or containers on a single physical server and OS instance. Compared to other virtualization technologies, Virtuozzo offers the highest levels of density, performance and manageability.

[LIST]
[*]Intelligent Partitioning - Division of a server into as many as hundreds of VEs with full server functionality.
[*]Complete Isolation - VEs are secure and have full functional, fault and performance isolation.
[*] Dynamic Resource Allocation - CPU, memory, network, disk and I/O can be changed without re-booting.
[*] Live Migration - Business continuity capabilities including live migration ensure data is available and recoverable.
[*] Mass Management - Suite of tools and templates for automated, multi-VE and multi-server administration.
[/LIST]
[Home page]("http://www.swsoft.com/en/products/virtuozzo/")

[Linux.com :: Review: Virtuozzo for Linux 3.0]("http://www.linux.com/articles/114151")[INDENT]>  Summary

Any business or organization that's looking at virtualization should put Virtuozzo at the top of the list. It's a really powerful solution that's relatively simple to administer and use.

Virtuozzo is not the same type of solution as VMware Server or ESX. Since Virtuozzo approaches virtualization differently, you don't have the same operating system flexibility that you'd have with VMware Server -- want to run FreeBSD, Linux, and Windows on the same machines? Then Virtuozzo isn't the offering for your organization. Want to use a virtualization solution that helps partition servers into multiple Linux VPSes, and makes things much easier to manage? Then I'd recommend checking out Virtuozzo when you evaluate solutions.

If you're an "open source at all costs" type of person, take a look at SWsoft's OpenVZ instead. OpenVZ has a subset of the features included with Virtuozzo -- you can still run multiple guests on a single host, and it offers much of the same functionality in terms of QoS features, but it lacks the GUI tools and utilities that make it really easy to manage Virtuozzo.[/INDENT]There is a trial version but this seems to be commercial software.


_[SIZE=4]VServer[/SIZE]_

From the Ubutu wiki :
> The [Linux VServer Project]("http://linux-vserver.org/Welcome_to_Linux-VServer.org") provides multiple Linux environments running inside a single Linux kernel.

You can think of it as a bit like running a new system inside a chroot, but with a different host name and IP address, a de-fanged root user, and configurable resource management. This is a similar feature to jails on FreeBSD and containers on Solaris 10+.

VServers are a different approach to the popular [XEN Hypervisor]("http://www.citrixxenserver.com/Pages/default.aspx"); with XEN you end up with a kernel for each virtual server; VServers do not. So, with VServer you have less (virtually no) overhead, on the other hand you also have fewer features - it is currently impossible to have a VServer with a different time set to the host system, for instance. However it is possible to run a different time zone, as that is a purely user-space feature. The design of UNIX in general mean that for the vast majority of applications, this virtualisation technique is perfectly adequate.

Note that Xen and VServer are orthogonal approaches - that is, it is perfectly possible and sometimes even sensible to run Xen virtual machines on a Linux system, then Linux VServers within those Xen machines. [Home page]("http://linux-vserver.org/Overview")
[VServer FAQ]("http://linux-vserver.org/Frequently_Asked_Questions")

_How-to_
[LIST]
[*]Ubuntu wiki ~ [uwiki]VServer[/uwiki]
[*][Vserver wiki]("http://linux-vserver.org/Installation_on_Ubuntu")
[*][Linux-VServer]("http://wiki.u32.net/index.php?title=Linux-VServer") ~ Installation walk through and performance tweaks
[*][Howto Forge : Linux-Vserver on Debian Testing (Etch), the easy way]("http://www.howtoforge.com/linux_vserver_debian_etch")
[*][Howto Forge : Linux-Vserver on Debian Sarge]("http://www.howtoforge.com/linux_vserver_debian")
[/LIST]


_[SIZE=4]General Tips[/SIZE]_

[LIST]
[*][uwiki]SeamlessVirtualization[/uwiki]
[*]_Portable machines_ Qemu is available across platforms and itis possible to install a machine onto a flash drive thus giving access to a portable machine. There are several options. For example you can runn a light version on Linux on Qemu within Linux/OSX/Windows (I suggest DSL or Puppy)

[How To: Run A Portable Puppy Linux Install On Any Computer]("http://blog.wired.com/monkeybites/2007/10/how-to-run-a-po.html")

[http://www.erikveen.dds.nl/qemupuppy/]QEMU-Puppy : A Personal Portable Computer]("http://www.erikveen.dds.nl/qemupuppy/%5DQEMU-Puppy%20:%20A%20Personal%20Portable%20Computer")

Simplepup is 81 Mb an comes with XFCE : [Wimplepup-0.3.1.iso]("http://www.puppylinux.org/user/downloads.php?cat_id=2&download_id=46")

You can use larger distros : See [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) for additional information and how-to's.
 for example :
[LIST]
[*][Gutsy (Ubuntu 7.10) on a flash drive]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") * See the link below to add qemu
[*][Run Ubuntu within windows]("http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/") *Can be adapted to Linux
[/LIST]
 
[*]_Booting your windows partition_: Currently this is, IMO, at best in Beta testing. This link may help : [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)
[/LIST]


[SIZE=4]**Windows Host**[/SIZE]

Options:
[LIST=1]
[*]Qemu
[*]VirtualBox
[*]VMWare
[*]Colinux
[*]Cygwin
[/LIST]


_[SIZE=2]Qemu[/SIZE]_

Qemu runs in Windows and a very easy introduction is DSL. The "Embeded" version includes qemu.

[Run (Damn Small) Linux on Windows]("http://www.tuxs.org/dslwin.htm")

There are graphical launchers for qemu as well :

[Qemu Manager]("http://www.davereyn.co.uk/")


_[SIZE=2]Virtual Box[/SIZE]_

Virtual Box runs on Windows and may be easier to use.

[[COLOR=red]aysiu[/COLOR]]("http://ubuntuforums.org/member.php?&u=21941") maintains a nice how-to run Ubuntu in Virtual Box (on Windows) [Here (psychocats)]("http://www.psychocats.net/ubuntu/virtualbox") 


_[SIZE=2]VMWare[/SIZE]_

VMWare is a mature product and there are a number of options.

[Here]("http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware") is a tutorial to install VMWare server + an Ubuntu guest.


_[SIZE=2]Colinux[/SIZE]_

[IMG]http://www.colinux.org/images/smalllogo.png[/IMG]

[Colinux]("http://www.colinux.org/") allows you to run Linux within Windows. Linux will run at near native speed.

[How to Colinux]("http://roth.textdriven.com/other/colinux/guide.php")


_[SIZE=2]Cygwin[/SIZE]_

[IMG]http://www.cygwin.com/cygwin-icon.gif[/IMG]

[Cygwin]("http://www.cygwin.com/") is a Unix like environment for windows. It includes a X server (yes, you can ssh -X to a windows box with Cygwin)

[How to install Cygwin]("http://www.physionet.org/physiotools/cygwin/")

---

### Post by ~~Tito~~ on 2007-10-20
Virtual Box:
I would like to add, make sure you install guest additions after you update to 1.52(downloading the deb from the Virtual box website and just installing it, it will update automatically and no data will be lost.) When you maximize it you don't have to go full screen and you can move the mouse in and out with out laggs (1gb+RAM for better stability).

---

### Post by markba on 2008-01-21
Link to "Qemu Launcher" is not working anymore. 
This is a working one: [https://gna.org/projects/qemulaunch/](https://gna.org/projects/qemulaunch/)

---

### Post by bodhi.zazen on 2008-01-21
> **markba said:**
> Link to "Qemu Launcher" is not working anymore. 
This is a working one: [https://gna.org/projects/qemulaunch/](https://gna.org/projects/qemulaunch/)

Thanks for the heads up.

This is the qemu-launcher home page : [http://projects.wanderings.us/qemu_launcher](http://projects.wanderings.us/qemu_launcher)

*link updated*

---

### Post by aBitLater on 2008-02-06
if you're using the howto at: 
[https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM")

then also, you might need to sudo modprobe tun, in addition to modprobe kvm-intel or modprobe kvm-amd

and change the following in your interfaces file (if you're configuring the advanced networking "Virtual NICs on VDE, VDE Tap'd to Host, Tap NATed to Outside" section)

```
post-down kill -s HUP `cat /var/run/vde_switch.pid`
```

change to:

```
post-down kill -s HUP $(cat /var/run/vde_switch.pid)
```

If this helps you, click my thanks ribbon / medal, so I can start looking cool in the ubuntu forums :) hehehe

---

### Post by aBitLater on 2008-02-06
if you're getting core dumps, try setting up with acpi (don't use --no-acpi). Then after you install your guest OS, search google on disabling power management for whatever operating system you use, and add the --no-acpi back in to the kvm command line.

If you're an uber-noob like me, you need to add quotes to your panel launcher command line:
```

gksu "vdeq kvm -hda /home/brianphillips/windows.img -boot c -cdrom /dev/cdrom -net nic -net vde -m 512"
```

Of course, make the memory what you want (-m), and this example assumes a dos or windows type guest OS is what you're launching.  gksu gives the windows that requires the su password.

---

### Post by Belak on 2008-02-20
Sorry about the little things, but you spelled InnoTek wrong.

You left off the first 'i'

"nnotek VirtualBox is a family of powerful x86 virtualization products"

---

### Post by bodhi.zazen on 2008-02-20
> **Belak said:**
> Sorry about the little things, but you spelled InnoTek wrong.

You left off the first 'i'

"nnotek VirtualBox is a family of powerful x86 virtualization products"

Thanks, fixed

---

### Post by jingo811 on 2008-03-28
Not sure if it's already posted but this website has a nice Tech Comparison chart with some good explanations about this subject.
[http://virt.kernelnewbies.org/TechComparison](http://virt.kernelnewbies.org/TechComparison)

---

### Post by Ghuloomo on 2008-07-28
Thanks guys.. i just needed this badly.. I'm trying to setup a windows xp on my ubuntu so i install Sony Vegas on it.. I waned to go for VMWARE but i guess it's not free
I'm going for VirtualBox.. any suggestions?

---

### Post by bodhi.zazen on 2008-07-29
> **Ghuloomo said:**
> Thanks guys.. i just needed this badly.. I'm trying to setup a windows xp on my ubuntu so i install Sony Vegas on it.. I waned to go for VMWARE but i guess it's not free
I'm going for VirtualBox.. any suggestions?

VMWare server is free of charge.

---

### Post by axel206 on 2008-08-12
Hey everyone! Anyone intrested can check this guide also. :)

[How to install Ubuntu Linux on Windows using VirtualBox]("http://www.my-guides.net/en/content/view/112/26/")

---

### Post by julie2008 on 2008-10-01
virtualization is interesting topic.it deals with multimedia.it is essential.
_________________________________________________________________
[Sending flowers to chicago](http://www.florist-flowers-roses-delivery.com/illinois/chicago_il.html) [low rate loans](http://www.cheaponline-loans.co.uk/) [vilafranca del penedes](http://www.vilafrancadelpenedes.com) [download ringtones](http://www.myringtoneshub.com/)

---

### Post by peter.faller on 2009-12-18
No mention of User Mode Linux, even though it is available in Ubuntu?

---

