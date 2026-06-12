---
title: "Editing Grub"
date: 2011-02-26
forum: Ubuntu Christian Edition
---

### Post by AlexNagy on 2011-02-26
I've got it working and it's really nice. Only thing is, I want to do some editing to grub but editing the grub.cfg directly doesn't seem to work. All I want to do is remove entries for earlier kernels (and get rid of earlier kernel files) and comment out some stuff that I don't want to see every time I boot (mainly I have a windows drive with two partitions, one is a recovery partition and I don't want to accidentally boot into that). Am I missing something?

---

### Post by oldfred on 2011-02-26
there is a new gui way that I have not tried:

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)


But I have done it manually with copying entries to 40_custom and turning off os-prober.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by AlexNagy on 2011-03-03
sorry for taking so long, checking it all out now. Thanks!

Update: Success has been had, thanks!

---

