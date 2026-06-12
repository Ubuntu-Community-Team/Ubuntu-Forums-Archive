---
title: "Select OS in multiboot Server 10.04 without keyboard/display?"
date: 2010-07-19
forum: Server Platforms
---

### Post by FransKlip on 2010-07-19
Is there a way to select a second installed OS on a home server system without display and keyboard?

 I am putting together a home server (for mail, storage, media streaming) using an Atom-based Ubuntu Server 10.04 on a 4 GB intern flash drive and 2 hard drives for data storage, but no display or keyboard.
 I want to make periodic full backups of the system (flash) disk and use a second OS (installed on a partition on the hard drive) with a graphical interface  (e.g. Xbuntu or PartImage) for maintenance purposes. I can connect remotely (from a Win7 or a Linux computer) to the X-display once the second system is running.
 
Now I see two problems:  
 a) how can the second OS be booted on this server without keyboard?  
 Is there a way to tell Grub2 to look at some hardware switch (or file) for the menu selection? The board has a serial and parallel port so I could wire up a switch to some pin of one of these. 
Also external USB connectors are available on front and back. 
Or can Grub2 read its default OS choise from some simple file, easily to change from a shell command of the eBox webbased system control internface?   

 b)  I assume the second OS is needed to make a complete backup of the server OS on the flash disk. Can the backup be automated? (i.e. switch to second OS, backup, reboot first OS)

Thanks

---

### Post by doogy2004 on 2010-07-19
GRUB_DEFAULT may be what you are looking for.  But I'm not quite sure how you would pull it off.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by spynappels on 2010-07-20
You can do this without dual booting, just install X server and forward through a ssh tunnel, it allows you to run GUI programs from a headless server. Or you can install a desktop environment and only run it when you need it rather than at boot. Or use Webmin/Ebox and learn the CLI at your own pace....

You could also look at setting up LVMs so you can save a snapshot of the disk easily. Although I would suggest you put /var and /home on one of the data storage disks. Then the Flash drive has little or no changing data on it and you could just do a dd to a backup flashdrive.

Generally, dual booting a server is considered counterproductive.

---

### Post by FransKlip on 2010-07-21
> **doogy2004 said:**
> GRUB_DEFAULT may be what you are looking for.  But I'm not quite sure how you would pull it off.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
thanks, 
there are some interesting features (user defined grub configuration file, one-time boot different system), but I will have to read it better and try it (in a virtual system). I hope the hardware arrives before the weekend.

---

### Post by FransKlip on 2010-07-21
> **spynappels said:**
> You can do this without dual booting, just install X server and forward through a ssh tunnel, it allows you to run GUI programs from a headless server. Or you can install a desktop environment and only run it when you need it rather than at boot. Or use Webmin/Ebox and learn the CLI at your own pace....

You could also look at setting up LVMs so you can save a snapshot of the disk easily. Although I would suggest you put /var and /home on one of the data storage disks. Then the Flash drive has little or no changing data on it and you could just do a dd to a backup flashdrive.

Generally, dual booting a server is considered counterproductive.

Thanks.
I Installed Xubuntu on top of Server ('apt-get install xfse-desktop' , it which appears to use a lot of GNome programs) in a virtual system, but then already 75% of my 4 GB disk was in use (before it was 28% in use). Removing a lot of desktop applications, and 'apt-get purge' reduced disk usage to 69%, but still too much for a server that has not done anything yet.
I probably will stick to the command line (I used to program computers that way 25 years ago). Perhaps I'll try X-only, 

For the data disks I will use LVM but I didn't plan to use it - or raid - on the system (flash) disk. But I will have a closer look; it might also be handy when replacing the flash disk.

---

