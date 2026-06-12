---
title: "virtualbox doesn't work on 11.04"
date: 2011-04-29
forum: Virtualisation
---

### Post by noworldorder on 2011-04-29
I upgraded from 10.10 to 11.4

Many applications did not show up in the upgrade

I had  to reinstall Virtualbox 4.0 and it doesn't work  !!  :(

"the virtualbox linux kernel driver is either not installed or there is a permission problem"

Help  ... what do I do???

---

### Post by linuxrevo on 2011-04-29
> **noworldorder said:**
> I upgraded from 10.10 to 11.4

Many applications did not show up in the upgrade

I had  to reinstall Virtualbox 4.0 and it doesn't work  !!  :(

"the virtualbox linux kernel driver is either not installed or there is a permission problem"

Help  ... what do I do???

yes same problem here. When I want to install windows 7 it says: a required cd/dvd device driver is missing and list of partitions is empty!!

---

### Post by noworldorder on 2011-04-29
p, li { white-space: pre-wrap; }  > Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.




this is what happens when I try to open XP on virtualbox

---

### Post by Kanna2412 on 2011-05-01
> **noworldorder said:**
> p, li { white-space: pre-wrap; }  




this is what happens when I try to open XP on virtualbox

I too have the same problem. I need immediate solution for this problem. I set up a virtual network on Virtual Box. I have very important work.

Please some body help me fix the issue.

---

### Post by Ferraglia on 2011-05-01
Hello, I fixed this way:
I installed virtualbox-ose-dkms
then
using terminal, sudo /etc/init.d/vboxdrv setup

hope this help.
bye

---

### Post by Kanna2412 on 2011-05-02
I tried reinstalled it and tried the command yesterday. but there is no vboxdrv file in etc/init.d folder. I got error: the file could not find.

Please help me.

---

### Post by johnathansmith on 2012-08-10
Hi, i'm having the same problem with linux kernel. 
Try this
> This is typically due to permission errors. If you installed the version of VirtualBox from the distro and then decide to use the release from VirtualBox.org, the best way to remove the previous install in a Debian based OS is to use the apt-get purge to totally remove the app and configuration settings. Since your guest/s are not effected with a purge they should still be available, but I always tell everyone to backup first.

I also suggest a reboot of the host between the remove and install to make sure all preloaded kernel modules have actually been purged.


---

