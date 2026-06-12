---
title: "Downgrade from 19.04 to 18.10 or 18.04"
date: 2019-03-29
forum: Ubuntu Development Version
---

### Post by mrjakso on 2019-03-29
Hello,

I've just upgraded to 19.04, after some time watching how everything works, it came to my attention that some browsers are lagging on scrolling, so i guess i will be going back to 18.10 for time that 19.04 is still beta, and after it's stable release i will upgrade to it, but my question here is:

How can i downgrade from 19.04 to 18.10? I never done that before and i want to keep all my data.

Thanks.

---

### Post by Frogs Hair on 2019-03-29
Hello 

Ubuntu 19.04 is still in development and if you are new to Ubuntu  please stick to supported versions unless you want to test . There is no downgrade option for Ubuntu so backup your files and install 18.04 or 18.10. 

Moved to Ubuntu Development Version.

---

### Post by mrjakso on 2019-03-29
I know it is still in development, that's why i've upgraded to it, i've wanted to check new features but like i said, for some windows (for example Discord, scrolling page is lagging) and i said to myself i can't work like that (i'm developing discord bots) so i want to downgrade for 18.10, if there is no official downgrade option, i guess i need to back up my files, thank you!

---

### Post by jdeca57 on 2019-03-29
I think you need to reinstall but that doesn't mean you would lose data if your home is on a separate partition. And if it isn't then this is the moment to think about good backups but then of course you're making them in Ubuntu 19.04 and who knows what the state of the backup software is there? Did you make a backup before upgrading?

---

### Post by dino99 on 2019-03-29
As it is an upgrade, dont forget to clean the system, to purge old packages versions and their settings as they  often disturb the system.
Use 'gtkorphan' and 'bleachbit' (as root, but carefully select options) to clean up the system, then do a cold reboot., then glance to the log (journalctl -b) to detect warnings/errors (if any)

---

### Post by oldfred on 2019-03-29
Best to always keep your main working install and create a new partition for any test installs.

If you have all your data in a separate data partition, the /home with your mostly hidden settings are small, so you can do a test install, copy /home into it and mount your data partition.

I use 25GB for / (root), not showing smaller folders. 

```
fred@Bionic-Z170N:~$ sudo du -hx --max-depth=1 / 2> /dev/null
[sudo] password for fred: 
...
535M    /home
...
5.2G    /usr
...
8.4G    /

```

```
        fred@Bionic-Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4        25G  8.4G   16G  36% /
/dev/sda1        50G   79M   50G   1% /boot/efi
/dev/sdb6       298G   48G  235G  17% /mnt/data
/dev/sdc3        20G  5.9G   13G  32% /media/fred/root128
/dev/sdc4        94G   14G   76G  15% /media/fred/data128
/dev/sdb4       146G   46G   93G  33% /mnt/backup 
/dev/sdb2        30G  4.0G   25G  15% /media/fred/bionic_b
/dev/sdb8        24G  6.6G   17G  30% /media/fred/disco
    
```

Note: I had typo on creation of ESP and it should be 500MB not 50GB. But have not yet needed space for another install or data.

---

### Post by monkeybrain20122 on 2019-03-29
> **mrjakso said:**
> I know it is still in development, that's why i've upgraded to it, i've wanted to check new features but like i said, for some windows (for example Discord, scrolling page is lagging) and i said to myself i can't work like that (i'm developing discord bots) so i want to downgrade for 18.10, if there is no official downgrade option, i guess i need to back up my files, thank you!

There are less risky ways to test new features, you can e.g, have a spare partition for testing, or install in an external hd. It is a very bad idea to trade in a stable, working system to a beta just to 'check new features' (unless you are not really using the system for anything important) Also "upgrade" is always problematic, when you really want the new OS, back up your data and do a clean install,  a lot faster and save you a lot of potential problems.

---

