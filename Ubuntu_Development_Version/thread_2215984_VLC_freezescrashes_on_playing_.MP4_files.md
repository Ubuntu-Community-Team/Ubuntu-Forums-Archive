---
title: "VLC freezes/crashes on playing .MP4 files"
date: 2014-04-09
forum: Ubuntu Development Version
---

### Post by Roosje on 2014-04-09
Is anyone else having this issue? And is there a fix for it? I am back to 13.10 on my second partition at the moment, because a HTPC without playing video is kinda useless ;-)

---

### Post by SeijiSensei on 2014-04-09
VLC plays MP4 files for me.  I'm using this version from the 14.04 repos:  2.1.2-2build2 I tried both an old file in 480p with "hard" subtitles and a very recent one in 1080p with H.264 video, AAC audio, and *SS subtitles.  I don't have any encodes with 10-bit color in the MP4 container to test that combination.

I suggest giving [SMPlayer]("http://smplayer.sourceforge.net/") a try if you're looking for an alternative to VLC.  It's in the repositories.

---

### Post by Roosje on 2014-04-09
I have installed SMPlayer, but it has terrible screen tearing that no amount of tinkering with V-Sync and power settings in the propriety NVIDEA driver fixes, where VLC plays like a dream (if it plays)

---

### Post by SeijiSensei on 2014-04-09
In smplayer, did you select "vdpau" in the drop-down box at the top of Options > Preferences > General > Video?  

On my earlier machine with an NVIDIA 9500GT using the proprietary driver and [VDPAU]("http://en.wikipedia.org/wiki/VDPAU"), SMPlayer ran smoothly.

---

### Post by andrew.46 on 2014-04-09
> **Roosje said:**
> Is anyone else having this issue? And is there a fix for it? I am back to 13.10 on my second partition at the moment, because a HTPC without playing video is kinda useless ;-)

It might be worth you while to tinker a little with the vlc Video Output settings and select one that makes your system a little happier.

---

### Post by Roosje on 2014-04-10
Just got this in my email from my bug report:

** Changed in: libav (Ubuntu)
       Status: Confirmed => Fix Committed

** Changed in: libav (Ubuntu)
       Status: Fix Committed => New

so i think i wait till the fix rolls in :-)

---

### Post by andrew.46 on 2014-04-10
Could you give the link to the bug report?

---

### Post by Roosje on 2014-04-10
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1288206](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1288206)

---

### Post by andrew.46 on 2014-04-10
Thanks for posting that, you have confirmed my decision to [compile vlc against FFmpeg ]("http://ubuntuforums.org/showthread.php?t=2141949")rather than the fork :)

---

### Post by CyborgAlpha on 2014-08-16
I've noted the date of the last post > April 10th, 2014
And the notice; > [COLOR=#0044aa ]**Hello CyborgAlpha, this forum is for the discussion of  Utopic Unicorn issues and Trusty Tahr point release testing only. The  Utopic release schedule can be found [ here]("https://wiki.ubuntu.com/UtopicUnicorn/ReleaseSchedule")**[/COLOR]
Yet -- these errors can found in the upgrade from 13.10 to 14.04 as of August 16th, 2014 --- including fresh install from the iso.

I removed mplayer2 and roled back to mplayer , resolving much of the video problems - but vlc still crashes on start-up.
I'm not going to give up on Ubuntu - but move further toward development.

---

### Post by Elfy on 2014-08-16
Thread closed.

If you've got an issue with 14.04 take it to the support areas now.

---

