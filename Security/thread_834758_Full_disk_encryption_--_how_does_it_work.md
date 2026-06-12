---
title: "Full disk encryption -- how does it work?"
date: 2008-06-19
forum: Security
---

### Post by RichPowers on 2008-06-19
Hey everyone,

I just installed Ubuntu 8.04 on my desktop using full disk encryption; this is my first experience with Linux. I have a few questions about full drive encryption that I would like answered before I migrate my important data to this new build.

1) Three logical volumes were created in the encrypted space: /, swap, and /home. The unencrypted /boot was created automatically.

Do these volumes act like physical partitions? For example, if I reinstalled Ubuntu, could I format / and leave /home unaffected, as you could with a regularly partitioned system? I'm uncertain how these volumes function relative to standard partitions.

2) How does full drive encryption actually *work*? I enter my password at boot and Ubuntu loads. Ok. But when is data actually encrypted/decrypted?

3) Is there a way to set the system to prompt me for my encryption password after I'm away for X minutes? Will hibernate cause the system to be encrypted?

4) How would backups work? If I create an rsync backup job and send it to a file server, will the data be encrypted and therefore unreadable?

Basically, I don't want to lose any valuable data because I'm inexperienced with full drive encryption. Should I discover serious limitations to this encryption method, I can nuke the drive and reinstall before sinking time into tweaking.

Thank you for your help.

---

### Post by hyper_ch on 2008-06-20
> **RichPowers said:**
> 1) Three logical volumes were created in the encrypted space: /, swap, and /home. The unencrypted /boot was created automatically.
Are you sure it did create a seperate /home partition?

> **RichPowers said:**
> Do these volumes act like physical partitions? For example, if I reinstalled Ubuntu, could I format / and leave /home unaffected, as you could with a regularly partitioned system? I'm uncertain how these volumes function relative to standard partitions.
Except for your /home (which I doubt) all are physical partitions. Very likely they are logical partitions in an extended one. Run
```

sudo fdisk -l

```
To view all yur partitions and
```

df -l

```
To see where each one is mounted to.

> **RichPowers said:**
> 2) How does full drive encryption actually *work*? I enter my password at boot and Ubuntu loads. Ok. But when is data actually encrypted/decrypted?
It is de/encrypted on-the-fly... when you copy around large data (movies, dvds, a lot of smaller files) you'll see a noticable slow down compared to normal read/write speed. However for normal usage you shouldn't notice much of a performance loss.

> **RichPowers said:**
> 3) Is there a way to set the system to prompt me for my encryption password after I'm away for X minutes? Will hibernate cause the system to be encrypted?
Setup a screensaver and enable the lock of your session. So you will have to enter your user password to unlock it. If power fails, everything is fully encrypted. So it depends on how strong your user password is...
Never tried hibernation.

> **RichPowers said:**
> 4) How would backups work? If I create an rsync backup job and send it to a file server, will the data be encrypted and therefore unreadable?

If you backup the encrypted drive then the data will be encrypted... but I backup the files within to another computer with encrypted drives... 

> **RichPowers said:**
> Basically, I don't want to lose any valuable data because I'm inexperienced with full drive encryption. Should I discover serious limitations to this encryption method, I can nuke the drive and reinstall before sinking time into tweaking.
Yeah, backups are a must (also on unencrypted drives) because if an encryption crucial part of the harddisk fails, you might not recover the data contained within it.

---

### Post by RichPowers on 2008-06-21
Thank you for your help, hyper.

I should've clarified: if I back up /home (and maybe some config files...I'm still a newbie so I don't know which ones yet) will /home and said config files be encrypted? I thought no, since they're not an image of the entire encrypted drive.

---

### Post by hyper_ch on 2008-06-21
they won't be... but you can backup into another encrypted partition/disk ;)

---

