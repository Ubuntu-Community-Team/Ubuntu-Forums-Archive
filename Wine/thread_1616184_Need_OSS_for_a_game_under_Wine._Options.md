---
title: "Need OSS for a game under Wine. Options?"
date: 2010-11-07
forum: Wine
---

### Post by nobodysbusiness on 2010-11-07
I want to play Half Life 2 under Wine on my Ubuntu 10.10 box. Unfortunately, there's an annoying [bug]("http://appdb.winehq.org/commentview.php?iAppId=2095&iVersionId=2890&iThreadId=60008") with Pulse/ALSA and my sound card, so I need to run the sound through OSS for that game. Unfortunately, [OSS3 has been removed]("http://vanvalkinburgh.org/blog/3153") from the 10.10 kernel. So I suppose that I have some options:

1.) Install 10.04, where OSS is still in the kernel, but I miss out on the 10.10 features.

2.) Compile my own kernel with OSS3, which would mean re-compiling when a new version of the kernel with security patches is released, right? A bit of a hassle.

3.) Use OSS4 instead. I'm happy with PulseAudio for most basic tasks, so I wouldn't mind if there was a method that continued to use PulseAudio for most things, but allowed OSS4 to be used by Wine. Does such a method exist?

Anyway, what do you think my best bet would be? I'm open to suggestions.

---

### Post by dino99 on 2010-11-08
install the Lucid kernel 2.6.35

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by gradinaruvasile on 2010-11-08
You may try to use Esound emulation. Just install the supporting PulseAudio packages, run winecfg and select esound output. If Esound still exists in Ubuntu, that is...


Im glad that i installed Debian...

---

### Post by nobodysbusiness on 2010-11-08
Thanks, dino99! It seems to be working a lot better now.

For those in future who want to follow my steps, I went to:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)

I installed three deb files:
linux-headers-2.6.35-020635rc1_2.6.35-020635rc1_all.deb
linux-headers-2.6.35-020635rc1-generic_2.6.35-020635rc1_amd64.deb
linux-image-2.6.35-020635rc1-generic_2.6.35-020635rc1_amd64.deb

When I rebooted, it was using the kernel installed above, with OSS3 working. I could then configure wine to use OSS with "winecfg" and launch HL2 with:
wine Steam.exe -applaunch 220 -novid -width 1600 -height 900 -dxlevel 70 -heapsize 512000

It seems to work better now. Thanks again for your help.

---

