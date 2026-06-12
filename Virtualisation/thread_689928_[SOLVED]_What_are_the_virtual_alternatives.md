---
title: "[SOLVED] What are the virtual alternatives?"
date: 2008-02-06
forum: Virtualisation
---

### Post by nikolas68 on 2008-02-06
Hi guys....i've installed Innotek VirtualBox on my NEC Versa S3200....but i don't like the way it works....and i cannot install VMWare since a message says this:
VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

What is another good virtual machine alternative?

---

### Post by pytheas22 on 2008-02-06
qemu is an option but it can only run Linux virtual machines.

I think that you should try to troubleshoot the VMware error message however.  As long as you have a standard machine--and i386 is definitely standard--it should work.  I don't know how you tried to install VMware, but there are plenty of guides online on getting VMware it installed in Linux, so you should check them out before giving up.  VMware is especially nice because it supports hardware acceleration (still in beta mode, but it generally works reliably enough), so you can even play games inside your virtual machine if you're into that.

---

### Post by randy78 on 2008-02-06
Check out the Virtualization forum, as it will provide you with many alternatives and lots of information.

Good luck!

[http://ubuntuforums.org/showthread.php?t=582729]("http://ubuntuforums.org/showthread.php?t=582729")

---

### Post by nikolas68 on 2008-02-06
MMMMMmmm i think i might try again to install Vmware as you've suggested but not from the repo: that's where i'm getting the error msg from..
thanks m8..

---

### Post by pytheas22 on 2008-02-06
yes, I seem to recall having trouble with the VMware package in the repository as well.  Look for directions online; they work better.

---

### Post by nikolas68 on 2008-02-06
> **pytheas22 said:**
> yes, I seem to recall having trouble with the VMware package in the repository as well.  Look for directions online; they work better.

I'm presently downloading from Softpedia the VMWare version 2.0.1 and was reading Igor Weblog page on how to install....will tell you how it goes. cheers.

---

### Post by nikolas68 on 2008-02-07
....things are not going smoothly: i've followed the instructions as per tutorial over here: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)
...but when i enter this line in the terminal i get this

```
nicola@ubuntu:~$ cp vmware-any-any-update115/*.tar vmware-server-distrib/lib/modules/source/
cp: cannot create regular file `vmware-server-distrib/lib/modules/source/vmblock.tar': Permission denied
cp: cannot create regular file `vmware-server-distrib/lib/modules/source/vmmon.tar': Permission denied
cp: cannot create regular file `vmware-server-distrib/lib/modules/source/vmnet.tar': Permission denied
nicola@ubuntu:~$ 
```

....and if i carry on with the installation  at the end it gets aborted. Any advice?? this goes over my basic knowledge...

SOLVED: just needed a simple SUDO...

---

