---
title: "Serp4 Upgrade to 8.04"
date: 2008-04-28
forum: System76 Support
---

### Post by farruinn on 2008-04-28
Hi!

I upgraded my Serp4 to 8.04 today but am experiencing some problems. The X server required a dpkg-reconfigure xorg-server before it used the binary nvidia driver and sound is not working.

Is this upgrade supposed to be supported on the Serp4 yet?

Thanks

---

### Post by farruinn on 2008-04-28
Correction: it wasn't using the binary nvidia driver, it was using the open source driver apparently (so I can get full resolution but no GLX). I ran nvidia-xconfig which created an xorg.conf that looked good to me but would not work.

---

### Post by Bromo on 2008-04-28
I have a serp3 and upgraded - and when I put in the latest ubuntu restricted drivers I lost wireless and sound.  The graphics is a bit buggy as well ...

---

### Post by globose on 2008-04-28
I received my new Serval Performance today (not sure what its version is, but obviously is the latest one).

I did a clean install with 8.04 and installed the system 76 drivers (but it told me I didn't need any because ubuntu had all of them already).

The sound does work, but is quieter than it was in 7.10.  After recovering from suspend, I have no sound until I reboot.  What can I do to fix this?

Thanks

---

### Post by farruinn on 2008-04-28
> **globose said:**
> I received my new Serval Performance today (not sure what its version is, but obviously is the latest one).

I did a clean install with 8.04 and installed the system 76 drivers (but it told me I didn't need any because ubuntu had all of them already).

The sound does work, but is quieter than it was in 7.10.  After recovering from suspend, I have no sound until I reboot.  What can I do to fix this?

Thanks

I would *assume* we have the same model (Compal JFL92). I've discovered I'm also having some suspend issues: no video after resuming. I haven't even tried hibernating yet.

---

### Post by thomasaaron on 2008-04-29
The no sound after suspend issue has been filed in a bug report. Follow progress on this issue here...
[https://bugs.launchpad.net/system76/+bug/223742](https://bugs.launchpad.net/system76/+bug/223742)

---

### Post by globose on 2008-05-02
Thanks, the link above worked for me after a reboot on my Serp4.

---

### Post by farruinn on 2008-05-05
> **thomasaaron said:**
> The no sound after suspend issue has been filed in a bug report. Follow progress on this issue here...
[https://bugs.launchpad.net/system76/+bug/223742](https://bugs.launchpad.net/system76/+bug/223742)

For the purposes of this thread: I ended up just installing from fresh and all my problems went away (well, all my Ubuntu related ones :)). Thanks for the link Tom.

---

