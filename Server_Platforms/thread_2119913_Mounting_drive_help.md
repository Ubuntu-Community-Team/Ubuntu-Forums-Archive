---
title: "Mounting drive help"
date: 2013-02-25
forum: Server Platforms
---

### Post by doomdragon on 2013-02-25
Hi,

A little problem. 
I am running Ubuntu 12.04 server and have two hard disks formatted in ext4 and LVM'd them together as one drive.
I wish to mount the drive on boot up but am having trouble. I obviously do not want to mount the drive 
to the folder in my user area ( I am running 12.04 from a USB) and not sure where to mount it to. 
I have tried creating a folder in the /media folder but throws a wobbly on reboot.
I plan to use this drive as a storage area for music and other media so need it accessible from a windows client machine.
Cheers for your help.

---

### Post by fdrake on 2013-02-25
> **doomdragon said:**
> Hi,

A little problem. 
I am running Ubuntu 12.04 server and have two hard disks formatted in ext4 and LVM'd them together as one drive.
I wish to mount the drive on boot up but am having trouble. I obviously do not want to mount the drive 
to the folder in my user area ( I am running 12.04 from a USB) and not sure where to mount it to. 
I have tried creating a folder in the /media folder but throws a wobbly on reboot.
I plan to use this drive as a storage area for music and other media so need it accessible from a windows client machine.
Cheers for your help.
post from terminal the output of:
```

sudo fdisk -l

```

---

### Post by doomdragon on 2013-02-25
I will get back to you when I get home from work. I thought I could SSH to the server but I think it is being blocked via the proxy here. Cheers

---

### Post by schragge on 2013-02-25
I guess you know it, but just to be sure: in order to access a logical volume the package *lvm2* needs to be installed.

I have this in my */etc/fstab*:
```

UUID=1d308560-a147-4aa0-94e6-eb0984390270 /mnt/data ext4 nodev,nosuid 0 0

```
[list=1]
[*]For this to work, the directory */mnt/data* should exist.
[*]You can get UUID for your drive with the *blkid* command.
[/list]

Since you intent to share the drive over network, */srv/data* or */export/data* would probably be better than */mnt/data* in your case. Instead of *data*, you can name your mount point whatever you like, e.g. */srv/public*.

---

### Post by doomdragon on 2013-02-25
I will try that. I am sure lvm2 is installed but will check just in case. 
I will try an alternative folder for it to mount to so I can share that disk space on the network, cheers for the help I will get back back to if I manage to succeed. Rather annoying as I have never had trouble with mounting via fstab before. Perhaps not having a GUI is confusing me! 
Cheers!

---

### Post by doomdragon on 2013-02-26
Cheers, 
have changed the folder and all is now sorted until I overkill it and turn it into a Domain controller (just so that I can do it for the fun of it!)

---

### Post by bab1 on 2013-02-26
> **doomdragon said:**
> Cheers, 
have changed the folder and all is now sorted until I overkill it and turn it into a Domain controller (just so that I can do it for the fun of it!)
Hold on there a second.  You should ***not*** mount LVM volumes with the UUID.  There's a bug using that method.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11349886&postcount=2") for why that is so.  Mount all LVM volumes by /dev/

---

### Post by doomdragon on 2013-03-03
Ah! Thanks for the warning, appreciated!

---

