---
title: "External drive permissions"
date: 2008-04-23
forum: Security
---

### Post by lauriejb on 2008-04-23
I have a LaCie external drive which the system sees perfectly, but the thing is locked to root.  When I try to change the ownership it says that everything is read-only.  sudo chmod does nothing useful, again saying that everything is read only.  I can lift files off, but want to use this as a backup drive.  How can I change the ownership/permissions so that I own it as user?

---

### Post by cdenley on 2008-04-23
What filesystem is on it? If it is ext3 then this command should work
```

sudo chown -R 1000 /media/disk

```
Replace /media/disk with the path where your filesystem is mounted.

---

### Post by thefunnyman on 2008-04-23
If the drive's filesystem is ntfs, you'll have to reformat it.  You cannot set permissions on an ntfs drive in ubuntu, at least I haven't found a way yet.  I have a 320 GB My Book with tons of data on it and it's filesystem is ntfs and it's read/write/execute across the board.  I have no place to put the data so I can reformat it, so I'm stuck.

Hope this helps.

---

### Post by cdenley on 2008-04-23
> 
If the drive's filesystem is ntfs, you'll have to reformat it.


Not unless you need different permissions for individual files/directories.

If you want to give everyone full permission to ntfs filesystems automounted in gutsy/hardy
```

gconftool -s /system/storage/default_options/ntfs-3g/mount_options \
 -t list --list-type string \
[locale=,exec,umask=000]

```
I don't think this is necessary, since it seems to have these permissions by default (at least in hardy).

If you're using a static mount in /etc/fstab, you just have to use options such as uid,gid,umask,fmask,dmask.
```

man mount.ntfs-3g

```

---

### Post by thefunnyman on 2008-04-23
sorry if I end up hijacking this thread, but can you set "other" to being read only for ntfs?  or is it an all-or-nothing kind of thing as far as user access is concerned?

sorry again for going off topic.

---

### Post by lespaul_rentals on 2008-04-23
You may need to open a superuser file manager to write to the drive:

Ubuntu: ```
sudo nautilus
```

Kubuntu: ```
sudo konqueror
```

---

### Post by cdenley on 2008-04-23
> **thefunnyman said:**
> sorry if I end up hijacking this thread, but can you set "other" to being read only for ntfs?  or is it an all-or-nothing kind of thing as far as user access is concerned?

sorry again for going off topic.

Apparently not automatically with the version of ntfs-3g currently in ubuntu.
[http://www.ntfs-3g.org/support.html#unprivileged](http://www.ntfs-3g.org/support.html#unprivileged)

You can do it manually, if the drive isn't already mounted
```

cdenley@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/usb -o uid=1000,umask=022
cdenley@ubuntu:~$ ls -ld /media/usb
drwxr-xr-x 1 cdenley root 4096 2008-04-23 11:56 /media/usb

```

---

### Post by lauriejb on 2008-04-24
Sorry - and thanks for the help everyone - I should have been more explicit.  I'm using Feisty which hasn't any NTFS support built-in.  At least I know now that it wasn't just my incompetence!  I have a long trail in DOS and Windows but Linux is proving something of a steep slope.

I have also now had a look at ntfs-3g, but I suspect the only real answer is to reformat the drive to ext3.  Fortunately when I migrated to Ubuntu from W2000 I shoved all the USB drive stuff onto the PC, and I can now hopefully format without problems.  Just for the record, what is the best/safest way of going about that particular task?  It's a LaCie 250Gb USB drive.

---

### Post by Biochem on 2008-04-24
With Feisty it is very easy to acces with write permission external NTFS drive. All you have to do is

sudo apt-get install ntfs-3g ntfs-config

Then you will have an program (I don't remember the exact name) in Program=>"System tools" that will allow you to configure your NTFS access.

DO NOT format your drive to ext3 if you plan to use it on multiple Windows Computer, because you will need administrator privilege to install the driver required

---

### Post by lauriejb on 2008-04-28
I'm still learning!  I finally discovered that ntfs-3g when installed automatically makes the NTFS files readable and writable (after managing to crash the drive so that it was unreadable and having to go back to XP to dismount it properly - Oh the shame of it) thanks biochem and others.

Interestingly the display of ownership on the drive when viewed from the desktop comes up as root:root but when a file is actually dragged to the PC the ownership reverts to your own.  I suspect that the display on the NTFS filesystem is a default one and the files themselves are not truly owned.  So if you are still there thefunnyman this seems to provide a way to get at your 320GB drive.  I wish you well in that, and thanks again everyone for the help.

---

### Post by jkurtisr32 on 2010-08-12
> **lespaul_rentals said:**
> You may need to open a superuser file manager to write to the drive:

Ubuntu: ```
sudo nautilus
```Kubuntu: ```
sudo konqueror
```


YOU ARE THE MAN. Thanks

---

### Post by bodhi.zazen on 2010-08-12
> **jkurtisr32 said:**
> YOU ARE THE MAN. Thanks

You should not use sudo with graphical apps.

Ubuntu (gnome) or xfce ```
gksu nautilus
```

KDE ```
kdesudo konqueror
```

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by jkurtisr32 on 2010-08-30
> **bodhi.zazen said:**
> You should not use sudo with graphical apps.

Ubuntu (gnome) or xfce ```
gksu nautilus
```KDE ```
kdesudo konqueror
```[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

The solution before worked using sudo. Why is it bad to use with graphical apps?

---

### Post by cariboo on 2010-08-30
When using sudo to run a graphical application, data could be written to /root, making it unavailable unless you run as root. When using gksu or kdesu all the data gets written to the correct directory /home/user

---

### Post by bodhi.zazen on 2010-08-30
> **jkurtisr32 said:**
> The solution before worked using sudo. Why is it bad to use with graphical apps?

The link I gave you discusses this.

The reason has to do with environmental variables, see :

[Difference between sudo su and sudo -s]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

---

