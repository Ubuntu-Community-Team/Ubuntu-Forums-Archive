---
title: "[SOLVED] Cant mount server drive in fstab"
date: 2008-05-31
forum: Server Platforms
---

### Post by Twizzle on 2008-05-31
I am trying to have my desktop PC automount a drive on my server at boot. The drive is NTFS as it is also used by an XP machine, and is automounted in the server. I put this in my fstab:

```
//server/Data	/home/Data	smbfs	username=name,password=pass   0	0
```

but it does not work. /home/Data is created and I can mount the drive normally.

---

### Post by quelx on 2008-05-31
from the terminal does ```
sudo smbmount //server/Data /home/Data --verbose -o user=name password=pass
``` work?

---

### Post by Twizzle on 2008-05-31
I get:
 ```
sudo: smbmount: command not found
```

---

### Post by quelx on 2008-05-31
> **Twizzle said:**
> I get:
 ```
sudo: smbmount: command not found
```

Do you have the samba client tools installed?

```
sudo apt-get install samba-common
```

---

### Post by Twizzle on 2008-05-31
I am sure they are installed and I get:

```
john@office:~$ sudo apt-get install samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 guile-1.6 libgoffice-0-common libgoffice-0-4
  libcrypt-ssleay-perl libdate-manip-perl slib libgsf-gnome-1-114
  libfinance-quote-perl guile-1.6-slib libhtml-tableextract-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

If I try again.

---

### Post by Krydahl on 2008-05-31
If you're using Hardy, smbfs is no longer supported. Try cifs.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by quelx on 2008-05-31
does ```
whereis mount.*
```
show a **mount.smbfs** or **mount.cifs**

what does
```
sudo apt-get install smbfs
```
give you

---

### Post by quelx on 2008-05-31
> **Krydahl said:**
> If you're using Hardy, smbfs is no longer supported. Try cifs.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

But it works, they are all part of the **smbfs** package

---

### Post by Twizzle on 2008-05-31
```
john@office:~$ whereis mount.*
mount: /bin/mount /sbin/mount.ntfs-3g /sbin/mount.ntfs /sbin/mount.smbfs /sbin/mount.fuse /sbin/mount.cifs /usr/share/man/man8/mount.8.gz

```

and 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  guile-1.6 guile-1.6-slib libcrypt-ssleay-perl libdate-manip-perl 
  libfinance-quote-perl libgoffice-0-4 libgoffice-0-common 
  libgsf-gnome-1-114 libgtkhtml3.8-15 libhtml-tableextract-perl slib 
The following NEW packages will be installed:
  smbfs 
0 packages upgraded, 1 newly installed, 11 to remove and 0 not upgraded.
Need to get 94.0kB of archives. After unpacking 11.1MB will be freed.
Do you want to continue? [Y/n/?] 

```

I chose Yes - I guess it was not installed properly?

---

### Post by Twizzle on 2008-05-31
And now this:
```
sudo smbmount //server/Data /home/Data --verbose -o user=name password=pass
```

worked! Thanks :)

Although it did prompt me for my password again?

---

### Post by Krydahl on 2008-05-31
Use smbfs in your fstab in Hardy and you'll get:

mount error 20 = Not a directory

There are quite a few threads around about this.

---

### Post by quelx on 2008-05-31
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

outlines a better way (see the **~/.smbcredentials** part) to mount drives with user/pass.

---

### Post by Twizzle on 2008-05-31
It works! Thank you so much. :)

---

### Post by Twizzle on 2008-05-31
Bugger ... spoke to soon.

I logged out then in again and the drive was mounted. Rebooted and got and error on shutdown:

CIFSVFS: Server not responding
CIFSVFS: No response for cmd 50 mid 76.

I had to press the reset button to reboot and now I am back in, it is not mounted.

---

### Post by Twizzle on 2008-05-31
If I try
```
sudo mount -a
```

I get

```
error 2 opening credential file ~/.smbcredentials
```

---

### Post by Twizzle on 2008-05-31
I really should read to the bottom of a post. Changing ~/.smbcredentials to /home/john/.smbcredentials solved it.

Still get the message on shutdown but not too fussed about that now.

Thanks again for your help.

---

### Post by quelx on 2008-05-31
Here is a thread the describes the problem (with an apparent solution, but I don't think it applies...)

[http://ubuntuforums.org/showthread.php?t=410206](http://ubuntuforums.org/showthread.php?t=410206)

try switching up the **smbfs** and **cifs** in the fstab line for the share.

EDIT: nevermind, glad its working for you now...

---

