---
title: "After installing Ubuntu Server 13.04 on softraid/mdadm, I am dropped to a shell"
date: 2013-05-23
forum: Server Platforms
---

### Post by Scrumps on 2013-05-23
Hello,

I was installing Ubuntu Server 13.04 on my machine and was attempting to do this on a softraid/mdadm

Following this guide:
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

After installation finishes, and the disc ejects. It boots to grub and offers me the option to boot to "ubuntu"

After that process happens I get the following:
[IMG]http://i.imgur.com/jPMWZjil.jpg[/IMG]

I thought maybe it was because it didn't recognize the /boot path, so I installed /boot to a separate hard drive and the issue still happens.

I was looking into this: [http://ubuntuforums.org/showthread.php?t=1653682](http://ubuntuforums.org/showthread.php?t=1653682)

But unfortunately, /dev/mapper/<uuid> doesn't exist for me, I have /dev/disk/by-*

So I am not sure where else to continue. I am sure if I disabled the RAID and just installed it to a single drive, it would no problem, unfortunately, I would like to be able to have the / path on RAID just incase. 

I appreciate the help.

---

### Post by Scrumps on 2013-05-24
This is resolved, I removed all drives except for what I was going to list as /home and the drives for the / raid

Fixed it self after a re-install

---

