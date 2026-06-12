---
title: "ubuntustudio, jack, rt, xruns"
date: 2008-12-01
forum: Ubuntu Studio
---

### Post by ameisevinyl on 2008-12-01
Heyho,

i switched from 8.04 to 8.10 
i got great audio realtime perfomance
with freebob, jackd, ardour, jamin in 8.04
with the ubuntupackages. but now it seems
as if something changed:

8.10 cannot be used out of the box for serious audio works.
so i did the usual stuff:

downloading rtirq and setting the priorities
adding some lines in /etc/security/limits.conf
(memlock, rtprio ...)
(also tried the ubuntustudio-control app)

adding raw1394 to audio group

stopped ACPI (or APCI i always mix up these two)

i also killed NetworkManager, removed compiz,
removed closed-source ATI-driver,
and tried to renice Xorg

but:
i never had a stable system:
on day it worked somehow the other day it gave me horrible performance:

a lot of xruns in jack, even under more or less no CPU-load

I tried to kill several deamons which i thought may cause the evil
behavior but as there are so many process in the output of top
and ps -A i came to the conclusion i should ask someone
professional:

any hints why jack is not performing right in 8.10
while i has done in 8.04?
any new realtime tasks that might interfere with
jackd?
(btw: i killed pulseaudio before i started jack)

does it makes sense to someone to upgrade already to 9.04?
i read on the ubuntustudio page that there are issues with 
the 8.10 release concerning the NetworkManager/Kernel/Shutdown-behaviour
(btw: that's true: my laptop did not shutdown correctly with the rt-kernel)

thanks a lot!
mart

btw: ardour2.5 showed some annoying bugs on my computer
(not importing audiofiles correctly)
would be great to have ardour2.7 in the ubuntustudio repo
as they went away for me after compiling this manually...

---

### Post by thorgal on 2008-12-01
1- kernel problem. All your changes are OK (rtirq, etc) but without a good RT kernel, that's useless. 8.10 does not have a proper kernel for audio work. Downgrade to 2.6.24.x-rt (don't know if you need more recent, YMMV)

2- ardour2.7 : [www.getdeb.net](www.getdeb.net)

---

### Post by ameisevinyl on 2008-12-02
thorgal, you rule!
thanks a lot!

---

### Post by ingeva on 2008-12-04
> **ameisevinyl said:**
> thorgal, you rule!
thanks a lot!

Thanks for confirming my findings. I couldn't get important audio things to work in 8,10, so I returned to 8.04 Hardy. There are still some issues with ALSA though, but there's so much I have to learn .... :)

---

### Post by cobrapatrol on 2009-02-14
I have the same problem using 8.10 and want to downgrade to 8.04 to get RT.  Are there any guides to downgrading from 8.10 to 8.04?  

Thanks - Jim

BTW,
The 8.10 was my initial Ubuntu Studio image, I did not upgrade.

---

### Post by neu2buntu on 2009-02-15
the problem with ardour 2.5 is a bug and not your setup. the only way as you probably have found to import audio is to drag and drop. cant wait till 3.0 is out ,...as far as i know midi will be included

---

