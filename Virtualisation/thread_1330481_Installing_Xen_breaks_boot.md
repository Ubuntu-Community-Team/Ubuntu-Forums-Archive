---
title: "Installing Xen breaks boot"
date: 2009-11-18
forum: Virtualisation
---

### Post by dmgub on 2009-11-18
Installed Ubuntu 9.10 Desktop, 64-bit, from Alternate-Install CD on a new Dell M6400. Dual Hard-drive, configured a /boot partition, also swap, configured most of the drive space as software RAID-0 mount point "/".

Appears to work nicely, configures my Intel Wireless Card, configures my NVidia Graphics card, update packages, reboot for luck, all looks good. 

Now I install Xen (I want to run a Windows VM, Windows-7 to be exact), I tried a couple of different times, but at it's most basic:
[FONT=Courier New]    apt-get install ubuntu-xen-server[/FONT]
Then restart as requested.
The reboot appears to work, see GRUB, GRUB Loading, see the black-and-white Ubuntu logo for a short while. All looking good until...
System falls to a text login prompt - and even worse, the prompt is flashing continuously. If I start typing my login name, the first two characters show up, but subsequent typing doesn't show up. I I just keep going, eventually I get a failed-to-login message,still flashing, still not legible really...
What's up? Suggestions?

---

### Post by sh1ny on 2009-11-19
Xen is no longer supported in Ubuntu. Try KVM.

---

### Post by Mi11z on 2009-11-20
yeah i was just gonna say, he's right.

---

### Post by frankabel on 2009-12-08
So no way to get Xen on karmic??

---

### Post by anandi on 2009-12-10
Hi,

I have been trying to get xen working under 9.10 myself, but had no luck so far. Searching in the forums led me to this thread. I have found many references which talk about people using xen i.e. ubuntu-xen-server (i know its a meta package and installs many other packages), and then using the same.

So there is no way i can get to run xen on 9.10 ? Can someone please confirm this.

---

### Post by frankabel on 2009-12-10
After read a "little" ones can understand few things:

-Ubuntu don't will support xen (xen dom0 kernel) until Linus(note the "s" ;)) support it, all seem that next year this can be happen. The fact that still exist packages for xen hypervisor(useless without a compatible dom0 kernel) and other management tools in recent releases don't mean ubuntu support xen at all. the package that is missing is xen-linux-system-2.6.XXX..

-Exist two path to get xen working on ubuntu, but of course, you are on your own and get ready to kernel compilation etc. :( or at least stolen kernels :) and begin long tests :( to see witch one fix ones of the hypervirsor you had installed

-one path is try to get a dom0 paravirt_ops kernel with a moderm xen hypervisor(>=3.4??) I'm not in this path, yet! anyway... I think that debian testing packages can be good as hypervisor, but still don't sure what kernel can be used, I mean, what is the canonical enough dom0 paravirt_ops kernel??? beside, that kernel work with 3.4 or need 4.0 unstable xen hypervisor??

-another path is try to get a XenLinux(normal and old and a few deprecated xen [http://wiki.xensource.com/xenwiki/XenLinux](http://wiki.xensource.com/xenwiki/XenLinux)) kernel from some where. I get in this path without any advance. I try with the ubuntu xen hypervisor(karmic and hardy) plus the debian xen hypervisor (stable and testing) again the debian stable xenlinux packages ([http://packages.debian.org/lenny/xen-linux-system-2.6.26-2-xen-amd64](http://packages.debian.org/lenny/xen-linux-system-2.6.26-2-xen-amd64)) without any successful, try with lot of grub options, but nothing.

I will research a little more and may be try to compile [http://x17.eu/xen/linux-2.6.31.4-xen-r4.aka.suse-xenified-2.6.31.3-1.1.src.rpm-rebased.patches.by.andrew.lyon.tar.gz](http://x17.eu/xen/linux-2.6.31.4-xen-r4.aka.suse-xenified-2.6.31.3-1.1.src.rpm-rebased.patches.by.andrew.lyon.tar.gz) or maybe install suse :))), seem like opensuse is right now the only distro that support xen


any comment, critics, etc is welcome

I will try to keep this post updated with what I'm doing

ref:
[http://wiki.xensource.com/xenwiki/XenParavirtOps](http://wiki.xensource.com/xenwiki/XenParavirtOps)
[http://wiki.xensource.com/xenwiki/XenDom0Kernels](http://wiki.xensource.com/xenwiki/XenDom0Kernels) 
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)
[http://wiki.debian.org/Xen](http://wiki.debian.org/Xen)
[http://lists.xensource.com/archives/html/xen-users/2009-10/msg00342.html](http://lists.xensource.com/archives/html/xen-users/2009-10/msg00342.html)

---

### Post by binwiederweg on 2010-03-12
> **frankabel said:**
> ubuntu don't will support xen (xen dom0 kernel) until Linus(note the "s" ;)) support it, all seem that next year this can be happen. The fact that still exist packages for xen hypervisor(useless without a compatible dom0 kernel) and other management tools in recent releases don't mean ubuntu support xen at all. the package that is missing is xen-linux-system-2.6.XXX..

Do you have any official statement that support your statement? I am asking because I'd like to state that fact in a seminar paper...

Regards,
Philipp

---

### Post by frankabel on 2010-03-12
If you refer to:

> ubuntu don't will support xen (xen dom0 kernel) until Linus(note the "s" ) support it, all seem that next year this can be happen.

not that I remember, but the rest:

> The fact that still exist packages for xen hypervisor(useless without a compatible dom0 kernel) and other management tools in recent releases don't mean ubuntu support xen at all. the package that is missing is xen-linux-system-2.6.XXX..

is a fact.

Can you pls point me to your paper when you get it ready?

I don't have time right now to continue the research on this topic but I can conclude from recently articles that:

Lot of non enterprise distros are moving to KVM due its inclusion in the kernel mainline make its support cheaper. Just big enterprises distros support Xen, but even some of them (redhat and sel, etc.) are looking to KVM with...lets said why not, preference. I support that in the fact that they are investing( in several forms, collaboration with and even acquisition of projects tied to KVM) on KVM, nevertheless they are obligate to support Xen cause is an already deployed tech, so why such double push, can be that Xen that is the future on Linux?

Cheers
Frank Abel

---

### Post by binwiederweg on 2010-03-12
Hallo Frank,

thank you for your time. I'll do some more research on that topic and let you know what I find out.

Regards,
Philipp

---

### Post by frankabel on 2010-03-14
Definitely an interesting link [http://lists.xensource.com/archives/html/xen-users/2010-03/msg00350.html](http://lists.xensource.com/archives/html/xen-users/2010-03/msg00350.html)

---

### Post by binwiederweg on 2010-03-15
Hey Frank,

thanks for the link. Really exactly what I was looking for.
Even though this is not an official post, it's an indicator of what's going on...

Regards,
Philipp

---

