---
title: "Install VritualBox on existing OS's?"
date: 2010-08-21
forum: Virtualisation
---

### Post by user_linux08 on 2010-08-21
I am not sure this question has been posted before.

I have a 3-part partitioned HD on which I have. 

1. Windows 7
2. Ubuntu 10.04
3. /Home for my Ubuntu files.

I use both OS's quite often. (Windows, for apps which don't run on Ubuntu).

Is that possible to install the VB such that, I can move from Windows to Linux and vis-versa with ease, and w/o the usual "restart" the machine with the desired OS?.

unfortunately I found Wine, practically useless for this purpose.

I am very new to the this Virtual thing.

---

### Post by wilee-nilee on 2010-08-21
You can install virtual in either and run either. Personally I prefer a Linux Host set up. The kicker is your system specs what are they?

---

### Post by bodhi.zazen on 2010-08-22
You can boot physical hard drives, but you need to be careful when you do so.

Windows requires more modifications then Ubuntu, and if you boot the wrong OS you can have data loss.

---

### Post by FattyOwl on 2010-08-23
I advise you to install virtualbox or vmware on a linux host and run windows in a virtual machine.

How to go about this:
[LIST]
[*]Make a complete backup disk of your windows installation.
[*]Either install VirtualBox or VMWare (workstation). VMWare is a non-free alternative but the overall quality and speed is much better.
[*]Create a new Virtual Machine with at least 1GB RAM for Windows 7.
[*]Install your backup disk on this virtual machine
[*]Delete your Windows 7 partition[*]
[/LIST]

You could also install a VM with ubuntu within Windows. That depends on which OS you use most often.

Here you can find a informative article comparing VMWare workstation and VirtualBox:
[http://www.eweek.com/c/a/Virtualization/VMware-Workstation-vs-Oracle-VM-VirtualBox-635564/](http://www.eweek.com/c/a/Virtualization/VMware-Workstation-vs-Oracle-VM-VirtualBox-635564/)

---

