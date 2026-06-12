---
title: "jack and firefox"
date: 2008-07-15
forum: Ubuntu Studio
---

### Post by Capoeira on 2008-07-15
i found this thread but wonder if it is up to date and also it is confusing: [http://ubuntuforums.org/showthread.php?t=208488&highlight=realtime-lsm](http://ubuntuforums.org/showthread.php?t=208488&highlight=realtime-lsm)

The thing is: i can't start jack with firefox running. and with jack running i get no sound in firefox (youtube for example) when loading ff after

what is the most simple solution for this?

---

### Post by thorgal on 2008-07-15
oss2jack is one way (I use it on my debian system) :

- get the fusd kernel module compiled, installed and loaded at boot time
- set up the right udev rules for the /dev nodes created at module loading time (/dev/fusd/control and /dev/fusd/status should be readable/writable by the user or audio group)
- permanently disable the alsa oss emulation layer so that oss2jack does not collide with it
- compile, install and run oss2jack from the command line after you start jackd.

Each of these steps contains its level of difficulty for a non advanced linux user.


alternative : configure pulseaudio so that it can run concurrently with jackd (been there as well myself but I don't need pulseaudio in general so in the end, I chose oss2jack, which is focused on OSS emulation only). Last time I did it, it was a few months ago and jackd or pulseaudio was a bit unstable. It was also a pain in the butt to configure so that it could work. When pulseaudio can use jackd as a sink and source, you can set up /etc/firefox/firefoxrc by setting the FIREFOX_DSP var to padsp.


Conclusion : this is no easy task. I hope you can find some easy to follow guide. I don't have time to write this down proper myself.

---

