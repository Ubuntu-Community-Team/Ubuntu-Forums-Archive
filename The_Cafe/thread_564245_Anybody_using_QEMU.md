---
title: "Anybody using QEMU?"
date: 2007-09-30
forum: The Cafe
---

### Post by RAV TUX on 2007-09-30
I just started using QEMU, I ran Haiku in QEMU last night.

I built the Haiku image in Linux and then ran it in QEMU.

I would like to try running some CD's & DVD's in QEMU but I haven't got a clue how to use this.

Looking for some QEMU help

I posted this in the Cafe also to make this more about discussion on QEMU in general and not just a help thread.

---

### Post by pluviosity on 2007-09-30
I tried using QEMU with DSL on a USB in my Windows partition for kicks.  It ran very nicely, only being a little slow when I used Firefox.

---

### Post by plb on 2007-09-30
I've tried it with kqemu but found both virtualbox and vmware to perform much better so I just use the latter.

---

### Post by stmiller on 2007-10-01
Virtualbox is based on qemu, and is quite nice.

But if you wan to use qemu there is a nice manager/gui here: [http://qemulator.createweb.de/](http://qemulator.createweb.de/)

---

### Post by altariel on 2007-10-01
I'd recommend qemu-launcher :) 
[http://packages.ubuntu.com/gutsy/otherosfs/qemu-launcher](http://packages.ubuntu.com/gutsy/otherosfs/qemu-launcher)

nice graphical way of configuring things ... 
but you need to have the kqemu-specific things done before you launch int since it won't do this automatically!

if you are using the commandline version add
-cdrom /dev/cd0 (for a real cd - beware of access restrictions!) 

or -cdrom /path/to/file 

if you want to boot from the cdrom/file you'll have to add 

`-cdrom file'
    Use file as CD-ROM image (you cannot use `-hdc' and and `-cdrom' at the same time). You can use the host CD-ROM by using `/dev/cdrom' as filename (see section 3.6.5 Using host drives). 
`-boot [a|c|d|n]'
    Boot on floppy (a), hard disk (c), CD-ROM (d), or Etherboot (n). Hard disk boot is the default.



[http://fabrice.bellard.free.fr/qemu/qemu-doc.html](http://fabrice.bellard.free.fr/qemu/qemu-doc.html)

---

### Post by ruibernardo on 2007-10-01
I'm using qemu. It is the only GNU/GPL option as oposition to vmware (closed source, [recent security problem]("http://www.vmware.com/support/server/doc/releasenotes_server.html") in 1.0.3) and virtualbox (compiled version isn't [totally free]("http://www.virtualbox.org/wiki/VirtualBox_PUEL")) and now that kqemu is also free in qemu, it is my choice.

With the vde package (check help.ubuntu.com on the kvm page or on [installing windows on qemu]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")), qemu (vdeqemu) can do all the networking that the others do, but in a transparent way using iptables (no magic modules nor hidden networking). 

kvm is derived from qemu. virtualbox too, but their code is specific to them. kvm will be integrated back to qemu soon, as I've read it on the qemu forum. kvm code is also on linux kernel.

> **altariel said:**
> I'd recommend qemu-launcher :) 
[http://packages.ubuntu.com/gutsy/otherosfs/qemu-launcher](http://packages.ubuntu.com/gutsy/otherosfs/qemu-launcher)

nice graphical way of configuring things ... 


qemu-laucher is cool, I use it too, just had to change qemu for vdeqemu to use it. 

Stmiler, in Gutsy [qemulator]("http://qemulator.createweb.de/") is on the repositories!

---

### Post by RAV TUX on 2007-10-01
> **altariel said:**
> I'd recommend qemu-launcher :) 
[http://packages.ubuntu.com/gutsy/otherosfs/qemu-launcher](http://packages.ubuntu.com/gutsy/otherosfs/qemu-launcher)

nice graphical way of configuring things ... 
but you need to have the kqemu-specific things done before you launch int since it won't do this automatically!

if you are using the commandline version add
-cdrom /dev/cd0 (for a real cd - beware of access restrictions!) 

or -cdrom /path/to/file 

if you want to boot from the cdrom/file you'll have to add 

`-cdrom file'
    Use file as CD-ROM image (you cannot use `-hdc' and and `-cdrom' at the same time). You can use the host CD-ROM by using `/dev/cdrom' as filename (see section 3.6.5 Using host drives). 
`-boot [a|c|d|n]'
    Boot on floppy (a), hard disk (c), CD-ROM (d), or Etherboot (n). Hard disk boot is the default.



[http://fabrice.bellard.free.fr/qemu/qemu-doc.html](http://fabrice.bellard.free.fr/qemu/qemu-doc.html)

> **epimeteo said:**
> I'm using qemu. It is the only GNU/GPL option as oposition to vmware (closed source, [recent security problem]("http://www.vmware.com/support/server/doc/releasenotes_server.html") in 1.0.3) and virtualbox (compiled version isn't [totally free]("http://www.virtualbox.org/wiki/VirtualBox_PUEL")) and now that kqemu is also free in qemu, it is my choice.

With the vde package (check help.ubuntu.com on the kvm page or on [installing windows on qemu]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")), qemu (vdeqemu) can do all the networking that the others do, but in a transparent way using iptables (no magic modules nor hidden networking). 

kvm is derived from qemu. virtualbox too, but their code is specific to them. kvm will be integrated back to qemu soon, as I've read it on the qemu forum. kvm code is also on linux kernel.



qemu-laucher is cool, I use it too, just had to change qemu for vdeqemu to use it. 

Stmiler, in Gutsy [qemulator]("http://qemulator.createweb.de/") is on the repositories!

Thanks for the 411.

---

### Post by pelle.k on 2007-10-01
Sure, i use qemu all the time. It's great when you like testing niche/hobby OS:es out like AROS, Haiku, Syllable (and the list goes on).
I've yet to try a linux distro out in qemu, but the fact is i prefer to test what i can on real hardware, unless there's no support for my hardware.

---

### Post by AndyCooll on 2007-10-27
I've recently started using Qemu and Qemulator and quite like it. 

My reasons are the same as those of epimeteo,

From a useage point of view I've found that all three are fairly similar. VirtualBox is probably the easiest to use, VMware the most polished, and Qemu the most free. However they all do a good job.

:cool:

---

