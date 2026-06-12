---
title: "Eternity - Raytraced Screensaver for Ubuntu"
date: 2007-10-02
forum: The Cafe
---

### Post by parker13 on 2007-10-02
The Eternity Screensaver project is a new screensaver which displays animations of raytraced scenes. There are a number of plugins available, most of which relate to Ubuntu and its derivatives.

I posted a HOWTO on these forums a few weeks back, but since then a few animations have been added including a brand new Ubuntu Studio screensaver. Here are a few screen shots:

[IMG]http://parker1.co.uk/eternity/screenshots/_thb_ubuntulogo.png[/IMG]
Video: [http://video.google.com/videoplay?docid=-6787049700523684795&hl=en](http://video.google.com/videoplay?docid=-6787049700523684795&hl=en)

[IMG]http://parker1.co.uk/eternity/screenshots/_thb_eternalubuntu.png[/IMG]
Video: [http://video.google.com/videoplay?docid=3522833444734552124&hl=en](http://video.google.com/videoplay?docid=3522833444734552124&hl=en)

[IMG]http://parker1.co.uk/eternity/screenshots/_thb_eternalstudio.png[/IMG]
Video: [http://video.google.com/videoplay?docid=-5157423048250793991&hl=en](http://video.google.com/videoplay?docid=-5157423048250793991&hl=en)

[IMG]http://parker1.co.uk/eternity/screenshots/_thb_SE-3D-3.png[/IMG]
Video: [http://video.google.com/videoplay?docid=-5223711495134257826&hl=en](http://video.google.com/videoplay?docid=-5223711495134257826&hl=en)


The repository has been moved to Launchpad's new PPA service, so I've updated the instructions to reflect this. There are now versions for both Feisty and 7.10.

Eternity should work with the screensavers in Gnome, KDE and Xscreensaver. It also works if you're running Beryl/Compiz. There are a few known issues with dual monitor setups and certain laptop graphics cards. Any information or bug reports would be helpful.

Website and download instructions, plus wallpapers and videos of the screensaver in action:
[http://parker1.co.uk/eternity/](http://parker1.co.uk/eternity/)

Tutorial thread:
[http://ubuntuforums.org/showthread.php?t=516526](http://ubuntuforums.org/showthread.php?t=516526)

Garry.

---

### Post by kebes on 2007-10-02
Wow! Those screensavers are beautiful!

Are they pre-rendered or ray-traced in realtime? How much CPU/GPU power does it take to display them?

---

### Post by Perfect Storm on 2007-10-02
Amazing work!

---

### Post by parker13 on 2007-10-02
> **kebes said:**
> Wow! Those screensavers are beautiful!

Are they pre-rendered or ray-traced in realtime? How much CPU/GPU power does it take to display them?

They're pre-rendered, which took quite a few days per animation. That's the beauty of it;  they take very little CPU to display (they're just MPEG2 files).

Most screensavers try to generate everything on the fly with fancy coding techniques, but I figured I could get better results by rendering in advance.

---

### Post by kebes on 2007-10-02
> **parker13 said:**
> Most screensavers try to generate everything on the fly with fancy coding techniques, but I figured I could get better results by rendering in advance.

Very nice work! I'm going to try installing them tonight!

---

### Post by Paul820 on 2007-10-02
Oooh, i used two of them in feisty, i think i'll get them for my new gutsy now. Thanks :)

---

### Post by Paul820 on 2007-10-02
They don't go full screen anymore, are they supposed to be that small? :(  I'm using gutsy beta. The screenshot shows the screensaver selection preview but the screensaver activated is the same.

---

### Post by parker13 on 2007-10-02
> **Paul820 said:**
> They don't go full screen anymore, are they supposed to be that small? :(  I'm using gutsy beta. The screenshot shows the screensaver selection preview but the screensaver activated is the same.

It's supposed to be full screen. It does work fine on my Gutsy beta machine... very strange. There's some new code which fixes preview issues and helps with twinview - maybe it's broken something for you. Damn.

---

### Post by parker13 on 2007-10-03
> **Paul820 said:**
> They don't go full screen anymore, are they supposed to be that small? :(  I'm using gutsy beta. The screenshot shows the screensaver selection preview but the screensaver activated is the same.

I've raised a bug on Launchpad for this issue:

[https://bugs.edge.launchpad.net/eternity/+bug/148437](https://bugs.edge.launchpad.net/eternity/+bug/148437)

Thanks for reporting it.

---

### Post by bonzodog on 2007-10-03
So when are these going to be available for other distro's as source code?

i've noticed that currently the ray-traced images are all ubuntu-centric. It would be nice to see more generic images that would allow other distro's to take advantage of this.

I use Zenwalk Linux now, with XScreensaver. My current set-up uses the Electric Sheep screensaver.

---

### Post by parker13 on 2007-10-03
> **bonzodog said:**
> So when are these going to be available for other distro's as source code?

i've noticed that currently the ray-traced images are all ubuntu-centric. It would be nice to see more generic images that would allow other distro's to take advantage of this.

I use Zenwalk Linux now, with XScreensaver. My current set-up uses the Electric Sheep screensaver.

Great idea. The source code is available in bazaar on Launchpad and *should* compile for other distros. However, I'll put some work into testing it to make sure it does.

Like you said, the plugins are currently very Ubuntu-centric. I guess the intention is to start with a focused target audience, although I agree that more generic stuff may have a wider appeal. A job for the future.

---

