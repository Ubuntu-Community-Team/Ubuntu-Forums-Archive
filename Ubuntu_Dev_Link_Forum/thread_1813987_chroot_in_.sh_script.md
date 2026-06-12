---
title: "chroot in .sh script"
date: 2011-07-28
forum: Ubuntu Dev Link Forum
---

### Post by jmlaguiness on 2011-07-28
Hello:)
I'm trying to do a custom live cd, and for that I need to chroot on a folder to install the various packages and configure the system correctly.
No problem right there, but when I try to do the same thing using a sh script,  putting the exact same comands in the same order, all seems fine, I have good feedback on the screen.
But after a while It feels like that the shell "zaps" the chroot, without arriving at the exit .. And then he starts to put a joyful mess with MY distribution paqueges il results a monster crash  with corruption of the system partition (okay I have an image but ...)
Below is the piece of code in question (do not try as is especially Linux viruses do not exist, but these lines come close though ...)

```

mount --bind /dev FileSystem/dev
# CHROOT
cd Filesystem
chroot .
#MOUNT
mount none -t proc /proc
mount none -t sysfs /sys
mount none -t devpts /dev/pts
export HOME=/root
export LC_ALL=C
#sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678  #Substitute "12345678" with the PPA's OpenPGP ID.
apt-get update
apt-get install --yes dbus
apt-get install -y ubuntu-standard
apt-get install -y casper
apt-get install -y lupin-casper
[lots of more]

#UNMOUNT
umount -lf /proc
umount -lf /proc
umount -lf /sys
umount -lf /dev/pts
#EXIT CHROOT
exit
umount FileSystem/dev

```

Someone knows how to fix it ?

Thanx ;)

---

### Post by Bachstelze on 2011-07-30
First, you should mount /dev and /proc *before* running chroot!

Second, the commands after the chroot line *will not* run in the chroot! chroot works somewhat similarly to sudo, you can't have a script like this:

```
#!/bin/sh

sudo -i
command....
```

Because sudo -i will spawn a new shell process, and the script will oly proceed after the sudo command (i.e. the shell) has terminated. The same applies to chroot. There are two ways to achieve what you want: either prefix all your commands with chroot (once again, in the same way as with sudo), like this:

```
mount -t proc none /mnt/root/proc
mount -o bind /dev /mnt/root/dev
chroot /mnt/root apt-get...
```

Or you can make a shell script with all the commands that must be run in the chroot and do

```
chroot /mnt/root blah.sh
```

---

### Post by nerdopolis on 2011-07-30
When you run chroot, chroot is actually calling another instance of bash, so the rest of the script is not run in chroot, but in your normal system.



If I had a script file I wanted to run as chroot at /media/chroot/chrootscript I would run 

```
chroot /media/chroot /chrootscript
``` 


You should put the rest of the script in the chroot, and call it like that.

---

