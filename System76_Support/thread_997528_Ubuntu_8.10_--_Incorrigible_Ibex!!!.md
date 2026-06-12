---
title: "Ubuntu 8.10 -- Incorrigible Ibex!?!!"
date: 2008-11-29
forum: System76 Support
---

### Post by MorphWVUtuba on 2008-11-29
I am SO SICK of these #$%@#$% kernel panics!  This is an absolutely PATHETIC release.  This is almost vista-epic-fail territory.  I don't know who's to blame, Ubuntu, Debian, Gnome, Linux, Steve Jobs, who cares?!??  I can't downgrade unless I want to run Hardy in 800x600 & no CF.  THIS SUCKS!!!

I've got the backports kernel modules & System76 drivers installed, so what's the problem?  Am I doing something wrong?

:mad:

---

### Post by thomasaaron on 2008-12-01
Your logs contained this...
error 4 in libglib-2.0.so.0.1800.2
...which may indicate a nautilus bug...
[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg239416.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg239416.html)

and this...

62133.778522] gsmartcontrol[25875]: segfault at 10 ip 00007f40b27b3376 sp 00007fffbf8b5430 error 4 in libc-2.8.90.so[7f40b2739000+169000]
...which may be an amarok bug...
[https://bugs.launchpad.net/ubuntu/+bug/281622](https://bugs.launchpad.net/ubuntu/+bug/281622)

Are you running KDE? What programs are running when it freezes. This looks more software related at first glance.

---

### Post by MorphWVUtuba on 2008-12-01
No, I'm not running KDE.

I was trying to do a large file transfer at the time of this lockup.  I can't remember exactly because I was doing so much moving of stuff around over the weekend, but it may have been while I was using an external drive that was dying.  I've since retired it, and I haven't had any crashes since that time.

I'm removing gsmartcontrol for the time being.  I don't *really* need it.

---

### Post by MorphWVUtuba on 2008-12-01
I'm having a heck of a time here Tom.  My virtual terminals are gone, and whenever my system reboots it hangs on shutdown & it displays absolutely nothing on the screen.

This thing is driving me completely crazy.  I just reinstalled after repartitioning & installing Windows.  I would really like to avoid reinstalling Ubuntu.

---

### Post by MorphWVUtuba on 2008-12-01
Just.  Great.

Now I have nothing after the gdm login.  Blank screen.

There is a reinstall in my future, isn't there?

---

### Post by thomasaaron on 2008-12-01
You have no idea how badly I hate to say this, but it might not be a bad idea. Something is definitely pretty badly hosed.

In your logs, I'm seeing segfaults that pertain to your wireless, amarok, nautilus...

I'm not getting all of this across the board, particularly after installing backports modules.

---

### Post by MorphWVUtuba on 2008-12-01
#-o

</sigh>

amd64 ISO, right?

---

### Post by thomasaaron on 2008-12-01
Correct. Sorry, man.

---

### Post by MorphWVUtuba on 2008-12-02
ARRRGH!!!

Fresh install, fresh apt-get update, system76-driver install, NVIDIA 177 driver install...

Still.  No.  Virtual Terminals.

](*,)

GRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRR!!!

Is this NVIDIA's fault?  Can we sick RMS on them?  Is it time to bring back the Boycott NVIDIA thread?

---

### Post by thomasaaron on 2008-12-03
Yeah, it's the nVidia drivers. That's the first I've heard of it. Just duplicated it on our shop Serval.

I disabled the nvidia drivers, and VT's work fine. Doing some more testing on this and will report back with my findings.

---

### Post by tvrusso on 2008-12-03
The absence of virtual terminals might be related to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201591](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201591)
and
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/129910](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/129910)

Apparently there have been multiple bugs related to the frame buffer since Gutsy.  It showed up around kernel 2.6.24-12, was apparently fixed, re-broken, fixed, and re-broken multiple times in multiple ways.

On my own (non-system76) Hardy machine with nvidia drivers, I also have blank virtual terminals, despite doing all the tweaks suggested in those launchpad issues.

Note that the virtual terminals *do* exist --- they're just not displaying due to some funkiness in the frame buffer set-up and its interaction with the nvidia driver.  You can actually log in to them and run commands (blind).  It's really annoying. ](*,)

---

### Post by thomasaaron on 2008-12-03
Tried fully updating and installing proposed updates as well. No dice.
We need to get a bug report going against nvidia-glx-177 on this one.

---

### Post by MorphWVUtuba on 2008-12-03
Let me know if you need me to file a bug report with NVIDIA.

I'm starting to think I should have made two different forum threads here, cuz I have two problems:  the blank terminals AND I am still getting the kernel panics.  I'm running a memtest now, & will report back on that.

But this 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)
is interesting.  Seems to match my symptoms pretty well.  I have 200MB+ syslog & messages files right now, blown up with recurring "swapper Tainted" messages, etc.  A span of 10 minutes of this stuff is over 95% of the contents of this file.

Maybe this is something where I can start to put cracks in the wall with my head...

](*,)

---

### Post by thomasaaron on 2008-12-03
Did you...

sudo apt-get install linux-backports-modules-intrepid

---

### Post by MorphWVUtuba on 2008-12-03
Yes, I did.  So did the people in that bug report.  I'm trying the patch suggested there from upstream, which requires uninstalling the backports package & installing a new iwlagn driver.

I'll report back...

---

### Post by MorphWVUtuba on 2008-12-03
No dice.  It appears that the patch I applied from bug #286285 is not compatible with the Intel 5300.  Any thoughts other than this?

](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by thomasaaron on 2008-12-04
I did some searching on this, and it appears that they had the same bug with the nvidia-glx-173 driver. It looks like they got it fixed (although, I tried the -173 driver on the Serval, and it doesn't seem to fix the VT for that model).

Carl says he remembers this happening with previous versions of Ubuntu in the past, and it always gets fixed.

Other than file a bug report on it, I'm not sure what else we can do at this point. You can disable nvidia, reboot and use nv for when you need the VT -- but that's got to be the stupidest workaround in the history of workarounds.

I'm pretty sure a bug report is the way to go.

---

### Post by MorphWVUtuba on 2008-12-04
What about the continuing kernel panic?

---

### Post by thomasaaron on 2008-12-04
This is weird. I'm not getting this from anyone else.

Please let go to your driver and create support logs and email them to me immediately after rebooting from the next kernel panic (so that it's easy for me to locate the freeze).

---

