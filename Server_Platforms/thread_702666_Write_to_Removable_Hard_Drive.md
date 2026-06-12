---
title: "Write to Removable Hard Drive"
date: 2008-02-20
forum: Server Platforms
---

### Post by sprouty on 2008-02-20
Hi, 

When i connect my hard drive a mount it using the mount command

[PHP]mount /dev/sda1 /share2[/PHP]

Has root i am able to navigate to the hard drive and create files on it. Any other user can browse but not write files to it.

I have tried chmod 777 on the /share2 directory and files inside and also tried the chown command.

Any one got any ideas?

On anorther not is there anyway to atmatically mount the drive on startup?

Cheers

---

### Post by freelinuxhelp on 2008-02-20
hmmm. is this a usb drive? mine are always mounted for me and I never have problems writing to them. 
You can look at /etc/fstab to automount it.
For more information, check this out:
```
man fstab
```

---

### Post by amohanty on 2008-02-20
You can mount it as user

mount /dev/sda /share2 -o "user" 
which will allow ordinary users to mount it. Better yet put it in /etc/fstab
with noauto,users after default.

More details about the mount command:
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

HTH
AM

---

