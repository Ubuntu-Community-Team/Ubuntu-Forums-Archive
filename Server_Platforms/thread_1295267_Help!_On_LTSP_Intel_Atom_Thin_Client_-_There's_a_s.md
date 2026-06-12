---
title: "Help! On LTSP Intel Atom Thin Client - There's a sound like falling rain."
date: 2009-10-19
forum: Server Platforms
---

### Post by AlexanderDGreat on 2009-10-19
Hi,

I'm using Jaunty 9.04, 4gb ram server, e7400 c2d, updated chroot, i386 arch, but my LTSP Intel Atom Thin Client has a sound like falling rain, so movies, and mp3's are mixed with this sound. What do I do? Help!

---

### Post by AlexanderDGreat on 2009-10-19
Is it just my casing? How many cpu fans does the Intel Atom board have? Is it really the fan? The casing? The motherboard? I'm so confused, can anyone help me?

Thanks.

---

### Post by cariboo on 2009-10-20
I have an atom based media center pc. I use one of [these]("http://www.in-win.us/products_pccase_series.php?cat_id=1&series_id=24") cases. My system has 3 fans including the one on the northbridge chip, no cpu fan. THe power supply has a builtin fan, so I can't do any thing about that, but the case fan plugs into the motherboard, I disconnected the case fan, and now I can just barely hear the chip fan. I don't hear anything like rain falling or any other extra noises.

---

### Post by AlexanderDGreat on 2009-10-20
Hi cariboo, thanks for replying. I attached the picture of my Intel Atom case. Can I ask for your help? What do you think I should do to locate my "windy white noise" problem? Is it the case, fan or something different?

Here's what I've done: when the windy noise started (it usually starts in LDM), I opened up the computer and poked-stopped the 3 fans (2 rear case fans connected to motherboard, 1 processor fan), with a pencil to see if they will go away, they didn't. :)

Later, I will tinker with my lts.conf and set the VOLUME = 50. Also, when I run alsamixer via ltsp-localapps xterm, and set Playback to mute, the noise doesn't disappear, so it must not be the Playback, mp3, or movies.

Also, I will try buying one of those USB sound cards and PCI sound card just to see if it disappears before I buy more units of Intel Atom and its casing. Thanks for reading.

---

### Post by AlexanderDGreat on 2009-10-20
Hey I fixed this problem by installing mplayer as a local app! And updating my chroot environment!

Now, I can barely hear the wind.

---

