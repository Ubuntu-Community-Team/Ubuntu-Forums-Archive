---
title: "I just added a slave HDD how do I configure it to copy a 20GB file?"
date: 2006-03-08
forum: Server Platforms
---

### Post by ttallos on 2006-03-08
I just added a slave HDD how do I mount it? I have server so I need to do it all command prompt.
here is what I have so far as root
fdisk -l   (lists my new drive lets call it hdc)
then     mkdir /media/250GB
then    mount /dev/hdc1 /media/250GB -t vfat -o iocharset=utf8,umask=000
when I try to copy a 20GB file I get errors and only copy 4Gig
the error message says: File Size limit exceeded

---

### Post by terminateprocess on 2006-03-08
Doesn't look like there's anything wrong with the way you're mounting it, but vfat simply doesn't like files any bigger than 2(?) Gigs. Maybe 4 at the most, but if you really need to transfer that file, you probably need to either break it up into small chunks (if you can do that) or reformat the drive to a filesystem that supports files that big. Seeing that you made it vfat, I'm kind of assuming that you need it readable in windows? Unfortunately, if that's the case, vfat is the only filesystem that is both readable and writable by both windows and linux, as far as I know.

---

### Post by ttallos on 2006-03-08
Thanks... I was thinking that what I need to do is go to a new ubuntu machine (5.10) that I installed at work that is malfunctioning, get the files off of it (1 backup file is 20 Gig) I was hoping to just copy the backup file to a hdc and xfer it to the new ubuntu server that I have just built. It looks like I will just have to have the backup program start over on the new server that is crummy. Hoping for some stability. By the way thanks for the help.

---

### Post by ttallos on 2006-03-08
The funny thing is that I can take a windows machine and open up a share to ubuntu machine 1 and ubuntu machine 2 and xfer the 20gig file that way. Long live samba.

---

