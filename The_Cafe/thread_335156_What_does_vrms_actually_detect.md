---
title: "What does vrms actually detect?"
date: 2007-01-09
forum: The Cafe
---

### Post by Dr. C on 2007-01-09
I ran the program with **both** Windows XP Pro and Windows Vista running in virtual machines under VMware Server. 

Here is my output 

fp-linux-ws F-Prot Antivirus for Linux Workstations.
linux-386 Complete Linux kernel on 386.
linux-686 Complete Linux kernel on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
nvidia-glx NVIDIA binary XFree86 4.x/X.Org driver
Reason: Proprietary license
opera The Opera Web Browser
ttf-gentium Gentium TrueType font
unrar Unarchiver for .rar files (non-free version)
Reason: Modifications problematic

So if it can miss both Windows Vista and XP of all things what else did it miss?

---

### Post by saulgoode on 2007-01-09
One of the principles of virtualization is that an operating system running on a virtual machine has no way to know that it is running on a virtual machine. In your case, Linux is completely unaware that it is not running on "real" hardware and there are other OSes present (this is as it should be).

---

### Post by Dr. C on 2007-01-09
> **saulgoode said:**
> One of the principles of an operating system running on a virtual machine is that there is no way for it to know that it is running on a virtual machine. In your case, Linux is completely unaware that it is not running on "real" hardware and there are other OSes present (this is as it should be).

Yes but I was running Vista and XP as the guests not the host. The host, Ubuntu Dapper is very much aware of the guests Windows Vista and Windows XP with thier memory consumption of close to 1.2 GB between both of them to start.

---

### Post by macogw on 2007-01-09
I think it just does the .deb's that are installed or have bits remaining after uninstallation.  Since Windows isn't in deb form, it doesn't show up.

I want to know why it thinks Sun Java is still non-Free?  They GPL'd it two months ago.

---

### Post by Kindred on 2007-01-09
Obviously it is not going to pick up what is running inside the VM, I would of thought it would show VMware Server itself though?  I suppose it would have to work on a database of some kind to do that, I have no idea how it works right now..

---

### Post by macogw on 2007-01-09
vmware server is installed from a source tarball, isn't it?  Anything installed from source won't show because it reads the list of .debs.  It says "list of packages" doesn't it?  Source-built stuff isn't packaged.

---

### Post by saulgoode on 2007-01-09
> **FineE said:**
> Yes but I was running Vista and XP as the guests not the host. The host, Ubuntu Dapper is very much aware of the guests Windows Vista and Windows XP with thier memory consumption of close to 1.2 GB between both of them to start.

My mistake. I was assuming that you were running Linux as a guest. Sorry if I sounded patronizing.

---

### Post by Dr. C on 2007-01-10
To do this properly you really have to do a hard disk scan. Still I would have expected it to detect VMWare server. As for telling what is running in a VM and if it is free as in speech or not checking the VMWare configuation files for "Windows" would be a start. If the hypervisor were free one still should be able to detect a non free guest especially Windows XP or Vista. 

I wonder how it handles WINE. Can it tell if a Windows application installed under WINE is free or not? 

I also have Flash 7 intalled on this system, and a bunch of non free codecs that it did not pick up.

---

### Post by macogw on 2007-01-10
It doesn't see IEs4Linux.

---

### Post by enopepsoo on 2007-01-10
> **saulgoode said:**
> My mistake. I was assuming that you were running Linux as a guest. Sorry if I sounded patronizing.

I read it over.  You did not sound patronizing 8)

---

### Post by Dr. C on 2007-01-10
> **enopepsoo said:**
> I read it over.  You did not sound patronizing 8)

I agree.

---

### Post by Iandefor on 2007-01-10
> **FineE said:**
> I ran the program with **both** Windows XP Pro and Windows Vista running in virtual machines under VMware Server. 

Here is my output 

fp-linux-ws F-Prot Antivirus for Linux Workstations.
linux-386 Complete Linux kernel on 386.
linux-686 Complete Linux kernel on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
nvidia-glx NVIDIA binary XFree86 4.x/X.Org driver
Reason: Proprietary license
opera The Opera Web Browser
ttf-gentium Gentium TrueType font
unrar Unarchiver for .rar files (non-free version)
Reason: Modifications problematic

So if it can miss both Windows Vista and XP of all things what else did it miss? It polls apt for software installed under a GPL-incompatible license, I believe. Unless you installed Windows via apt, I see no reason for it to detect software you never installed via the package management system.> **macogw said:**
> I want to know why it thinks Sun Java is still non-Free?  They GPL'd it two months ago. See above and apply above to the fact that: Java is *in the process of being GPL'ed*. It isn't GPL'ed all the way yet. It was *announced* months ago. Even if it were all the way GPL'ed, the package in the repositories is frozen. They'd have to backport the GPL'ed version because the version in Edgy isn't GPL'ed.

