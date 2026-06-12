---
title: "Daru1 freezes"
date: 2009-03-25
forum: System76 Support
---

### Post by perce on 2009-03-25
Dear Tom,

today my computer is freezes every few minutes, and there is no other way to bring it back to life than pressing the power button. However not everything is dead, because when I put the CD in the drive before switching off, the drive spinned off. I tried to attach the logs, but the I got some error from the forum webpage.

---

### Post by thomasaaron on 2009-03-25
Did you ever do the firmware update per these instructions...

> To flash the CD/DVD drive firmware in your (white)DarU1 or GazV4, follow
the instructions on this bug report...
[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

...beginning with the post that has this header...
Thomas Aaron  wrote on 2007-08-13:  (permalink)

If not, that's probably the problem. If so, contact me by email for expedited support.

---

### Post by perce on 2009-03-25
If it's the the update of about 1.5 years ago yes, I did. In fact the problem I'm experiencing is new: it happened the first time a couple of weeks ago, but it's only today that it has become unmanagable. Eventually it froze with the live CD too after my previous post.

---

### Post by thomasaaron on 2009-03-25
Thanks, Perce.

Try re-seating your memory cards and hard drive. If that doesn't fix it, please run memtest86 on it and let me know if it throws any errors.

---

### Post by perce on 2009-03-25
> **thomasaaron said:**
> Thanks, Perce.

Try re-seating your memory cards and hard drive. If that doesn't fix it, please run memtest86 on it and let me know if it throws any errors.

Can you send me instructions about the memory card please? (you've already sent me instructions for the hard drive last summer)

---

### Post by thomasaaron on 2009-03-26
Just remove the smallest of the panels on the bottom of the DarU1. You only have one memory card. Press the little retainer arms to the side, and the memory card will pop up. Then you can pull it out and re-seat it.

Make sure all power is disconnected: AC and Battery.

I was thinking...

If that doesn't solve it, run the computer and let it freeze a couple of times. Make note of the *time* that the freezes begin and end. Then go to System > Administration > System76 Driver > Support > Create and attach the logs.tar file created in your home directory.

It may not be hardware related at all. Could be some process that is sucking up memory and cpu time.

You also might want to go to a terminal and run...

```
top
```

It will show you if there are any hog processes.

---

### Post by perce on 2009-03-29
Dear Tom, 

I had a crash this afternoon, so I send you the logs. It's hard to tell you 
the time when the crash happened: it was around 19:30 in France, but my computer was still in Mountain time, so it should be around 11:30 in the logs. Anyway, it's just before the last reboot. 

I've run the memtest from the live CD a couple of times and I got no error, but I haven't had time yet to reseat the disk.

Thank you

---

### Post by thomasaaron on 2009-03-29
> Mar 28 12:09:32 Bach bonobo-activation-server (paolo-12820): could not associate with desktop session: Failed to connect to socket /tmp/dbus-tBLI4VoXC3: Connection refused
Mar 28 12:09:33 Bach exiting on signal 15
Mar 28 12:19:27 Bach syslogd 1.5.0#2ubuntu6: restart.

Are you running AWN? If you are, disable it and see if the problem happens again.

---

### Post by perce on 2009-03-30
> **thomasaaron said:**
> Are you running AWN? If you are, disable it and see if the problem happens again.

I have no idea what it is.

---

### Post by thomasaaron on 2009-03-30
AWN is the Mac-like docking bar. I saw a post attributing some of your error messages to AWN. But if you don't know what it is, that probably isn't it.:P

After more research, I found this bug. It attributes the above error messages to the following bug. This bug is related to using a KVM switch...
[https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970](https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970)

Are you using a KVM switch?

---

### Post by perce on 2009-03-30
> **thomasaaron said:**
> AWN is the Mac-like docking bar. I saw a post attributing some of your error messages to AWN. But if you don't know what it is, that probably isn't it.:P


I have never installed it, so I guess I'm not using it.

> 
After more research, I found this bug. It attributes the above error messages to the following bug. This bug is related to using a KVM switch...
[https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970](https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970)

Are you using a KVM switch?

Again, what is it?

One remark I can add, is that I almost never have freezes when I'm on power, which makes me suspect of an ACPI related problem (as usual).

---

### Post by thomasaaron on 2009-03-30
A KVM switch is a device you put plug a keyboard, mouse, and external monitor into. Then you plug your computer into the KVM switch.

I'm not aware of any ACPI problems with the DarU1. We still use them heavily here in the administrative offices with no problems.

I'll keep looking into your error logs.

---

### Post by thomasaaron on 2009-03-30
Let's try this again. The next time it happens, *immediately* shut off the computer and reboot. As soon as the reboot process is complete, go to your System76 driver and re-create the logs. 

Also, this time, please tell me what the time is on the system clock (on your upper toolbar). Don't worry about whether it is French or Mountain time. I just need to know the time on the clock applet. Otherwise, I'm just spinning my wheels trying to find out which errors relate to the freezing.

Also, a new set of logs will give me something to compare the old set too. That may be helpful.

Also, see if the problem occurs with Skype off. You have a number of Skype errors in your logs as well.

---

### Post by perce on 2009-03-31
If you tell me what log files you need, next time I can create the tar by hand from a live CD so that the last logs are immediately after the freeze.

---

### Post by thomasaaron on 2009-03-31
I need /var/log/syslog and /var/log/messages.

I'm sure you know this, but just for the sake of anyone else following this thread, if you try to capture these logs from a terminal in a live CD, you will get logs from the live CD session, not from the installed OS on the hard drive. You need to CD into the installation root partition to capture the correct logs.

---

### Post by perce on 2009-04-01
> **thomasaaron said:**
> I need /var/log/syslog and /var/log/messages.

I'm sure you know this, but just for the sake of anyone else following this thread, if you try to capture these logs from a terminal in a live CD, you will get logs from the live CD session, not from the installed OS on the hard drive. You need to CD into the installation root partition to capture the correct logs.

In principle I know, but I can always forget, so thank you for reminding. But so far no more crashing, probably because I'm mostly on power now that I'm back to work.

---

