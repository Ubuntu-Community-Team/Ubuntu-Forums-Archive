---
title: "LMMS Segmentation fault"
date: 2011-06-29
forum: Ubuntu Studio
---

### Post by Lordgreeny on 2011-06-29
Please help.

I've been trying to run LMMS, but when I run it I get the splashscreen and then nothing. (Sometimes I can briefly see the settings screen before it just goes poof.)
I'm pretty sure I've got LMMS version 4.9

Terminal gives me this when I run it:
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Segmentation fault

I'm using 10.04 on a 1GB, 1.50GHz Intel Celeron M processor. 

What do?

---

### Post by jejeman on 2011-06-29
See what is writed in dmesg. After segfault run
```
dmesg|tail
```
If you uninstall blue tooth audio you will loose those errors.

---

### Post by Lordgreeny on 2011-06-30
I uninstalled bluetooth audio support, and I no longer get the connection failed notices before the segfault but it's still segfaulty nonetheless.

dmesg gave me this about lmms:
[ 1253.397169] lmms[2004]: segfault at b2eee4c0 ip b2eee4c0 sp aeee9eac error 14 in pulseaudio.mo[b2ef3000+3000]

Anyways, thanks for your time.

---

### Post by jejeman on 2011-06-30
I didn't exepect segfault to go away, just bt errors.

So segfualt is in pulseaudio.mo.
Well, you can try to turn off pulse audio and then start lmms. Also I've see that you have 4.9 version which is not from 10.04, how did you install it?

---

### Post by Lordgreeny on 2011-06-30
How do I turn off pulseaudio?

I tried doing it according to this: [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)
But doing so automatically uninstalled lmms and some other stuff for some reason, so I had to undo it. 

I installed 4.9 by adding the repository listed on the LMMS website and installing it via the terminal.

---

### Post by jejeman on 2011-06-30
Hahaha, I really don't know what is elegant about that procedure.
Anyway here is how I do it, less elegant ;)
[http://ubuntuforums.org/showpost.php?p=10938851&postcount=6](http://ubuntuforums.org/showpost.php?p=10938851&postcount=6)
I've just installed lmms from their ppa, and it's working. The version now is 4.10. Try it, maybe it will work for you.

---

### Post by JayPeeJay on 2011-07-02
killall pulseaudio

Also make sure that you are running JACK control before you start LMMS.  If you have LMMS set up to use the JACK audio interface, it will not start until you do so, it will freeze at the splash screen just like you said.  Once you are in LMMS you can change the settings to not use JACK, but the latency is amazing especially if you use a midi controller to record.

---

