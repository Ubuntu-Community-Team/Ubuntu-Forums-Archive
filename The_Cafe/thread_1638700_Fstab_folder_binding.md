---
title: "Fstab folder binding"
date: 2010-12-06
forum: The Cafe
---

### Post by Oxwivi on 2010-12-06
Can anyone explain what binding folders in fstab do? I've come across this, and tried Googling more info, but it only brings results about how to use it. What exactly does it do?

---

### Post by undecim on 2010-12-06
Fstab is used for mounting.

When you mount, e.g. /dev/sda1 to /media/sda1, the root of the filesystem of sda1 is "mounted" to /media/sda1, so that /media/sda1/somefile.txt is /somefile.txt on the filesystem on sda1.

Binding a folder is very similar. If I bind e.g. /dev to /chroot/dev (chroot is a common use for binds) then the /dev/ folder of my filesystem is mounted to /chroot/dev. /chroot/dev/somedevice is actually /dev/somedevice.

It works like a shortcut to that folder, but at the kernel level, which lets us do things like chroot. With it, whereas symbolic links, wouldn't work. E.g., if I made a symbolic link /chroot/dev to /dev, then under a chroot, /dev/ would be a link to itself, which is entirely useless.

---

### Post by Oxwivi on 2010-12-06
I think I'm getting the picture. Suppose I've a music folder in a different partition, and I bind it to the music folder in my home directory. When I go to the Music folder from places, I will directly go the music folder in the other partition. And whatever I save in my music folder would be saved in that partition, right?

---

### Post by undecim on 2010-12-06
> **Oxwivi said:**
> I think I'm getting the picture. Suppose I've a music folder in a different partition, and I bind it to the music folder in my home directory. When I go to the Music folder from places, I will directly go the music folder in the other partition. And whatever I save in my music folder would be saved in that partition, right?

Right. If you have /media/sda1/Music and bind that to /home/oxwivi/Music, then /home/oxwivi/Music is actually /media/sda1/Music in the same way that /media/sda1 is the / folder on /dev/sda1.

Though for a Music directory in your home folder, a symbolic link should suffice.

---

