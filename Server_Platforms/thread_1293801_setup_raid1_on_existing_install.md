---
title: "setup raid1 on existing install"
date: 2009-10-17
forum: Server Platforms
---

### Post by jonny.milano on 2009-10-17
Hi there,

I've been using Ubuntu as my home server software for about a year now. I was brand new when I started and I love all that I have learned about computers and linux. Thing is now I would like to create a RAID1 setup on my existing disk. I have a 80GB partion that holds all of my system files and some media files. I used LVM and two 40GB drives I had siting around to make a 80GB partion that I would now like to mirror with my boot partion for backup. 

Is this possible? Or, does RAID have to be installed when the OS is installed? I have googled around but all of the tutorials I find are for doing just that, installing RAID at the OS install.

Thanks in advance for all of the help.

---

### Post by cesarbrod on 2009-11-24
I am just facing the same problem and I wonder if you came up with a solution...

Thanks!

Cesar

---

### Post by whoop on 2009-11-24
Check here...
[http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server)

Also check out my own thread where I made a /home raid1 partition on an existing install (this seems close to what you want), I tried to be as descriptive as possible there:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)

---

### Post by Denbert on 2009-11-24
Here is another [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny)

---

### Post by jonny.milano on 2009-11-24
> **cesarbrod said:**
> I am just facing the same problem and I wonder if you came up with a solution...

Thanks!

Cesar

I didn't. I am just doing manual backups. The links below look promising but I don't have the time right now to delve into it. Besides, the data in this case is not sooo important. Let me know if you use the info below and if it works out! Otherwise, next time, I'll just install RAID at the OS install.

---

### Post by cesarbrod on 2009-11-25
This one: [http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server)

Worked as a charm! Thank you all!

---

