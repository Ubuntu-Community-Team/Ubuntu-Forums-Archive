---
title: "Daily desktop 64 bit iso goes directly to &quot;try&quot;, no ability to &quot;install&quot; (VM)"
date: 2015-12-17
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-12-17
I wanted to verify a bug report that was set to "fix released" yesterday.
When I try to install a VM guest of the daily Desktop 64 bit ISO of 2015.12.17 it goes straight to trying Ubuntu, bypassing the "Try Ubuntu" or "Install Ubuntu" normal decision point.
The same was true yesterday, however that daily was still 2015.12.14.
If I go back to my last previous daily ISO, 2015.11.13, I get the "Try Ubuntu" or "Install Ubuntu" normal decision point.

Anybody else?

My host is my main 14.04.3 Ubuntu server 64 bit. And I use KVM. Not that I think it matters but my command line is:

```
doug@s15:~/iso$ sudo virt-install -n desk_dev -r 8192 --disk path=/media/newhd/desk_dev.img,bus=virtio,size=20 -c xenial-desktop-amd64-2015-12-17.iso --network bridge=br0,model=virtio,mac=52:54:00:87:d2:f4 --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```

---

### Post by Doug S on 2015-12-18
same issue with the daily of 2015.12.18.

---

### Post by sudodus on 2015-12-18
Is this standard Ubuntu Xenial desktop amd64?

Please help me read the long command line for KVM: is it running in BIOS mode or UEFI mode?

I can try it in a real computer.

---

### Post by sudodus on 2015-12-18
When I download the 'current' iso file, I get the file date Dec 9. I think it means the newer versions have not passed some automatic tests. See this link:

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

I think you are testing the 'pending' iso file - which may explain your problem - but I could check if it affects also Lubuntu, which has no automatic tests.

---

### Post by flocculant on 2015-12-18
64 bit are building - 32bit are not, 64 bit should have plymouth fixed, 32bit will still be without. Not sure any build is quite right tbh.

---

### Post by Doug S on 2015-12-18
> **sudodus said:**
> When I download the 'current' iso file, I get a file date Dec 9. I think it means the newer versions have not passed some automatic tests. See this link:

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

I think you are testing the 'pending' iso file - which may explain your problem - but I could check if it affects also Lubuntu, which has no automatic tests.Oh, Thanks. I only know, and have only ever known, to use the link on the [QA tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds") which puts me [here]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/108899/downloads") (for this use case).

Yes, standard Ubuntu Xenial desktop amd64.

My KVM command line reads as:

. The definition file will be called desk_dev (results in /etc/libvirt/qemu/desk_dev.xml). Not to be confused with the eventual virtual computer name.
. Give the VM 8 Gigs of memory.
. Give the VM a 20 gig disk where in the host it is located at /media/newhd/desk_dev.img
. The VM will pretend to use a CDROM by using this file xenial-desktop-amd64-2015-12-17.iso (I execute the command from my iso directory).
. For a network use the bridge I have previously setup so that the VM ends up on my LAN.
. For the network interface re-use the same MAC address (because then my mac based dhcp server will give the VM a known IP address, and the same one all the time).
. Use vmvga video driver. Why? Because the default cirrus driver sucks.
. Use VNC to connect to the VM, from anywhere, and prevent any automatic console stuff. Why? Because for me this method works, and I have never ever succeeded with any other method.
. Give the VM 4 CPUs.

---

### Post by sudodus on 2015-12-18
Yes, this happens with Lubuntu too (***Edit 1: ***in two real computers). I tested with today's xenial-desktop-i386.iso (Dec 18).

I can select 'Install', but it starts the normal 'Try' alias live session. Ubiquity starts from the 'Install' icon, so the problem is not that ubiquity is missing or failing.

You have found a bug.

[hr][/hr]
***Edit 2,*** more testing:

The same problem affects today's Lubuntu 64-bit, xenial-desktop-amd86.iso (Dec 18) in BIOS mode (syslinux) as well as in UEFI mode (grub2).

Another problem: Lubuntu 32-bit does not shutdown or reboot at the prompt 'Please remove the installation medium, then press ENTER: so I use SysRQ r e i s u b
Shutdown works for Lubuntu 64-bit, but not reboot, so this feature is flaky.

---

### Post by sudodus on 2015-12-18
> **Doug S said:**
> Oh, Thanks. I only know, and have only ever known, to use the link on the [QA tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds") which puts me [here]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/108899/downloads") (for this use case).

Yes, standard Ubuntu Xenial desktop amd64.

My KVM command line reads as:

. The definition file will be called desk_dev (results in /etc/libvirt/qemu/desk_dev.xml). Not to be confused with the eventual virtual computer name.
. Give the VM 8 Gigs of memory.
. Give the VM a 20 gig disk where in the host it is located at /media/newhd/desk_dev.img
. The VM will pretend to use a CDROM by using this file xenial-desktop-amd64-2015-12-17.iso (I execute the command from my iso directory).
. For a network use the bridge I have previously setup so that the VM ends up on my LAN.
. For the network interface re-use the same MAC address (because then my mac based dhcp server will give the VM a known IP address, and the same one all the time).
. Use vmvga video driver. Why? Because the default cirrus driver sucks.
. Use VNC to connect to the VM, from anywhere, and prevent any automatic console stuff. Why? Because for me this method works, and I have never ever succeeded with any other method.
. Give the VM 4 CPUs.

