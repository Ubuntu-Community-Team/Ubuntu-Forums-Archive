---
title: "Faulty virtualbox install"
date: 2010-11-04
forum: Virtualisation
---

### Post by MathMcC on 2010-11-04
Hopefully my terminal output will shed some light on the issue... It seems like virtual box doesn't like my kernel version. I tried to uninstall it but it goes through the same process. When I try to do anything with apt it seems to try build virtual box. It seems to have messed up apt completely.

```
math@math-laptop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
math@math-laptop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
math@math-laptop:~$ sudo dpkg --configure -a
Setting up virtualbox-ose-dkms (3.1.6-dfsg-2ubuntu2) ...
Removing old virtualbox-ose-3.1.6 DKMS files...

------------------------------
Deleting module version: 3.1.6
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-ose-3.1.6 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.36-1-generic
Building for architecture x86_64
Building initial module for 2.6.36-1-generic

Error! Bad return status for module build on kernel: 2.6.36-1-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose/3.1.6/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-ose-dkms.0.crash'
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 virtualbox-ose-dkms
math@math-laptop:~$ 

```

---

### Post by uRock on 2010-11-04
Which OS uses that kernel as a default? Have you posted on Oracle's forum as well? [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by anewguy on 2010-11-04
Hummmmmm.....I just installed 10.10 this week, and my kernel is only at 2.6.35-22.   Are you running 10.10?  If not, what are you running?  Did you do something to install a newer kernel?  If so, why?

I would suspect that there are dependencies in the modules you are trying to build from and that they currently won't work with the kernel version you have.


Dave ;)

---

### Post by uRock on 2010-11-04
> **anewguy said:**
> I would suspect that there are dependencies in the modules you are trying to build from and that they currently won't work with the kernel version you have.
Especially if trying to install the one in Synaptic.

Moved to Virtualization s__ub-forum.

---

### Post by MathMcC on 2010-11-04
> **anewguy said:**
> Hummmmmm.....I just installed 10.10 this week, and my kernel is only at 2.6.35-22.   Are you running 10.10?  If not, what are you running?  Did you do something to install a newer kernel?  If so, why?

I would suspect that there are dependencies in the modules you are trying to build from and that they currently won't work with the kernel version you have.


Dave ;)
I followed [this guide]("http://ubuntuforums.org/showthread.php?p=9328344#post9328344") which lists ways to improve Ubuntu with my laptop. It includes a command to obtain the latest Linux kernel.

```
apt-get -y install linux linux-generic linux-headers-generic linux-image linux-image-generic
```
I didn't upgrade to 10.10. As far as I know I still have 10.04.

Can I roll back to a previous kernel version? I see the previous kernel versions of my OS (presumably for this sort of reason) still listed in GRUB but I've tried booting into them and still can't install. I think the error message is the same but I can check that if need be.

---

### Post by uRock on 2010-11-04
> **MathMcC said:**
> I followed [this guide]("http://ubuntuforums.org/showthread.php?p=9328344#post9328344") which lists ways to improve Ubuntu with my laptop. It includes a command to obtain the latest Linux kernel.

apt-get -y install linux linux-generic linux-headers-generic linux-image linux-image-generict 
I didn't upgrade to 10.10. As far as I know I still have 10.04.

Can I roll back to a previous kernel version? I see the previous kernel versions of my OS (presumably for this sort of reason) still listed in GRUB but I've tried booting into them and still can't install. I think the error message is the same but I can check that if need be.
If you try to boot the newest of the 2.6.32 kernels and it works, then you should be able to uninstall the newer kernel that you are currently using, but check before removing it.

---

### Post by MathMcC on 2010-11-04
OK I booted into the previous kernel without a hitch. Though I lost at least some of the changes I've made. E.g. Following the above tutorial I'd managed to get the touchpad working... now it doesn't...

How do I go about uninstalling the other kernel? Or at least the patch of it... I'm not sure how the process works.

Thanks for the swift help.

---

### Post by CharlesA on 2010-11-05
You should be able to just apt-get purge the other kernel.

---

### Post by MathMcC on 2010-11-05
Cheers. Like this?

sudo apt-get purge 2.6.36-1

---

### Post by CharlesA on 2010-11-05
Check here: [http://www.alterego7.com/2008/04/removing-those-extra-kernels-in-ubuntu.html](http://www.alterego7.com/2008/04/removing-those-extra-kernels-in-ubuntu.html)

---

