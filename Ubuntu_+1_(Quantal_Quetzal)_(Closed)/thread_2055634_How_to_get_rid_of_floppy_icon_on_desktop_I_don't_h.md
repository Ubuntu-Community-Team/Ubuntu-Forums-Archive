---
title: "How to get rid of floppy icon on desktop? I don't have one!"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fedleo on 2012-09-09
I just upgraded my old-but-good P3 Notebook from xubuntu 12.04 to 12.10. 
On my desk (see pic) I have TWO floppies icons but I don't have even one. 
The discs are not mounted nor I can remove them. I Already deleted entry on fstab but floppies are still presents. 
I know I can disable removable icons (even if it's not an option for me) from desktop settings panel, but doing so ONE icon still remain. Where are stored XFCE removable media informations?

Before someone ask me to SEARCH here is the latest entry I found about this iussue: [http://ubuntuforums.org/showthread.php?t=1308102](http://ubuntuforums.org/showthread.php?t=1308102)
but didn't help. :(

Thanks,

F.

---

### Post by oldos2er on 2012-09-09
Moved to Ubuntu +1 (Quantal Quetzal).

---

### Post by cariboo on 2012-09-09
Check to see if the floppy module is loaded, and if it is, blacklist it. The blacklist files are located in /etc/modprobe.d

---

### Post by fedleo on 2012-09-11
> **cariboo907 said:**
> Check to see if the floppy module is loaded, and if it is, blacklist it. The blacklist files are located in /etc/modprobe.d```
effe@C400:/etc$ modprobe -l|grep floppy
kernel/drivers/block/floppy.ko
```
I tried to add it to blacklist.conf with```
blacklist floppy
``` but without results. Even if I remove the floppy.ko the drivers still remains there.```
effe@C400:/etc$ sudo rm /lib/modules/3.5.0-14-generic/kernel/drivers/block/floppy.ko
```

---

### Post by cariboo on 2012-09-11
You have to unload the floppy module, using the following command:

```
sudo rmmod floppy
```

Then you can blacklist it.

Trying to remove the module before unloading it, isn't going to work.

---

### Post by mips on 2012-09-12
> **fedleo said:**
> 
On my desk (see pic) I have **TWO** floppies icons but I don't have even one. 

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375)
[http://ubuntuforums.org/showthread.php?t=2053504](http://ubuntuforums.org/showthread.php?t=2053504)

---

### Post by GeForce 9500GT on 2012-09-12
Did you also diabled the floppy in your BIOS if this can be done on your laptop? Just a thought i had...

---

### Post by fedleo on 2012-09-12
> **cariboo907 said:**
> You have to unload the floppy module, using the following command:

```
sudo rmmod floppy
```

Then you can blacklist it.

Trying to remove the module before unloading it, isn't going to work.Done but one floppy icon still remain.
> **mips said:**
> [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375)
[http://ubuntuforums.org/showthread.php?t=2053504](http://ubuntuforums.org/showthread.php?t=2053504)Thnaks for the links. I am subscribed to all notifications for this bug now.
> **GeForce 9500GT said:**
> Did you also diabled the floppy in your BIOS if this can be done on your laptop? Just a thought i had...Yes. I have removed any option related in my BIOS.

**Edit: After a classic apt-get upgrade and a reboot even the second icon is gone. Thanks to all.**

---

