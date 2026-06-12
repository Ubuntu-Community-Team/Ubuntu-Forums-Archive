---
title: "Kernel cleanup and GRUB menu update"
date: 2013-05-16
forum: Server Platforms
---

### Post by putz3000 on 2013-05-16
I have a storage server I have been slowly trying to get production ready (long story, not relevant). The box is currently running 10.04 LTS Sever, software raid1. over time I have installed multiple kernels and decided to attempt some cleanup. 

After installing the latest kernel I rebooted, paused at the menu long enough to write down the listed kernel entries, and continued to boot to the latest for verification that it would boot just fine. At this point I had 5 kernels listed and installed. I first ran the following code to generate a list of installed kernels which I verified against my hand written list:

```
dpkg --get-selections | grep linux-image
```

I then removed the three oldest kernels (leaving the two newest ones) using the following code:

```
Sudo apt-get purge linux-image-2.6.32-28-server linux-image-2.6.32-39-server linux-image-2.6.32-41-server
```

After everything was done processing, I rebooted the server to see what the menu looked like. The top part of the GRUB menu correctly showed just the two kernels I had left installed. The bottom portion of the GRUB menu showed all of the kernels associated with (on /dev/sdc1) which I believe is the mirrored drive. I thought I had seen transactions processed during the uninstall that referenced sdc1 so I thought maybe I just needed to update the GRUB menu which I did using the following command:

```
sudo update-grub
``` 

But, on reboot the menu is unchanged. So my question is, how do I remove or make sure old kernels are removed from the secondary mirrored drive and how do I get the GRUB menu updated to reflect that change?

---

### Post by darkod on 2013-05-16
If it's a true mirror you still have only one root partition and remving the kernels with the above command should have removed them from the system. There should be no separate kernels reported on sdc1.

The OS counts as one in raid1. From what you are saying it seems that there are kernels reported on sdc1 like a different OS.

What does this show:
```
cat /proc/mdstat
```

---

### Post by putz3000 on 2013-05-16
I think I just figured out what is going on. Looks to me like Corporate changed the backup script on this machine which I was not aware of. Instead of backing up data folder it appears to be copying the system over to it. Which also makes sense when I start thinking about sda, sdb, and sdc. So I believe sdc1 is actually the backup drive. I disconnected the drive, updated GRUB menu and on reboot would go straight to login. I then hooked up the drive and re-updated GRUB menu again and upon reboot have everything listed again. So I am going to assume that if the backup script is working correctly that tomorrow I should see only two kernels listed on sdc1 as well.

Sorry for the hassle but thanks for replying darkod.

---

### Post by putz3000 on 2013-05-16
If someone can tell me how to mark this thread as solved I will gladly do so. I have been poking around for the last few minutes but seem unable to figure it out. I am sure its obvious and I am just not seeing it.

---

### Post by oldfred on 2013-05-16
We have a temp work around on solved. For info on why see my signature.

 
Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

