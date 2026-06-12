---
title: "NVidia (specifically nvidia-settings) breaking system, changes system to read only"
date: 2012-07-28
forum: System76 Support
---

### Post by chez17 on 2012-07-28
I have a Gazelle (gazp6) running Ubuntu 12.04.

I can't find any information on google about this so I'm guessing it's not that common. This is the second time this has happened to me and it was the same circumstances oddly enough. Here is the first time:

[http://ubuntuforums.org/showthread.php?t=1982339](http://ubuntuforums.org/showthread.php?t=1982339)

Basically, I have a dual monitor set up and once in a blue moon I have take my computer with me and switch it back to a single monitor set up using the nvidia-settings tool. This is the second time that I have switched it from a dual monitor setup to a single monitor setup and upon the next restart, the file system is in read only mode. I can't find much information about this but it literally has only happened directly after changing monitor configurations. People have suggested that it is a corrupt hard drive. This computer is only 6 months old. I also have a Windows partition on it that works just fine so it's definitely a linux thing. This is my work computer, I need it to do things like have a roof and eat food. I need to know a few things.

Am I the only one who has experienced this?

Is this computer no longer safe to work on, as this keeps happening?

Can anyone at System76 let me know if there is any warranty I can rely on over six months after purchase?

Am I up a certain creek without a paddle?

This is my second System76 and I have promoted the company every chance I get on reddit and various forums. Trust me, I'm a fan.  At this point, however, I'm considering buying a new computer and to not have to worry about this and it's not going to be a System76. Two crashes in the first 6 months is not acceptable. Sorry if I'm a little harsh here but I just had to cancel a trip with friends because my computer crashed and I can't do the work I need to do. Instead I'm home trying to deal with this. I could use some help here.

---

### Post by Newbunto on 2012-07-30
> **chez17 said:**
> 
Basically, I have a dual monitor set up and once in a blue moon I have take my computer with me and switch it back to a single monitor set up using the nvidia-settings tool.

I don't switch from external monitor to laptop display only (may have done it once ever) so can't comment directly on your question but do you actually need to do what you are doing?

If you just shut your laptop down with the external monitor connected, disconnect the external monitor and boot up later on when you are on the road, doesn't it do the right thing? It may depend on whether you use the option in nvidia-settings to save the settings. (I do not!)

(The result of all of this for me is that every time after booting up, with the external monitor connected, I have to use nvidia-settings to change from the two displays showing the same thing to using only the external monitor. So I use nvidia-settings at least once a week, without a problem. I don't use any of the dual monitor configurations, except temporarily. It's always either external monitor or laptop built-in display, but not both, except temporarily.)

If you can avoid changing from dual monitor to single monitor, it may help to fault isolate. I appreciate that such an infrequent issue can be a pain to pin down.

---

### Post by TheFu on 2012-07-30
What do you mean by this?
> **chez17 said:**
>  the file system is in read only mode. I can't find much information about this but it literally has only happened directly after changing monitor configurations.

Is it mounted as read-only or are all the file permissions changed to read only?

I've found that when a file system is mounted as read-only, that means some sort of corruption is happening and **fsck** [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck) needs to be run. Have you run it?

What do the **syslog **and **dmesg **logs show?

Probably the easiest fix is to force an fsck at the next reboot.  To do that, drop an empty file into the root for any partition you'd like checked.
```
sudo touch /forcefsck
```will force it on the root file system.  You can probably do it for all other file systems by making certain they are unused, umount, fsck, mount. On multiuser systems or servers, that is nearly impossible, so rebooting into single-user mode will be needed.  I'd still use the /forcefsck trick for /, however.

fsck is part of normal Linux maintenance.  It happens automatically from time to time, but if there are issues, running it manually is helpful.  There are other standard system maintenance things for Linux desktops. This article that I wrote for Lifehacker might help: [http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

