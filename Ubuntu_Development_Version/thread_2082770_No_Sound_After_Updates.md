---
title: "No Sound After Updates"
date: 2012-11-10
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2012-11-10
I just rebooted my raring desktop, after a week or so...  to find that there's no sound whatsoever.  The sound app doesn't show my card, though it's there when I lspci.

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

I even plugged in a USB sound adapter, which works fine with my laptop running precise, and get nothing.

So, I'm just wondering:  Is anyone else currently seeing this problem, or have I discovered new breakage?  After everything's been great for the last couple of years, I thought our sound problems were a distant memory.

---

### Post by philinux on 2012-11-10
Yep same here. No device listed in sound gui.  Always seems to happen early on on the cycle.

---

### Post by 3vi1 on 2012-11-10
> **philinux said:**
> Yep same here. No device listed in sound gui.  Always seems to happen early on on the cycle.

Ahhh... great!  Err... I mean:  Sorry you're having the same problem, but at the same time I'm glad it's not unique to me so that I don't have to go into the low-level troubleshooting.  :)

If it's really that prevalent, I'm sure they'll revert the breakage - or push through it - soon.

Thanks for the sanity check!

---

### Post by dino99 on 2012-11-10
no issue here on i386; is it a fresh daily install ? Maybe sound settings have been mute on your side. Did you get something logged ?

---

### Post by pqwoerituytrueiwoq on 2012-11-10
have you tried this?
```
killall pulseaudio;rm -rf ~/.pulse;rm ~/.pulse-cookie;pulsepaudio --start
```

---

### Post by zika on 2012-11-10
> **pqwoerituytrueiwoq said:**
> have you tried this?
```
killall pulseaudio;rm -rf ~/.pulse;rm ~/.pulse-cookie;pulsepaudio --start
```It might be wise not to advise such drastic erasure. You're not sure if someone has important settings in those folders. I would always advise creating backup before erasure. I (for sure) have files in ~/.pulse that I would not like to get erased so easily, even though i do have their backup, I hope...

---

### Post by philinux on 2012-11-10
> **pqwoerituytrueiwoq said:**
> have you tried this?
```
killall pulseaudio;rm -rf ~/.pulse;rm ~/.pulse-cookie;pulsepaudio --start
```

Seeing as this is a test install yes I have deleted those folders and reboot
 Device is missing sound gui.

---

### Post by pqwoerituytrueiwoq on 2012-11-10
only file i could imaging would be a "client.conf" everything else is auto generated
on my deskop i put a one in my skel folder to set the guest account to use hdmi
```
 ls /etc/skel/.pulse/ -l
total 0
lrwxrwxrwx 1 root root 22 Nov  8 16:26 client.conf -> /etc/pulse/client.conf
```

---

### Post by zika on 2012-11-10
> **philinux said:**
> Seeing as this is a test install yes I have deleted those folders and reboot
 Device is missing sound gui.Why reboot?
Too big hammer...
There are rare occasions when reboot is necessary and they (in my case) involve heavy lock-ups only...
> **pqwoerituytrueiwoq said:**
> only file i could imaging would be a "client.conf" everything else is auto generated
on my deskop i put a one in my skel folder to set the guest account to use hdmi
```
 ls /etc/skel/.pulse/ -l
total 0
lrwxrwxrwx 1 root root 22 Nov  8 16:26 client.conf -> /etc/pulse/client.conf
```My imagination is a bit wider...

---

### Post by philinux on 2012-11-11
Reboot was to change from 13.04 to 12.10. I have 2 hard drives. :p

---

### Post by pqwoerituytrueiwoq on 2012-11-11
> **philinux said:**
> Reboot was to change from 13.04 to 12.10. I have 2 hard drives. :p
i have 3 connected and 2 sitting in my case unplugged, 1 is a ssd another is my primary storage drive, 1 is in a hot swap bay
40gb, 80gb, 500gb, 30gb (ssd), and 160gb
10.04 is on my ssd
12.10 is on my 80gb
xp and something is on the 40gb
backups are on the 160gb

did i win the off topic who has the most drives contest?

---

### Post by 3vi1 on 2012-11-11
```
evil@saturn:~$ killall pulseaudio;rm -rf ~/.pulse;rm ~/.pulse-cookie;pulseaudio --start
pulseaudio: no process found
E: [pulseaudio] main.c: Daemon startup failed.

```

I figured out the issue.  Apt-get upgrade had installed pulseaudio-esound-compat:i386, and removed pulseaudio-esound-compat.  Apparently pulseaudio won't start when that package is missing.  You'd think it would be a dependency or something.

---

### Post by philinux on 2012-11-12
> **3vi1 said:**
> 
I figured out the issue.  Apt-get upgrade had installed pulseaudio-esound-compat:i386, and removed pulseaudio-esound-compat.  Apparently pulseaudio won't start when that package is missing.  You'd think it would be a dependency or something.

Spot on that man have some :popcorn:

I installed pulseaudio-esound-compat and it removed the i386 version. I'm on 64 bit by the way and pulseaudio-esound-compat is the 64 bit package.
Sound restored.

Have you raised a bug?

---

### Post by John_Swing on 2012-11-15
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543)

---

### Post by floyd_pepper on 2013-05-12
Hi, I had the same problem and found out it was because of 'speech-dispatcher'. 

I fixed it by installing Boot-up-manager:
> sudo apt-get install bum

Start Boot-up-manager from Dash. Hit 'Advanced' and pick 'Services' tab. Deselect 'speech-dispatcher'. 
[Screenshot]("https://www.dropbox.com/s/h4f7awusf8060lb/Screenshot%20from%202013-05-12%2022%3A13%3A29.png")

Apply and restart.

---

### Post by pqwoerituytrueiwoq on 2013-05-12
> **3vi1 said:**
> ```
evil@saturn:~$ killall pulseaudio;rm -rf ~/.pulse;rm ~/.pulse-cookie;pulseaudio --start
pulseaudio: no process found
E: [pulseaudio] main.c: Daemon startup failed.

```

I figured out the issue.  Apt-get upgrade had installed pulseaudio-esound-compat:i386, and removed pulseaudio-esound-compat.  Apparently pulseaudio won't start when that package is missing.  You'd think it would be a dependency or something.

that was moved to [FONT=courier new]~/.config/pulse/

[/FONT]edit, seems this thread was old, *points at the necromancer above me*

---

### Post by cariboo on 2013-05-12
Seeing as we are in Saucy development now, I'll close this thread.

---

