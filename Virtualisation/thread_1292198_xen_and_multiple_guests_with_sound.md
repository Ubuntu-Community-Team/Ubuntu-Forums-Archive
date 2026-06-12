---
title: "xen and multiple guests with sound"
date: 2009-10-15
forum: Virtualisation
---

### Post by MisterE2002 on 2009-10-15
i've installed the xen kernel. My Dom0 sound works (installed alsa-base) but in the virtual machines it does not work. I like to have it working in hvm and paravirtual machines. It seems that it locks the card when playing.

At [http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:qemu](http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:qemu) i see that qemu is responsible. And maybe "--enable-alsa' when compiling should make it work?
If i run "/usr/lib/xen-3.2-1/bin/qemu-dm --audio-help" i indeed don't see alsa.

So the questions are:
1: if i compile it with "--enable-alsa' can i run hvm an paravirtual machines with sound?
2: if so, why is it not default? (i know xen is mostly used for servers, but anyway). Is the another distro which enables it by default?
3: Is it possible to enable alsa at an easy way?
4: Can i use OSS at dom0 level to mix the sounds from ALSA domU's?

PS: i know that it's possible to pass through the soundcard, or use PulseAudio, but i rather do it the "right" way.

---

