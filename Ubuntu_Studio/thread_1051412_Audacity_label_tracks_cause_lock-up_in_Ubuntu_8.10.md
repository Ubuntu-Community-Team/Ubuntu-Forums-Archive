---
title: "Audacity label tracks cause lock-up in Ubuntu 8.10"
date: 2009-01-26
forum: Ubuntu Studio
---

### Post by Effcook on 2009-01-26
I've started using Audacity on a machine that was recently upgraded
to Ubuntu 8.10.  After successfully doing a number of operations
on a 20 minute long track, I added a label track and things started to
get weird.  Adding the first label at the beginning works, but when I
add a second label, the audio i/o seems to freeze up.  The meter shows
stuck levels.  I can still move the cursor around the waveform, but the
rewind button and the play button don't function.
I have tried doing this on several different tracks and have had the
same problem. There are no errors on the terminal window where I ran
Audacity. In Ubuntu 8.04 I used to see similar lockups, but they usually
self-unlocked after about 30 seconds.  This is a fairly generic
i386 32 bit Ubuntu install on an Athlon 64 processor.

---

### Post by Ouoertheo on 2009-01-27
Have you tried running Audacity from the command line so you can see the program output?

---

### Post by Effcook on 2009-01-27
>Have you tried running Audacity from the command line so you can see the program output?
Yes, that's how I ran it, there were no messages.
I tried building the latest version of Audacity (1.3.6), that involved first
installing these package depencencies:
2x2.8-headers
wx2.8-i18n
wx-common
libwxbase2.8-0
libwxgtk2.8-0
libwxbase2.8-dev

The problem is still present with the new version, but is now
somewhat different. After adding a label
and trying to play, the console fills up with
HCK OnTimer
messages and freezes for some tens of seconds, eventually the
level meter unfreezes and play starts to work again.
Playing with it a bit, before adding the label track, I get a few
HCK OnTimer messages, but not as many and things don't tend to freeze up.
For some reason, the label track seems to make things worse.
I'm beginning to suspect some kind of hardware problem, I will try
to duplicate this error on another box.

---

### Post by Effcook on 2009-01-27
I tried to recreate this problem on another machine (Athlon 1700 CPU running
Ubuntu 8.10).  Everything works just fine there using the same audio file and
the default installation of Audacity.  The problem machine uses an
Asus K8V-MX motherboard (Athlon 64 2800+ cpu) with built-in ADI AD1888 SoundMax
audio i/o.

---

### Post by Stochastic on 2009-01-27
This sounds like a reproducible bug based around a particular hardware configuration.  I'd take this to launchpad.net and report it there for the devs to mull over.

---

