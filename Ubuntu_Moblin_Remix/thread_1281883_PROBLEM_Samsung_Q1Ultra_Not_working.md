---
title: "PROBLEM: Samsung Q1Ultra Not working"
date: 2009-10-03
forum: Ubuntu Moblin Remix
---

### Post by mavr83firenze on 2009-10-03
Hi. I am a sorry owner of a Samsung Q1 Ultra. Sorry because i've never had much luck with it. The touchscreen never fully worked on 9.04 and now my 9.10 doesn't even work at all.
Neither Moblin or regular versions work for me.
It starts with a message about a bug in the bios. Then it goes trying to load and it ends up in a flashing screen saying 

drm:intelfb_restore ÈRROR failed to restore crtc configutation: -22

I tried to boot with other options and if i select all of them (noapi etc etc) it loads but work very slow. When installing with this options i get the same problem when booting the system.

Please help. I am really looking forward to a new interface. Can i just install some of this stuff on my 9.04? What packages?

P.S Tried distroupgrade at first. It worked but te system looked unstable and slow. Especially the menu. The rest looked quite fine but no sound and other problems too.

---

### Post by jackmetal on 2009-10-31
Did you manage to get the boot issue fixed (drm:intelfb_restore ÈRROR failed to restore crtc configutation: -22)??

I've run into the same thing on mine after the update to karmic and I've had to go back to PCLinuxOS (since it actually works).  :-(

---

### Post by mavr83firenze on 2009-11-01
do you have a Q1 too? Does that linux works well with it? 9.04 remix worked quite fine for me. Not at best, but it was alright.

---

### Post by jackmetal on 2009-11-01
Yeah, I like 9.04 on my Q1U..  Worked really well.  The upgrade to karmic broke it though - still haven't found a fix for the boot issue, so I'm thinking seriously about moving it back to PCLinuxOS (I used PCLos for years with no problems at all, then switched most of my systems to Ubuntu around version 8.10).  Even 8.10 worked really well on the Q1 for me, but not karmic.  :-(

---

### Post by ulugeyik on 2009-11-02
The solution described here works for Samsung Q1U with Live USB and netbook remix:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421?comments=all)

Unfortunately, the touchscreen does not appear to be working.

---

### Post by lusierra77 on 2009-11-16
Hi.  The touchscreen on 9.04 desktop work, look for touch packages are p reinstalled an so (ipod) for iPhone interface, now kubuntu have on screen k board for typing  ;)

---

### Post by ulugeyik on 2009-12-21
It works very very slow. I can't put my finger on where the problem is.

---

### Post by simple_2k3 on 2010-02-26
I fairly confident the problem is with "netbook-launcher".  It uses 3D acceleration (I think openGL).  Its kinda weird because I have Karmic NBR setup on my q1U and get 50.0 fps with glxgears, but the netbook-launcher is to slow to be useable.  I think I'm giving up on Karmic and starting to play around with Lucid Alpha 3.

---

### Post by mavr83firenze on 2010-03-09
having luck with Lucid? I wanna try that as soon as something a little more stable comes out.

---

