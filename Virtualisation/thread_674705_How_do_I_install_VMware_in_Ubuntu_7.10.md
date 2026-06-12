---
title: "How do I install VMware in Ubuntu 7.10?"
date: 2008-01-22
forum: Virtualisation
---

### Post by indianballer24 on 2008-01-22
I want to run windows xp on VMware on Ubuntu. How do I set this up?

---

### Post by dark_phantom on 2008-01-22
Download the latest VMware server from [www.vmware.com](www.vmware.com) for linux.  Unpack it and run the vmware-install.pl file, take all the defaults.  You will also need to register to get a serial number.  You can follow the instructions below from steps 3, 4 and 6.  It's for Dapper Drake, but should be similar to Gutsy Gibbon.

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by aeroseth on 2008-01-22
Hi, I was wondering the same thing, I'm running Gutsy Gibbon 7.10 with a very custom x86_64 kernel so I was having trouble. I mean restricted module nastiness and such, so I did a search @ HowToForge and found this little Betty of a Tutorial, she worked like a charm!

[http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10](http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10)

Have an awesome day! :guitar:
Seth

---

### Post by indianballer24 on 2008-01-24
Does the vmware server allow having multiple operating systems run at the same time?

---

### Post by fjgaude on 2008-01-25
> **indianballer24 said:**
> Does the vmware server allow having multiple operating systems run at the same time?

Yes, it does... I run Ubuntu with WinXP as a guest... works good. Notice my signature.

---

### Post by MetalManiacMat on 2008-01-25
Yer I'm a bit of a n00bcake to linux, well actually im king n00b when it comes to linux. But I do know a little. 

Anyway I downloaded the package file VMware-workstation-6.0.2-59824.i386.tar.gz from the VMware site. Now when I open it and click vmware-install.pl I get an error a little something like this.

> The file /home/mat/.fr-maf6bC/vmw…distrib/vmware-install.pl changed on disk.
Do you want to reload the file?

So then I press the reload button and another error message but a little diffent this time.

> Could not revert the file /home/mat/.fr-maf6bC/vmw…distrib/vmware-install.pl.
gedit cannot find it. Perhaps it has recently been deleted.

So what I'm really asking is how do I install or work around this or whatever. All I want is to have VMware on my computer so a can run multiple OS's on my desktop...

Please help me, I have a slow internet connection and it took ages just to download 200mb.

---

### Post by fjgaude on 2008-01-25
I don't know anything about workstation... download the server version, it is free. From there things should go good. Don't forget to get the license while you are on the vmware.com site.

---

### Post by dcstar on 2008-01-26
> **fjgaude said:**
> I don't know anything about workstation... download the server version, it is free. From there things should go good. Don't forget to get the license while you are on the vmware.com site.

You don't need to download things that are in the repositories, enable the Partner repository and just install VMware server (like any other package).

---

### Post by rosegarden78 on 2008-01-27
no luck with VMware is commercial product instruction confusing try VirtualBox from the repositories instead. [http://ubuntuforums.org/showthread.php?t=679884](http://ubuntuforums.org/showthread.php?t=679884)

---

