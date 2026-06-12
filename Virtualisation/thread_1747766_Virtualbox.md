---
title: "Virtualbox"
date: 2011-05-03
forum: Virtualisation
---

### Post by Vinger on 2011-05-03
Hello,

I formatted my pc completely from 10.10 (32bit) to 11.04(64bit)

Everything works fine, except for virtualbox.
I accendently installed virtualbox OSE, but removed it to install the complete virtualbox from the oracle sources... I hope this is not the problem...
I tried to add my old virtual machines, but i get this error
> 
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary. 

When i go to /etc/init.d, i don't see the file vboxdrv
when i do the command, i get the following:
> 
koenh@koenh-Kubuntu:/etc/init.d$ /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory


I allready remove and reinstalled virtualbox 4.0, but no luck.
Does anyone has an idea what the problem could be?
tx.

---

### Post by Vinger on 2011-05-04
Hello,

I also tried to make a new machine, but this gave the same error...

No one an idea?

tx.

---

### Post by Vinger on 2011-05-08
solved by purging and reinstalling...

---

### Post by franz.linz on 2011-05-08
I had a similar problem. The Virtualbox didn't start in '2.6.38-9 PAE'-Kernel. The compiling of the 'DKMS' to this kernel goes wrong.

Solving the problem:
Starting with linux-version 2.6.38-9 (while booting whit grub, on my pc it was in 'previous versions'),
complete deinstallation of 'virtualbox-dkms',
installation of  'virtualbox-dkms', this time the compilation is ok,
restarting the system
Virtualbox works as before.

I hope, this problem will be fixed soon.

good luck

---

### Post by franz.linz on 2011-05-09
If your pc runs under 2.6.38-9-PAE-kernel, then you have to install linux-headers-generic-pae (eg. with synaptic-packagemanager). The dkms-modules are newly compiled and after a system-restart virtualbox should run.

best regards
:D

---

### Post by Vinger on 2011-05-16
Hello guys...

This is working...
I have reinstalled the ose version, and then purged is.
After this, i installed the complete version and it was ok.

tx.

---

### Post by aveeshkumar on 2011-08-22
As posted above, the following worked with a slight modification - ubuntu natty, vbox 4.1.2

replace aptitude with apt-get

sudo apt-get update (OK)
sudo apt-get install dkms (already latest)
sudo /etc/init.d/vboxdrv setup (error about conf file not in good format but WORKED)

Thanks all - HTH

my level - advanced noob!

---

### Post by steve7777777 on 2011-12-03
> **aveeshkumar said:**
> As posted above, the following worked with a slight modification - ubuntu natty, vbox 4.1.2

replace aptitude with apt-get

sudo apt-get update (OK)
sudo apt-get install dkms (already latest)
sudo /etc/init.d/vboxdrv setup (error about conf file not in good format but WORKED)

Thanks all - HTH

my level - advanced noob!

Thanks! worked with Maverick Meerkat with vbox 4.1.4

I got the error:
Kernel driver not installed (rc=-1908 )
Your answer is a gift that keeps on giving! My vm was back up in minutes. Thanks!!!

---

### Post by jcoles on 2011-12-14
I did as Vinger suggested: Complete removal of the OSE version and installation of the full version. 

MAJOR PROBLEM: /etc/init.d/vboxdrv is not installed!!!!

Synaptic lists it as an installed file for virtualbox-4.1, but it is NOT present. Do I need to extract it from the archive and install it myself? 

Should virtualbox-ose-dkms still be present? 

apt-get cannot find virtualbox-dkms and I can't even find such a package on the virtualbox web site. 

A full install should deliver a working system, with all files installed. How can I fix this? Any ideas?

---

### Post by lukeiamyourfather on 2011-12-14
VirtualBox requires a kernel module to run the virtual machines. If you install VirtualBox from Oracle directly you'll have to install the kernel module specific to the kernel you're using (this is not automatic). If you use VirtualBox from the Ubuntu repositories it will install the appropriate kernel modules for you. From my understanding of it, there's only one version of VirtualBox now which was previously called VirtualBox OSE. The non-OSE features are now an extension pack from Oracle, so you might as well just install the VirtualBox from the Ubuntu repositories because they are the same and installing from the repositories is easier. Then you can install the extension pack if you like regardless of how VirtualBox was originally installed.

---

