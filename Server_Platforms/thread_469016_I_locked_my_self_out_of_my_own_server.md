---
title: "I locked my self out of my own server"
date: 2007-06-09
forum: Server Platforms
---

### Post by etechship on 2007-06-09
I have made my file system read only by editing the /etc/fstab file wrongly. I have tried to use Knoppix, but I can't get it to mount my hard drive.

I can log in and access the server just fine, I just can't write anything on it, and I  get lots of errors when loggin in.

I heard somewhere that ubuntu had restore floppies. I don't know itf that would help or not. I already tried using the restore disc, but either shells don't give me the access that I need to change that file back

thanks
dave

---

### Post by turinglabs on 2007-06-09
Try remounting it read-write on the fly, for example if I had the root filesystem mounted on /dev/sda1:

sudo mount -o remount,rw /dev/sda1

---

### Post by etechship on 2007-06-09
I did what you said, and this is what I typed.

I did mount -l to find my root filesystem, then I did sudo mount -o remount,rw /dev/ida/c0d0p1 to remount it, and I got this error mount: / not mounted already, or bad option

thanks
dave

---

### Post by NeoGreen on 2007-06-09
Man, I am having the same issue.  But with me I can't even ssh to it and my web site is down.

---

### Post by gombadi on 2007-06-10
> **etechship said:**
> 
I did mount -l to find my root filesystem, then I did sudo mount -o remount,rw /dev/ida/c0d0p1 to remount it, and I got this error mount: / not mounted already, or bad option


Not mounted means that it can't remount it so just try to mount normally.

If you are using knoppix then ls -l /mnt to see what partitions it can see on the hard drive then mount the partition on the correct mount point in /mnt

ie mount /dev/ida/c0d0p1 /mnt/somedirectory 

Then you can change to /mnt/somedirectory/etc and copy fstab.original to fstab
You did make a backup copy of the file before editing didn't you?
That is what is called experience :)

What changes were you making to /etc/fstab

---

