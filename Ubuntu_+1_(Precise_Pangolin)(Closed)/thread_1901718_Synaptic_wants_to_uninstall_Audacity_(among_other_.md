---
title: "Synaptic wants to uninstall Audacity (among other apps) when I try to install WINE"
date: 2011-12-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2011-12-29
Kind of stumped on this one. Went to install WINE on my Precise Pangolin desktop machine. However, when I select either 1.2 or 1.3 it insists it will have to uninstall Audacity, along with a whole slew of other items. 

What would be the reason for that? I have successfully run Audacity on machines that had WINE also installed plenty of times. This a bug in 12.04 to report?

Robert

---

### Post by oldos2er on 2011-12-29
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by thatguruguy on 2011-12-29
There's no good reason not to report it as a bug.

Synaptic should tell you what dependant packages have to be removed or changed, so that you can figure out what the conflicts are.

---

### Post by mattduckman on 2011-12-29
If you're on a 64 bit installation, you're probably experiencing the mess of conflicts between 32 and 64 bit libraries. As indicated in this report, the problem is known and will be resolved later

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091)

---

### Post by seeker5528 on 2011-12-29
Just a guess on my part, but I would guess it has something to do with recent updates to ffmpeg and it's related libav*, postproc, etc... packages and WINE or Audacity or one of the things they pull in needing to be updated for compatibility with the newer ffmpeg. 

Later, Seeker

---

### Post by Robertjm on 2011-12-29
Yup, 64-bit install. First time I have ever ventured there so everything else would've been pure 32-bit. Hopefully, later is sooner than late later. :p

> **mattduckman said:**
> If you're on a 64 bit installation, you're probably experiencing the mess of conflicts between 32 and 64 bit libraries. As indicated in this report, the problem is known and will be resolved later

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091)

---

### Post by seeker5528 on 2011-12-29
> **Robertjm said:**
> Yup, 64-bit install. First time I have ever ventured there so everything else would've been pure 32-bit. Hopefully, later is sooner than late later. :p

The list of things that need to be converted to multiarch is getting smaller, the necessary gstreamer stuff is installable now and I think the majority of the other stuff too, still a few of the low level system packages that need some sorting out.

I think there has started to be some work to convert ffmpeg to multiarch, but still seems to be some holdup either in ffmpeg itself or some of the things it depends on.

Later, Seeker

---

