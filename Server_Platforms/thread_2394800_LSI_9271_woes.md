---
title: "LSI 9271 woes"
date: 2018-06-21
forum: Server Platforms
---

### Post by dgingvitac on 2018-06-21
I have a server that is having major issues with the LSI 9271 controller, but not directly with the controller.  We have tried swapping the controller, but it doesn't do any good.  The whole platform also operates properly under Windows, but not under Ubuntu server.  Under Ubuntu server, if it is left idle for a long period, about an hour, it will kill the IO and all the file systems go into read only mode.  Only a reboot will bring it back.  However, if it is kept active, as I have done with a batch file that copies 4GB of data to it from my desktop every minute, then it is fine.  I believe it is something in the power savings settings.  I think must be shutting something off that the RAID controller needs and is causing an IO issue.  Of course, we can't get any logs on it because the files systems all go into read only mode.  

Anyone else have this issue?  Anyone know how to shut off all the power savings settings on the command line, to test my theory?

---

### Post by LHammonds on 2018-06-21
If you look in /etc/fstab, is the following option declared for the partition that is being remounted as read-only?

```
errors=remount-ro
```

Seems like a re-mount as read-only means it is running into errors it cannot correct.  Might be issues with the hard drives, the cable or the controller (but you said you used a different controller).

I'd swap out the cable real quick since that is an easy fix if that's the problem.

Next, I'd run a test on the hard drives.

LHammonds

---

### Post by dgingvitac on 2018-06-21
The drives tested good in a test on the controller itself, and a replacement cable would be harder to do than you might think.  I can't take the server down for more than 2 hours, and then only after midnight, as it is a production system.  I'm keeping it alive with my copying trick, but just allowing it to go down would create much howling among management, despite it only slightly affecting one user.  So, I'm left with trying out the power savings settings.

---

### Post by dgingvitac on 2018-06-21
I have been able to find it is device 0000:04:00.0

---

### Post by dgingvitac on 2018-06-21
now I have a cron job that copies files from one folder to another rather that copying files in from the outside.

Now to figure out why the raid controller keeps crashing during inactivity.

---

