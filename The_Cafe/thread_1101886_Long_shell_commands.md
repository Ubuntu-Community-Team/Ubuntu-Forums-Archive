---
title: "Long shell commands"
date: 2009-03-20
forum: The Cafe
---

### Post by PacSci on 2009-03-20
I was practicing my shell command writing skills the other day, and I was wondering how long shell commands can get? It has to be useful, and the commands have to do something related (i.e. not just a string of random commands connected by ";" or "&&"). My best one is:

```
sudo -v; while true; do ps aU person_on_computer | awk '/their-web-browser/ {system("sudo kill " $1)}'; sleep 10; done
```

I just enter my password, and every ten seconds, the Web browser of the person currently sitting in my chair closes. This way, if someone is on the computer and I need to use it, then I just run this command while SSHed in from a laptop upstairs. They'll leave in about five minutes out of sheer frustration. Any more practical and less psychological-warfare-ish commands?

---

### Post by FuturePilot on 2009-03-20
There is no limit. They can be as long as you want.

---

### Post by cardinals_fan on 2009-03-20
There is no limit, but it doesn't take long to reach a point where writing a script would make more sense.

---

### Post by Dr Small on 2009-03-20
> **cardinals_fan said:**
> There is no limit, but it doesn't take long to reach a point where writing a script would make more sense.
To that, I will agree. Thus, why I have alot of scripts in ~/bin

---

### Post by bryonak on 2009-03-20
It doesn't qualify because of the many &&'s, but I'll share it anyway ;)



It takes only three commands to install Gentoo.
```

cfdisk /dev/hda && mkfs.xfs /dev/hda1 && mount /dev/hda1 /mnt/gentoo/ && chroot /mnt/gentoo/ && env-update && . /etc/profile && emerge sync && cd /usr/portage && scripts/bootsrap.sh && emerge system && emerge vim && vi /etc/fstab && emerge gentoo-dev-sources && cd /usr/src/linux && make menuconfig && make install modules_install && emerge gnome mozilla-firefox openoffice && emerge grub && cp /boot/grub/grub.conf.sample /boot/grub/grub.conf && vi /boot/grub/grub.conf && grub && init 6

```
That's the first one.

---

### Post by PacSci on 2009-03-21
I know there isn't a limit, I just wanted to see some long commands people have thought of.

---

### Post by kevdog on 2009-03-21
The && has special meaning.  It only means launch the next command if the previous one successfully executed.  If the prior statement failed to execute, the next set of commands will not be run!  Compare this to ||

---

