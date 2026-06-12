---
title: "Unexpected Reboot / sound shrieks (jaunty upgrade)"
date: 2009-05-24
forum: System76 Support
---

### Post by fohat on 2009-05-24
I have a Wild Dog (Early '09 version) which came with 8.10, and not long after I upgraded to the newest System76 driver, I chose to upgrade it to 9.04 using the update manager.  This process seemed to go smoothly, however I've got 2 issues that appear to have cropped up after upgrading to Jaunty. 

 The first issue is that the machine has rebooted unexpectedly 3 times in the last 10 days or so.  This is while putting a bit of load on it; running World of Warcraft over WINE, and simultaneously using Transmission (downloading 1 torrent, uploading 4 others).  The last reboot was this morning so I decided to try checking the logs, however they only seem to start logging after the reboot.  Is there a way to see a log from before my system rebooted?  I have a feeling I've got a driver issue at this point.

 The second issue I've got after the Jaunty upgrade, is that when I press backspace in a text field when the cursor is at the begining of the field I am getting a rather loud high pitched shriek emanating from my speakers.  This shriek also occurs when I choose to restart the computer.  Other than that the sound seems to work fairly well.

The only other major change I made to the system since I got it was apt getting kubuntu desktop to get KDE, but I don't really know if that has contributed at all as the system was stable for about a month afterwards.  I did that well before Jaunty arrived.

Any ideas?

Thanks

---

### Post by thomasaaron on 2009-05-26
The Jaunty upgrade process from Intrepid went very poorly. The number of hosed upgrades I've seen has been monumental.

There are settings for the beeping noise (although, I've never heard it described as a shriek). Try running this command...

sudo modprobe -r pcspkr

Does that fix it? Does your other sound still work? If so, we can research further how to fix it permanently.

As for the random rebooting, please go to System > Administration > System76 Driver > Support > Create and post the logs.tar file it creates in your home directory. I'll have a look.

---

### Post by fohat on 2009-05-26
Thanks for the response, log file attached.

I was about to tell you that the modprobe didn't fix the sound issue, but first I decided to go have another look in system->Preferences->sound.  Previously I had unchecked "play alerts and sound effects" thinking that would fix it, but I see now there is another check box below that called "play alert sounds".  I've unchecked that as well now, and the shriek is gone.  I think there should be an improvement on that ui design, if you uncheck the first box because you don't want alerts, I would think the other should uncheck itself...

Thanks for helping check into the reboot issue, let me know if you find anything.

Cheers

---

### Post by thomasaaron on 2009-05-27
Well...

1. Your syslog should be much longer. I can't see what happened before the only restart mentioned in the log. Please recapture the logs after the next reboot and re-post them.

2. Your syslog mentions something about Microsoft's Joliet filesystem. Could you please tell me more about how you have your computer set up? Installed software, VMs, etc...

3. Immediately before *one* restart in your messages log, there is a npviewer segfault (i.e. flash crashed). But I'm not sure if that is the reboot in question.

So, if you'd re-capture the logs after the next random reboot, I'd appreciate it.

---

### Post by fohat on 2009-05-27
Currently I have a dual boot setup with Windows 7 (build 7000) using Grub.  I haven't booted into Windows for over a week now.  I've got Virtualbox and VboxGTK installed but have not used those programs yet.  The only other software I have installed is several web browsers, and the aforementioned Kubuntu-desktop via apt.

I'm pretty sure that the last time it rebooted I was trying to read a very old audio CD-R, which did not seem to work.  I don't recall which media player I used, but it may have been Rhythmbox.  After the reboot I took the same CD and it played OK on my mac mini but there was some deterioration as some of the songs had issues during playback.

I will be sure to post an updated log file if I get another reboot.

Thanks

---

### Post by plato4me on 2009-08-17
I started out with jaunty on the Wild Dog, but I have the same issue. I got another random reboot a few minutes ago.  Attached are my log files.  Any help would be most appreciated.

BTW, I've done the memory check - seven passes, running all night.  No errors reported.

---

### Post by pseudotheist on 2009-09-17
> **thomasaaron said:**
> There are settings for the beeping noise (although, I've never heard it described as a shriek). Try running this command...

sudo modprobe -r pcspkr

Does that fix it? Does your other sound still work? If so, we can research further how to fix it permanently.
I seem to have this problem.  Did you ever research a permanent fix?

---

### Post by thomasaaron on 2009-09-18
fohat and plato4me, please email me at support...at...system76...dot...com. We're having this issue with some others that that have this problem. I'd like to include you guys in the research.

pseudotheist, did 'sudo modprobe -r pcspkr' work for you?

---

### Post by pseudotheist on 2009-09-18
> **thomasaaron said:**
> pseudotheist, did 'sudo modprobe -r pcspkr' work for you?
Yep.  Just not persistent through reboot.

---

### Post by flukeairwalker on 2009-09-18
I used to have this problem, but I can't remember what finally fixed it. I know Thomas Aaron helped me out with it. This was several months back.

---

### Post by satsujinka on 2009-09-19
You have to disable PC Beep in alsa. Open a terminal, type "alsamixer", and mute the PC Beep channel.

---

### Post by pseudotheist on 2009-09-21
> **satsujinka said:**
> You have to disable PC Beep in alsa. Open a terminal, type "alsamixer", and mute the PC Beep channel.
I see no PC Beep channel...

---

### Post by satsujinka on 2009-09-21
Alsamixer may not fit on your terminal so you may have to scroll right. If you still can't find it could you post a screenshot.

Since "sudo modprobe -r pcspkr" worked for you, you may be able to disable it by adding the following to /etc/modprobe.d/blacklist.conf:

```
blacklist pcspkr
```

---

### Post by pseudotheist on 2009-09-21
It warns me I'm about to edit a readonly file.  Is there a correct way to update the blacklist?

---

### Post by satsujinka on 2009-09-21
You need root access to modify things in /etc. As far as I am aware there's no update command, it's meant to be edited manually. I do know that Kamic has that line in it's blacklist.conf file, if that makes you feel more comfortable about it. Honestly though, I've always used alsamixer (or xfce mixer) to turn off the beeps.

---

### Post by pseudotheist on 2009-09-21
Well, here's the list of options I have in AlsaMixer:
Master
Headphone
PCM
Front
Front Mic
Surround
Center
LFE
Line
CD
Mic
IEC958
IEC958 Default PCM
PC Speaker
Caller ID
Channel Mode
Off-hook

---

### Post by satsujinka on 2009-09-22
PC Speaker should be the same thing as PC Beep. Try muting that.

---

### Post by pseudotheist on 2009-10-01
> **satsujinka said:**
> PC Speaker should be the same thing as PC Beep. Try muting that.

Just wanted to say this seemed to work.  Thanks everybody!

---

### Post by moster on 2009-10-01
I am considering to disable updates all together. Let alone upgrades. There is probably source of your problems.

---

### Post by HotShotDJ on 2009-10-02
> **moster said:**
> I am considering to disable updates all togetherThis is not a good idea.  You want to keep security updates enabled at the very least.

---

### Post by moster on 2009-10-02
> **HotShotDJ said:**
> This is not a good idea.  You want to keep security updates enabled at the very least.

Every 5-10 "update pack" brake something. My current condition is like a plane with leaking oil, one engine down and smoke goes from other one. I am holding fingers crossed that it fly until Ubuntu 9.10 is out. Then I will do clean install.

---

### Post by HotShotDJ on 2009-10-02
> **moster said:**
> Every 5-10 "update pack" brake something.Security updates shouldn't break things... but then again, Jaunty has been one of the more... ahem... "difficult" Ubuntu releases.

---

