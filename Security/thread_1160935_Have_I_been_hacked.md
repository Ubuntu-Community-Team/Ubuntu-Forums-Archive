---
title: "Have I been hacked?"
date: 2009-05-16
forum: Security
---

### Post by cguy on 2009-05-16
A few moments ago I encountered some herratic behaviour:
- tabs in Opera switching by themselved
- multiple instances of Trash spawning
- herratic mosue behaviour
- no mouse control

How can I tell if I have been hacked?
Could it be just a bug?


---

I already changed my password to a stronger one.


Ok, I kinda rushed posting. I know I should have read before (which is waht I am doing now), but it's the first time I am dealing with this, so I am excited. :D
*backing up data*

---

### Post by jordilin on 2009-05-16
It seems very weird. I would restart and take a look at /var/log/messages

---

### Post by tubbygweilo on 2009-05-16
cguy, is it possible to access your machine via another or new mouse? As what you describe could be attributed to a failing or misbehaving mouse cause by dirt, old age or broken hardware.

---

### Post by cguy on 2009-05-16
> **tubbygweilo said:**
> cguy, is it possible to access your machine via another or new mouse? As what you describe could be attributed to a failing or misbehaving mouse cause by dirt, old age or broken hardware.
I thought the same the first few seconds, but then Trash windows started spawning. Where did those come from?
There was no link whatsoever directly accesible with the mouse at the time.

Here's the messages file. I skimmed through it and didn't see anything suspicious, but I don't have a solid know-how anyway.
The last duplicate lines have been generated when I ran Firestarter.

I checked for rootkits and got the following warnings, which I believe are false positives.
[13:58:56] /usr/sbin/unhide                                  [ Warning ]
[13:58:56] /usr/sbin/unhide-linux26                          [ Warning ]
[14:00:18]   Checking /dev for suspicious file types         [ Warning ]
[14:00:18] Warning: Suspicious file types found in /dev:
[14:00:19]          /dev/shm/pulse-shm-3967358011: data

---

### Post by Dr Small on 2009-05-16
Do you have Remote Desktop enabled?

---

### Post by cguy on 2009-05-16
I disabled it a few days ago.

---

### Post by WatchingThePain on 2009-05-16
Have you noticed your system using more memory, cpu or bandwidth than usual with this?.
Take a quick look at 'dmesg | less' in case that has something useful in case of hardware problems.

---

### Post by cguy on 2009-05-16
No, I did not notice such things.

The output of dmesg | less are variations of
[ 8736.055650] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:f4:b1:23:16
:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=1 P
ROTO=UDP SPT=68 DPT=67 LEN=308 

Lots of them.

---

### Post by jonnygd on 2009-05-17
Hi cguy, It doesn't sound like you've been hacked, sounds more like failing hardware or a glitch in the system, I wouldn't be too worried about it. For piece of mind you could always install wireshark and monitor your network traffic but if you have firestarter and have checked for rootkits you should be fine.

---