Thanks for explaining your KVM command line :-)

---

### Post by Doug S on 2015-12-18
> **sudodus said:**
> 
***Edit 2,*** more testing:

It does not shutdown or reboot at the prompt 'Please remove the installation medium, then press ENTER: so I use SysRQ r e i s u b

The same problem affects today's Lubuntu 64-bit, xenial-desktop-amd86.iso (Dec 18) in BIOS mode (syslinux) as well as in UEFI mode (grub2).Yes, I get that issue also, and should have mentioned it before.

Thanks very much for your testing. I'll see if I can find a pre-existing bug report or think about making a new one.

---

### Post by sudodus on 2015-12-18
If you make a bug report, post a link to it so that I can mark 'affects me too'.

---

### Post by MikeMecanic on 2015-12-18
This bug is not affecting kubuntu 16.04 LTS (Dec. 14th and last daily build).  Build an ISO image last night using Strartup Disk.  This morning I try the installer and it boots normally.  Was able to take a tour and restart and shutdown normally:  Was ask each times to eject the media.  Just try to install it and it was normal.

But last week I was working on how to remove grub in Windows 10 architecture.  So I load the Trusty Tar (14.04.3) and it boots directly in the try Ubuntu desktop.  But I was able to do the installation from there.  

Regards,

Edit: I thought that December 14th was the last build.  So I download Kubuntu 16.04 Dec. 18th build and the same apply.  No bug

---

### Post by Doug S on 2015-12-18
I found a pre-existing [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1525446"), and have added my use case. I also entered a failed installation test on the QA tracker.

---

### Post by Doug S on 2015-12-18
> **sudodus said:**
> When I download the 'current' iso file, I get the file date Dec 9. I think it means the newer versions have not passed some automatic tests. See this link:

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
@sudodus, or anybody. Is there somewhere one can review the automated testing logs for any results, partial or complete, for the last few days.

---

### Post by sudodus on 2015-12-19
> **Doug S said:**
> I found a pre-existing [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1525446"), and have added my use case. I also entered a failed installation test on the QA tracker.

I'll add 'affects me too'.

> **Doug S said:**
> @sudodus, or anybody. Is there somewhere one can review the automated testing logs for any results, partial or complete, for the last few days.

I don't know, but someone should know. Maybe you get an answer if you ask via the Ubuntu Quality mailing list.

---

### Post by flocculant on 2015-12-19
[https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/xenial/ubuntu](https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/xenial/ubuntu) 

You can find the build-logs there. 

It's a bit hit and miss finding flavours - but they are there :)

Automated stuff should be at Jenkins [https://jenkins.qa.ubuntu.com/](https://jenkins.qa.ubuntu.com/)

---

### Post by Doug S on 2015-12-19
The xenial-desktop-amd64.iso of 2015.12.19 has the goes directly to "try" issue.

> **MikeMecanic said:**
> But last week I was working on how to remove grub in Windows 10 architecture.  So I load the Trusty Tar (14.04.3) and it boots directly in the try Ubuntu desktop.  But I was able to do the installation from there.This method worked. It also re-booted properly at the end of the installation. Thanks. I did not know of this method to do the installation. I do observe a test case for this method, for which I submitted a "pass".

---

### Post by sudodus on 2015-12-19
With enough RAM, it is no problem to install from 'Try Ubuntu'. Otherwise it is an advantage the use the 'Install Ubuntu' option, because it is basically a simple openbox session, which uses less RAM than the full live desktop session.

---

### Post by MikeMecanic on 2015-12-19
Ubuntu 14.04.3 (10-12 days ago), Ubuntu Kylin 16.04 LTS and XUbuntu 16.04 LTS are loading directly into the desktop,or try Ubuntu.  Do we really need this option?  It's still possible to run the installer Inside Try Ubuntu. 

Today's daily builds.: 12-18

---

### Post by sudodus on 2015-12-19
If you have only 384 MB or 512 MB RAM it is definitely an advantage to use the 'Install Lubuntu' option instead of 'Try Lubuntu' and then click the desktop icon, but when there is enough RAM for all the eye candy, 'Install Lubuntu' is not necessary. The limit is higher for the other Ubuntu flavours, but I think almost all brand new computers have enough RAM to install via 'Try [x]ubuntu' and the desktop icon. So the option 'Install [x]ubuntu' is useful for old computers.

---

### Post by matt_symes on 2015-12-22
Doug I could buy you a beer.

```
maybe-ubiquity
```

I've spent the last 3 weeks trying to find that.

---

### Post by Doug S on 2016-01-01
xenial-desktop-amd64.iso of 2016.01.01 (January 1st, 2016) gives me the option to "try" or "install".
It still doesn't re-boot properly at the end of the installation, but works fine after a forced re-boot.

EDIT: Above was a VM installation. An installation on real hardware re-booted fine at the end of installation.

---

### Post by Irihapeti on 2016-01-01
I can confirm the same for Xubuntu xenial-desktop-i386.iso of 2016.01.01

---

### Post by sudodus on 2016-01-01
> **Irihapeti said:**
> I can confirm the same for Xubuntu xenial-desktop-i386.iso of 2016.01.01

+1 for Lubuntu xenial-desktop-i386.iso of 2016.01.01

---

