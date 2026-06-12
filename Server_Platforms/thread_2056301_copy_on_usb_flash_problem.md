---
title: "/ copy on usb flash problem"
date: 2012-09-11
forum: Server Platforms
---

### Post by nikibg on 2012-09-11
Hello i have linux distribution  i wanna copy / directory to usb flash drive 

first i had format usb in 2 partitons one fat 16 and one ext2 
then i mounted usb and ```
cp -r / .
``` but it show me :

cp: can't open '/proc/sys/net/ipv4/route/flush': Permission denied
where is the problem :S

---

### Post by dozdozez on 2012-09-11
This command will try to copy your whole system in the usb flash drive, including all sysem files (some of them can only be accessed by root, other "files" are just the devices in your computer),  and the flash drive itself (mounted in /media/...).

The error you get is that you can't read a file that your unprivileged user has no permission to read so that's ok.

maybe what you want to do is copy your home directory, where there are all your personal files and settings, in that case type:
```

cp -r /home/(your username)/ .

```

Some programs store some information in other directories so if you want to make a whole backup you need them, I can't thell you where are they cause i don't know. (for example evolution stores e-mail acount information and passwords out of your /home)

---

### Post by nikibg on 2012-09-11
I wanna copy whole system in the usb flash drive 

how i can copy it

---

### Post by trundlenut on 2012-09-11
> **nikibg said:**
> I wanna copy whole system in the usb flash drive 

how i can copy it

Do you have a cd/dvd drive?

If so boot the machine with a live CD then copy the file system from the hard drive to the usb this way rather than trying to copy a running system.

Why are you trying to do this anyway?

---

### Post by nikibg on 2012-09-11
I dont have cd / dvd

I have image file with linux and I boot it from usb flash but it make RAM disk and i wanna storage some info or change something and this is the way that i came up with

---

### Post by dozdozez on 2012-09-11
I would use dd, but it can be done with the cp command, look this link:

[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

---

### Post by nikibg on 2012-09-11
thanks guys :popcorn:

---

