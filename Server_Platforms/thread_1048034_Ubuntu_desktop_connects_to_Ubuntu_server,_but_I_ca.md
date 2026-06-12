---
title: "Ubuntu desktop connects to Ubuntu server, but I cannot explore to the server drive!"
date: 2009-01-23
forum: Server Platforms
---

### Post by daaussie on 2009-01-23
Ok, so i have a ubuntu workstation which has thunderbird (i want email file on ubuntu server), I have wine (with myob installed), the access file is on server.

I can access the server from the machine by going to places>network>connect to server> etc, -AND- have created desktop shortcuts to the server files we regularly access.

But when I try to re-direct thunderbird email file or get MYOB (accounting) to read from server (rather than workstation) location, but when I scroll all i find is the workstation folders.

Please help.

Also, I don't know why Ubuntu 8.10 doesnt give Openoffice 3.0, and I am new to this, what's an easy way to upgrade?

Thanks.

---

### Post by daaussie on 2009-01-23
please help guys/girls.:p

---

### Post by capscrew on 2009-01-23
Okay...

If you want to see the share by browsing the file system folders, you need to mount the share to the file system. 

Try mounting the share to a mount point in the system.  It would look something like this:```
sudo mount -t cifs //server/share /mnt/mydirectory  -o user=user password=password
```

---

### Post by daaussie on 2009-01-24
Yes mounting works. you can also make a script through terminal which mounts on each boot. Now I have a desktop shortcut to MYOB working on v8.10 using WINE.
Yahoo!!!!

---

### Post by capscrew on 2009-01-24
Actually, you can mount it through the /etc/fstab file.  That's what it is for -- automount at bootup.  Checkout:```
man fstab
```

---

### Post by Iowan on 2009-01-24
More **fstab** info [here]("http://ubuntuforums.org/showthread.php?&t=283131").

---

