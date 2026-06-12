---
title: "Why hasn't anyone done this?/Is this possible?"
date: 2008-08-14
forum: The Cafe
---

### Post by Fixman on 2008-08-14
I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

---

### Post by damis648 on 2008-08-14
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

An Operating System cannot format and repartition its own drive/partition. Its not possible. The OS would erase itself before anything would be done. If you mean, say install on a separate, pre-created partition, I do not see why not, although you would most likely still need a CD for this, if the OS did not have some sort of unmounting-and-repartitioning-and-mounting feature for repartitioning itself, still booted. A similar implementation, though not on a separate partition, would be WUBI. [http://wubi-installer.org/](http://wubi-installer.org/).

---

### Post by smartboyathome on 2008-08-14
There is Wubi, but the reason there isn't any is because you need to have all partitions unmounted in order to install an OS (for partitioning, mainly).

---

### Post by GreenN00b on 2008-08-14
Because a running OS usually locks the hard drive and it is relatively hard and unsafe to bypass this.
There are some versions of operating system that can boot from other operating systems ... I don't remember one right now but I encountered some ...
Also some install CD's act like live CD's so you can take a look at the OS before installing it ...

---

### Post by picpak on 2008-08-14
There are distros that install inside Windows, but I've never found them to work very well.

---

### Post by collinp on 2008-08-14
> **picpak said:**
> There are distros that install inside Windows, but I've never found them to work very well.

Guess what Wubi does? Anyways, it is relatively unsafe to mess with partitions while one or more is mounted, easy way to lose data. For that, a CD is the safest option.

---

### Post by KingTermite on 2008-08-14
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

What's an Operative System? :p


damis648 explains it pretty well.

---

### Post by lisati on 2008-08-14
> **KingTermite said:**
> What's an Operative System? :p

it almost sounds like something that got lost in translation, a bit like "Built-in Operating Smarts" for BIOS - it might be of help to some people even though it's not the usual intepretation. My guess is that most of the forum regulars wuld call it an "Operating System"

---

### Post by billgoldberg on 2008-08-14
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

There is Wubi, but that doesn't really count as a real OS install.

The reason why is already explained here.

---

### Post by spupy on 2008-08-14
Actually, you can do something like this, but manually.
That is the way to install gentoo. The LiveCD used to install gentoo doesn't even have to be a gentoo livecd, if I remember correctly. It is only needed to wget the compressed base system from the internet, chroot into it and install the rest. I guess you can do this from another running Linux distro, too.

---

### Post by az on 2008-08-14
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

It used to be possible to launch linux from windows (before windows XP).  Loadlin was a program than would make your computer boot into a linux operating system without rebooting - it would bootload linux onto the memory that was being run by windows.  

That was pretty much a huge security flaw and has since been corrected.  So, it's not possible to relinquish complete control of your computer while it is running Windows (or mac) without rebooting.

---

### Post by Fri13 on 2008-08-28
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

Actually there is. The operating system is the Linux (it is monolith kernel!) and you can get only a network bootfloppy or install them to USB stick. Size is around 20-40Mb (same as those very small distributions). Then you boot your computer with it and you get command line where you first create your partitions, set the booting and then you give the address of FTP/HTTP/Local place where the rest packages of software system is going to be downloaded/copied and installed. Usually the Operating System is installed before that to disk from the bootdisk, and you actually use it with the installation applications to get rest of the system applications installed. 

This is actually bretty dificult operating for novice users because it needs bretty much understanding of how distributions are build. And usually you compile Linux before that with your own settings and drivers so you get exactly the wanted operating system running before you start installing any other applications. Usually this is done for machines what has limited HD space or other special needs where the normal system installation is not possible.

In earlier times, programmers needed to download operating system (Linux) and all needed development softwares alone and get them compiled to computer, that was very dificult task and it was time when Windows 95 was came out. Now it's much easier to install software system to your computer because CD images where operating system and all applications have pre-build and you only need to boot from it and install it to HD. But as I said, you can get those small boot disk from at least from Debian, Gentoo and mayby a openSUSE so you can build your own Software System around Linux operating system if you wanted. If you choose Debian, you can even Install Hurd.

---

### Post by swoll1980 on 2008-08-28
maybe a .exe that installs an os to flash drive. Something like that?

---

### Post by koenn on 2008-08-28
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?
The Debian installation manual describes a procedure that does just that:
from within an existing Linux or Unix system, you run a program (debootstrap), and that program installs Debian.

---

### Post by Golem XIV on 2008-08-28
There's always [Linux from Scratch]("http://www.linuxfromscratch.org/") but the installation is a bit slow...:)

---

### Post by leepesjee on 2008-08-28
Spupy, don't understand your smiley, but love your other quote/signature :)

BTW, as others have mentioned, it is possible. You can even tar a complete exiting installation and untar that into another partition. The only thing that remains to be done is to configure grub. LFS-ers do that with their basic installation to build new one's from that.

---

### Post by mocoloco on 2008-08-28
I'm surprised no one has yet mentioned [goodbye-microsoft.com]("http://goodbye-microsoft.com/")
Of course you have to already have Windows installed for it to work.

---

### Post by oldos2er on 2008-08-28
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

 Like this: [http://www.faqs.org/docs/Linux-HOWTO/Network-Install-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Network-Install-HOWTO.html) ?

---

### Post by init1 on 2008-08-28
> **Fixman said:**
> I always noted that all (or all I have seen) Operative Systems are an iso image that you must put on a cd and boot from that CD (or something *like* that). Why isn't there an OS where you can download a program, and that program installs the OS, without isos nor anything?

> **damis648 said:**
> An Operating System cannot format and repartition its own drive/partition. Its not possible. The OS would erase itself before anything would be done. If you mean, say install on a separate, pre-created partition, I do not see why not, although you would most likely still need a CD for this, if the OS did not have some sort of unmounting-and-repartitioning-and-mounting feature for repartitioning itself, still booted. A similar implementation, though not on a separate partition, would be WUBI. [http://wubi-installer.org/](http://wubi-installer.org/).

> **smartboyathome said:**
> There is Wubi, but the reason there isn't any is because you need to have all partitions unmounted in order to install an OS (for partitioning, mainly).

> **GreenN00b said:**
> Because a running OS usually locks the hard drive and it is relatively hard and unsafe to bypass this.
There are some versions of operating system that can boot from other operating systems ... I don't remember one right now but I encountered some ...
Also some install CD's act like live CD's so you can take a look at the OS before installing it ...
Actually, it **is** possible. But not in the traditional sense. If you've got Linux installed, you can boot another on the same partition if the root is compressed. This would be like doing a USB drive install, except with a hard drive. The system would be live, but it wouldn't require any formating or partitioning. I've done this with SliTaz before.

---

### Post by Lostincyberspace on 2008-08-28
I would like to see some thing like this built in to the linux quick boots, like Asus has, so you could have a thousand different Distros at your finger tips.

---

### Post by tdrusk on 2008-08-28
> **spupy said:**
> Actually, you can do something like this, but manually.
That is the way to install gentoo. The LiveCD used to install gentoo doesn't even have to be a gentoo livecd, if I remember correctly. It is only needed to wget the compressed base system from the internet, chroot into it and install the rest. I guess you can do this from another running Linux distro, too.
Yeah you chroot into the actual hard drive and install the system. It's kind of like what every live cd does except Gentoo makes you do it. After this you have to edit your grub to make it so you can boot into partition. 

Not so many people have extra partitions hanging around on their hard drives.

Honestly I would rather install Ubuntu over Gentoo any day.

Wubi kind of works like the threadstarter subscribed.

---

### Post by Giant Speck on 2008-08-28
Unetbootin

I used it to install Ubuntu, because for some reason I couldn't install it from CD.

---

### Post by Sorivenul on 2008-08-31
> **Golem XIV said:**
> There's always [Linux from Scratch]("http://www.linuxfromscratch.org/") but the installation is a bit slow...:)

Compared to 15 - 30 minutes for a typical Ubuntu install, this is true.  However, it is not too terribly bad anymore, actually, thanks to the ALFS project and LFScript.  LFScript is a neat little tool.  Learn about it [here]("http://www.zimbio.com/Ubuntu+Linux/articles/63/LFScript+Automated+Linux+Scratch") - you can still follow the video tutorial, though a newer version of LFScript is out.  You can find the up-to-date build scripts [here]("http://lfs.marcelweb.nl/lfsweb2/index.php?section=home").

---