---

### Post by Dr. C on 2007-01-10
> **Iandefor said:**
> It polls apt for software installed under a GPL-incompatible license, I believe. Unless you installed Windows via apt, I see no reason for it to detect software you never installed via the package management system. See above and apply above to the fact that: Java is *in the process of being GPL'ed*. It isn't GPL'ed all the way yet. It was *announced* months ago. Even if it were all the way GPL'ed, the package in the repositories is frozen. They'd have to backport the GPL'ed version because the version in Edgy isn't GPL'ed.

I can see why it detected Java since it is still in the process of being GPLd, but I am not sure of the APT theory since I have for example flashplugin-nonfree showing as installed under Synaptic and vrms did not pick that up either.

---

### Post by Iandefor on 2007-01-10
> **FineE said:**
> I can see why it detected Java since it is still in the process of being GPLd, but I am not sure of the APT theory since I have for example flashplugin-nonfree showing as installed under Synaptic and vrms did not pick that up either. I noticed similar discrepancies which undermined my confidence in that particular interpretation. The Wikipedia article is somewhat more helpful:

[http://en.wikipedia.org/wiki/Vrms](http://en.wikipedia.org/wiki/Vrms)
> ***vrms** (Virtual [Richard M. Stallman]("http://en.wikipedia.org/wiki/Richard_Matthew_Stallman")) is a [program]("http://en.wikipedia.org/wiki/Computer_program") that will analyze the set of currently-installed packages on a [Debian]("http://en.wikipedia.org/wiki/Debian")-based system, and report all of the packages from the non-free tree which are currently installed.* It seems, then, that vrms adapted to work on Ubuntu would, perhaps, find software from the analogue of non-free, ie Multiverse/commercial. Software installed from outside those repositories but still not Free would escape vrms' notice, if Wikipedia is correct.

EDIT: A more authoritative source, packages.debian.org, corroborates Wikipedia.

[http://packages.debian.org/stable/admin/vrms](http://packages.debian.org/stable/admin/vrms)
> The vrms program will analyze the set of currently-installed packages on a Debian GNU/Linux system, and report all of the packages from the non-free tree which are currently installed.

---

### Post by tbroderick on 2007-01-10
> **FineE said:**
> for example flashplugin-nonfree showing as installed under Synaptic and vrms did not pick that up either.

Maybe it's fooled by flashplugin-nonfree cause it's just an installer and not flash.

---

### Post by Dr. C on 2007-01-10
> **Iandefor said:**
> I noticed similar discrepancies which undermined my confidence in that particular interpretation. The Wikipedia article is somewhat more helpful:

[http://en.wikipedia.org/wiki/Vrms](http://en.wikipedia.org/wiki/Vrms)
 It seems, then, that vrms adapted to work on Ubuntu would, perhaps, find software from the analogue of non-free, ie Multiverse/commercial. Software installed from outside those repositories but still not Free would escape vrms' notice, if Wikipedia is correct.

EDIT: A more authoritative source, packages.debian.org, corroborates Wikipedia.

[http://packages.debian.org/stable/admin/vrms](http://packages.debian.org/stable/admin/vrms)

The version of vrms in Ubuntu is I suspect the Debian version and has not being modified by Ubuntu so it will only pick up non free packages in the Debian non free repositories as opposed to Ubuntu non free repositories. Anything else including popular non free programs such as VMWare, Flash etc will escape detection.

---

### Post by Iandefor on 2007-01-10
> **FineE said:**
> The version of vrms in Ubuntu is I suspect the Debian version and has not being modified by Ubuntu so it will only pick up non free packages in the Debian non free repositories as opposed to Ubuntu non free repositories. Anything else including popular non free programs such as VMWare, Flash etc will escape detection.From my experience, Ubuntu does a relatively good job of managing crossovers like that. Also, if all it detected was software from Debian non-free, it would be almost certain to detect *nothing* on an Ubuntu system. Packages are rebuilt from Debian to Ubuntu and they update the metadata to reflect the Ubuntu section it comes from, not the Debian section.

---

### Post by deanlinkous on 2007-01-11
vrms is not perfect, some false positives and false negatives.....and vice versa :)

The gentium font IS free......
Some of the other packages that are not free won't get noticed because vrms probably hasn't been updated.

---

