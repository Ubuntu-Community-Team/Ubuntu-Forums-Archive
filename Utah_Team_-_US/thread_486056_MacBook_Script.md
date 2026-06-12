---
title: "MacBook Script?"
date: 2007-06-27
forum: Utah Team - US
---

### Post by troseph on 2007-06-27
Hey guys, I have a macbook running a CoreDuo 2.0Ghz And I can't get Ubuntu to install properly on it. Every time I do get it to install my mouse (usb or the touch pad) doesn't work. It is really jerky and slow. I ran into thenetduck yesterday, and he said there is a script available that fixes the problem. Also, what should I use for a boot loader? I can't get the installer for 7.04 to allow me to select no boot loader or lilo. Any help you can give me would be awesome!

---

### Post by benanzo on 2007-06-27
The standard installer wont let you continue without installing a bootloader.  It defaults to GRUB, but you can just uninstall it after its done and install LILO instead, if thats what you want.

---

### Post by troseph on 2007-06-27
The problem is that Grub doesn't load. So I can't just replace it. :) I need to mount my install on the HD and chroot into bin/bash but I can't remember how to do that. Sometihng like mount -t proc none /target/proc etc etc... But I just can't remember the commands. If someone could tell me those I will be set. :)

---

### Post by Zelut on 2007-06-27
I am running Ubuntu on a macbook.  I am putting together a tutorial on installation.  If you can wait a day or so I'll try to get that posted for you on my blog...

sounds like you might be looking for rEFIt though.  Check out [http://help.ubuntu.com/community/MacBook](http://help.ubuntu.com/community/MacBook) for some tips in the meantime.

---

### Post by benanzo on 2007-06-27
to chroot into an Ubuntu install:

Change to root:
```
sudo bash
```
make a dir for your root partition:
```
mkdir /mnt/ubuntu
```
mount your system:
```

mount /dev/sda1 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev

```
chroot in:
```
chroot /mnt/ubuntu /bin/bash
```

---

### Post by troseph on 2007-06-27
Benanzo, you're a saint. :P

---

### Post by thenetduck on 2007-06-28
This is what I used to get everything up and running. Worked nicely ;) 
[http://www.mikesplanet.net/ubuntu-704-on-a-macbook-pro/](http://www.mikesplanet.net/ubuntu-704-on-a-macbook-pro/)  -  Thank you Mike

---

### Post by troseph on 2007-06-30
that worked perfect netduck. Thanks. :) I'm sure glad I happened to run into you.

---

### Post by thenetduck on 2007-06-30
Bah I just had the link Mike is the real hero ;)

---

