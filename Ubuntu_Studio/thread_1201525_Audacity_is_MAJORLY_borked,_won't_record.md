---
title: "Audacity is MAJORLY borked, won't record"
date: 2009-07-01
forum: Ubuntu Studio
---

### Post by fredbird67 on 2009-07-01
I have had a very frustrating time getting Audacity to record without clipping, and now, to make matters worse, it won't even record at all. When I try to record, it won't even get off the starting point, and as such, nothing at all gets recorded. I've tried choosing different default sampling rates, default sample formats, and setting different playback and recording devices, and not it's all borked.  I even tried uninstalling it and even deleting the .deb files that were downloaded in the /var/cache/apt/archives directory to force the system to download everything all over again -- nothing. I also tried deleting any folders in my home directory that start with ".audacity", and that didn't work, either.  It's completely borked, and this is on Linux Mint 7 (aka "Gloria"), which I installed over the weekend.  Any ideas?

Fred in St. Louis

---

### Post by igorzwx on 2009-07-01
Hi Fred!

Something is really very strange with Audacity 1.3.7 and Ubuntu 9.04

I am now making "quasi-scientific" experiments with Audacity, ALSA, OSS4, and Ubuntu 9.04.
The results are very strange.

I use test audio files.
You can try them too.

You can create test audio files with Audacity Nyquist with these commands:

(mult (sum (hzosc 10) (hzosc 19500)) 0.45)

(mult (hzosc 19500) 0.9)

(mult (hzosc 10) 0.9)

These produce three files:

10Hz + 19500Hz
19500Hz
10Hz

How to create test files

1. Audacity -> Generate -> Silence (5 seconds are enough)

2. Effects -> Nyquist prompt 

3. type a command, or copy-and-paste (paste with Ctrl+V)

Save them and play with Audacity and Media players.
If you hear tones, or strong noise, something is wrong.

---

### Post by fredbird67 on 2009-07-01
Igor, I tried that and didn't hear a thing.

I've also got accounts on here for my wife and for guests.  I just tried logging in as her and trying it from there -- same thing, so whatever the problem is doesn't have anything to do with anything audacity-related that's in my home folder.

What's happening is, when I try to record, the cursor looks like it's trying to move off zero but is being held hostage and stuck on zero.  Does this description of what's wrong make any sense?

---

### Post by fredbird67 on 2009-07-01
Consider this one SOLVED!  I found the answer in the following thread:
[http://ubuntuforums.org/showthread.php?p=7548540](http://ubuntuforums.org/showthread.php?p=7548540)

---

