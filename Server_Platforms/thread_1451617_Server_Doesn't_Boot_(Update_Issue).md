---
title: "Server Doesn't Boot (Update Issue)"
date: 2010-04-10
forum: Server Platforms
---

### Post by dakez2010 on 2010-04-10
Hello, after installing some updates on my server, one of which is a kernel upgrade my system stopped responding and required a manual reboot. The server is headless,  powered it on again and it didn't seem to be booting because I was unable to access SSH on it or any other services. I hooked it up to a monitor and powered it on to be greeted with the GRUB screen with several kernel selections. Strangely, booting with an older kernel still doesn't work. The problem is that there is this extremely fast scrolling text after booting the machine with any of the kernels, it scrolls too fast to be able to see what the contents are. If there is a way I can rollback the update, maybe using a restore disk or something, please let me know about it. I need to get this server back up and running ASAP.

---

### Post by wojox on 2010-04-10
Server edition? Hardy, Intrepid, Jaunty, Karmic,  Lucid.

---

### Post by dakez2010 on 2010-04-10
I run Ubuntu Server 9.10, sorry for not including that information in the first post.

---

### Post by wojox on 2010-04-10
You can usually run:

```
dmesg | tail
```

To find boot messages. Do you have a GUI of any sort installed?

---

### Post by dakez2010 on 2010-04-10
I cannot access a shell at all on this system. There is constant text on my machine, that will never complete, it's a blur. Is there anything I can do to prevent reimaging my machine, because this machine contains many GB's of critical data that I would have to first backup. I'm thinking that it's simply a boot issue and that my whole machine isn't screwed. I have no GUI, even if I did, the boot process wouldn't go as far as to actually get to it.

---

### Post by wojox on 2010-04-10
Okay, sorry about that. You cant get in even with the monitor and keyboard hooked back up. I see. Can you access recovery mode? 

The only other option I could think of would be to boot a live desktop cd, mount the drive and back up to another drive.

---

### Post by dakez2010 on 2010-04-10
I've decided to backup all my data and reinstall the OS (Maybe a different one, I haven't decided yet). Too bad Ubuntu Server 10.04 isn't out yet, because this would be the perfect opportunity to upgrade from 9.10 -> 10.04. I usually do full reinstalls rather than upgrades because upgrades tend to always break something in the process. I'll probably reinstall Ubuntu Server 9.10, this time being extremely careful about updates and things. I'd rather go without kernel upgrades, but I know that they are essential to the security of the system. Then again, while being essential, they sometimes **** up my system. Thanks for your help however, and hopefully I won't run into any of this again. If someone else that encountered this issue is now reading this thread, I feel sorry for you, because there doesn't seem to be a remedy other than to reinstall the operating system. Maybe I missed something, I don't know. We all learn from our mistakes *sigh*.

---

### Post by wojox on 2010-04-10
Give Debian Lenny a try. Its a great server.

---

### Post by dakez2010 on 2010-04-11
To sum up, I booted into the recovery mode of the Ubuntu Server 9.10 install disk and gained access to a shell, although I was unable to login. I mounted my flash drive and began backing up the drive using the command line. I then reformatted the machine and reinstalled Ubuntu Server. When Ubuntu Server 10.04 comes out, I'll be sure to test in VMWare before trying in my production machine.

For any users wondering how to mount the flash drive in a command line in the restore mode. Use the following command. ```
mount -t vfat /dev/sdb1 /home/flash
```
Make sure the mount directory/point exists. Use ```
umount /dev/sdb1
``` to unmount the filesystem.

Thank you for your help.

---

