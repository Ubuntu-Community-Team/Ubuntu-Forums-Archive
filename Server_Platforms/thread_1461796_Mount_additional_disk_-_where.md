---
title: "Mount additional disk - where?"
date: 2010-04-24
forum: Server Platforms
---

### Post by Kljuka on 2010-04-24
Hi,
I've bought an old DELL server. I've got 73GB raid disk in it. It's very small, so I've bought additional 1.5TB disk (and connected it to PCI card). I want to use this server as a web server for more than 1 user. I was thinking to have my home directory on 73GB disk (it's a RAID disk), but others should have it on 1.5TB disk.

Where should I normally mount additional 1.5TB hard disk? What's the normal way of doing this?
Should I mount it in /mnt/storage and create symbolic links from /home/<username> to /mnt/storage/<username> ?

---

### Post by Bachstelze on 2010-04-24
You can mount it pretty much anywhere, but if the disk doesn't have a particular purpose, /mnt/something is a reasonable choice, yes. Also you don't (and really, shouldn't) create symlinks for home folders. The home folder of a user does not necessarily have to be /home/user, it can be /mnt/storage/user, or basically anything. You define the home folder of a user, along with his login, password, etc., when you create the account.

---

### Post by Kljuka on 2010-04-24
Thank you Bachstelze for help.

---

### Post by ajgreeny on 2010-04-24
> **Bachstelze said:**
> You can mount it pretty much anywhere, but if the disk doesn't have a particular purpose, /mnt/something is a reasonable choice, yes. [COLOR=Red]Also you don't (and really, shouldn't) create symlinks for home folders.[/COLOR] The home folder of a user does not necessarily have to be /home/user, it can be /mnt/storage/user, or basically anything. You define the home folder of a user, along with his login, password, etc., when you create the account.
Can you explain exactly what you mean by that, please.  I have a partition that I use to test new linux distros, including Ubuntu, as well as my main Ubuntu 9.10 OS partition, and I always mount the separate /home partition of the main OS in /mnt of the test OS, and link the data folders from the new home folder to the main home data folders.  It works without a problem of any sort, though I keep all the hidden configuration folders of one OS separate from the other OS to avoid any conflicts of application versions etc etc.

Are you saying that this is not a good idea, or just that to link the whole /home partition from one to the other is not good?

---

### Post by Bachstelze on 2010-04-24
> **ajgreeny said:**
> Can you explain exactly what you mean by that, please.  I have a partition that I use to test new linux distros, including Ubuntu, as well as my main Ubuntu 9.10 OS partition, and I always mount the separate /home partition of the main OS in /mnt of the test OS, and link the data folders from the new home folder to the main home data folders.  It works without a problem of any sort, though I keep all the hidden configuration folders of one OS separate from the other OS to avoid any conflicts of application versions etc etc.

Are you saying that this is not a good idea, or just that to link the whole /home partition from one to the other is not good?

You can of course create symlinks inside your home folder that point anywhere, what I was referring to is if your home folder is, say, /home/user, but /home/user is in fact a symlink to some other dir. While it technically works, it can create confusion (for example the user could be unsure where his home directory is actually located) and permission problems. If you want all your home directories to be in some other folder than /home, it's better to define that at creation-time instead of creating symlinks all over the filesystem.

---

### Post by ajgreeny on 2010-04-24
OK, thanks.  I now see what you mean.

---

### Post by Kljuka on 2010-04-24
What happens if you put /home on additional disk and this disk fails?
Does the server freeze? Can these users still log in?

---

### Post by Bachstelze on 2010-04-24
The server doesn't freeze and users can still log in. If the system can't access a user's directory when they log in, it sets their home directory to / (no, it doesn't give them write permission on it :p). Needless to say, users can't do much after they login when this happens, but it doesn't make the system unusable.

---

### Post by Vegan on 2010-04-24
I have a USB disk and I plug it in, but the machine is headless so I use webmin to mount it and then I can tar up everthing in case of yet another failure.

This disk is in a case, so I yank it now rather than use a slave disk like I was before that bit me.

A nuisance, but until I get more servers its going to have to do.

Lately I have been even more lazy, now I use the USB disk on the WIndows box and use SAMBA shares to allow me to backup.

This is because I have a KVM on the Windows box while the Linux box has nothing but storage.

---

### Post by windependence on 2010-04-24
> **Vegan said:**
> I have a USB disk and I plug it in, but the machine is headless so I use webmin to mount it and then I can tar up everthing in case of yet another failure.

This disk is in a case, so I yank it now rather than use a slave disk like I was before that bit me.

A nuisance, but until I get more servers its going to have to do.

Lately I have been even more lazy, now I use the USB disk on the WIndows box and use SAMBA shares to allow me to backup.

This is because I have a KVM on the Windows box while the Linux box has nothing but storage.
This relates to the OP how? 

Why not just mount the disk from the command line using SSH? Seems a bit much to install WebMin just to mount a disk.

-Tim

---

