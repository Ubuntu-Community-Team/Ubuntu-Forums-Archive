---
title: "Disk FILLS with infinite logs - at least 2 years old bug"
date: 2022-08-03
forum: Ubuntu, Linux and OS Chat
---

### Post by incomt65 on 2022-08-03
**EDIT:** this is a rant. Sadly the replies have been blind to the central problem: the way the system handles an uncontrolled flux of logs, and the lack of warning to the user. I already know how to fix the log problem because unfortunately there is a lot of similar cases and plenty of posts with solutions. 

---

I can't believe this. I really can't. 2 years ago I installed Ubuntu and out of the blue the system frozed after some minutes of use. I discovered it was the disk filling with gigantic syslog, journal and kernel logs. I mean -  growing at 1GB every 10 or 20 seconds.

The bug was known and could be prevented adding a line in grub. However, the problem itself is:

- The logs grow INCONTROLLABLY, filling the disk without limits. This IS BAD SOFTWARE DESIGN (or lack of), be it open source, proprietary, anarchocapitalist, xenomorph or whatever.

- There is no warning of disk filling. The system just freezes. Again - horrible design. Both MacOS and Windows warn when there is insufficient space.

But the worst part is that I installed Ubuntu 22.04 this week and two years later the problem is still there! No action was taken! How can this be? And I don't mean the originator bug, which is a hardware problem -- I mean the software design part. I can't believe two years and several reports this thing still happens.

Anyway. If I had the money I' buy a Mac but I'm stuck with this. Overriding the bug, the system works and is a very nice progress from the previous version. The desktop is very pretty.

Regards

Alvaro Medina

---

### Post by Tadaen_Sylvermane on 2022-08-03
I'd suggest whatever software you are using is the problem and not the distro itself. I've never seen this happen personally. Recently though I decided to try a bit more specific about my partitioning, now /var is it's own 5g partition and the above simply cannot happen. Which bug are you referring to?

---

### Post by incomt65 on 2022-08-04
> **Tadaen_Sylvermane said:**
> I'd suggest whatever software you are using is the problem and not the distro itself. I've never seen this happen personally. Recently though I decided to try a bit more specific about my partitioning, now /var is it's own 5g partition and the above simply cannot happen. Which bug are you referring to?

Ah, ye olde "its your software not the distro". That could be if I had installed anything other than the distro, which is not the case. As for your solution, Ubuntu is, AFAIK, targeted to end users, not experts that know about partitioning. The simplest install does not offer multiple partitions (not even the swap partition from old days).

---

### Post by TheFu on 2022-08-04
Since this is chat, not help, I'll just say that log file limits are easy to set. They can even be made to never touch storage, ever.  When we run in the Try Ubuntu mode, logs never touch storage.

Oh, I cannot resist.  Run these commands to address the issue ASAP:
```
$ sudo journalctl --vacuum-size=500M

# edit the config file to limit loggin.l
$ sudoedit /etc/systemd/journald.conf
```

Change the lines inside to look like:
```
[Journal]
Storage=persistent
SystemMaxUse=500M
SystemMaxFileSize=50M
SystemMaxFiles=10
Compress=yes
```
replacing any non-comment lines as needed.
At the next reboot, these settings will take affect.  I think "auto" is the default, but on your system, for some reason, this isn't working well.  That usually means there are system/program issues that need to be resolved, so look at all the log files and take corrective action.

It is true that the default installer is really stupid for disk layouts.  It is up to the smarter user to do something ... er ... smarter.  There are so many reasons the defaults are unacceptable, but that's multiple, different, threads.

---

### Post by deadflowr on 2022-08-04
What bug?

---

### Post by oldfred on 2022-08-04
If an Asus all you need is a boot parameter. Previous post was one model Asus, but issue is with multiple models of Asus.
Best to talk to Asus about buggy system as just about everyone else does not have the issue.

Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3) & 
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by TheFu on 2022-08-04
I have an Asus laptop and don't remember this issue.  It is an 8th gen Core i5.

---

### Post by zebra2 on 2022-08-09
> **deadflowr said:**
> What bug?

Ok, I decide that I don't want a "sleep mode" activating on my system. The solution that I use in to open a terminal and insert something like this 

```
 sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target 
```.

As a result of my using a mask to inhibit the sleep mode my auth.log starts to accumulate endless alerts (13Gig) that the mask was used. This in spite of the fact that systemd provides the mask if desired by the system admin. 

So my solution is to delete the auth.log file and reboot to create it anew and the add some journald.conf adjustments similar to the ones displayed in the post #4 above.  This fixes the problem just fine and in fact I go back and add in some changes suggested by TheFu which gives me a even cleaner result and all is good. 

I don't know if this is a bug or not but if not then the release is missing a switch in the Shut Down part of the System Settings to turn off the sleep mode. It could be on the table but left incomplete but if it was completely overlooked then I would call it a bug.

---

