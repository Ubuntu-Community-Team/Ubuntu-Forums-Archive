---
title: "Problem instaliing realtek alsa driver"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by hempar on 2008-05-11
I was trying to install realtek alsa driver but when i came to step when i need to copy files i am getting error. need help

Following step i did

hemant@hemant-desktop:~$ sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`

hemant@hemant-desktop:~$ sudo mkdir -p /usr/src/alsa

hemant@hemant-desktop:~$ cd /usr/src/alsa

hemant@hemant-desktop:/usr/src/alsa$ sudo cp /home/hemant/realtek/alsa*

Here I'm getting following error message

cp: target `/home/hemant/realtek/alsa-utils-1.0.15.tar.bz2' is not a directory

---

### Post by XTO HACPAB on 2008-06-09
I have the same problem with alsa and that utils! Please Help!!!

---

### Post by ocarinahuff on 2008-08-11
> **hempar said:**
> I was trying to install realtek alsa driver but when i came to step when i need to copy files i am getting error. need help

Following step i did

hemant@hemant-desktop:~$ sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`

hemant@hemant-desktop:~$ sudo mkdir -p /usr/src/alsa

hemant@hemant-desktop:~$ cd /usr/src/alsa

hemant@hemant-desktop:/usr/src/alsa$ sudo cp /home/hemant/realtek/alsa*

Here I'm getting following error message

cp: target `/home/hemant/realtek/alsa-utils-1.0.15.tar.bz2' is not a directory

You didn't type where you want to copy those files to.  Use:
sudo cp /home/hemant/realtek/alsa* /usr/src/alsa/
or
sudo cp /home/hemant/realtek/alsa* .
(single dot means current directory)

---

