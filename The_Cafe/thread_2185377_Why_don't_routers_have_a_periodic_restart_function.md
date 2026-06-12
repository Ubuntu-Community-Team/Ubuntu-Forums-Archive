---
title: "Why don't routers have a periodic restart function? [Rant]"
date: 2013-11-02
forum: The Cafe
---

### Post by kurt18947 on 2013-11-02
This morning I couldn't connect to a wireless router/access point.  I figured something happened with the notebook or O.S.  Did the usual restart, swap out a different USB wifi adapter.  Nothing, still couldn't connect.  Rebooted the daisy chained router/wireless access point, still can't connect.  Grrrr.  Checked the upstream router, sure enough, couldn't get a wired connection there.  Unplug, wait, plug in and everything worked.  DD-WRT has a function where a user can set the device to reboot itself periodically.  Why can't manufacturers add this function?  It seems like any consumer quality complex electronic device, be it router, DVR or similar can benefit from a periodic reboot.  Perhaps they (manufacturers) like to think their products' design & reliability is such that they don't require such a function?  If so, I'd beg to differ.

---

### Post by Lars Noodén on 2013-11-02
Can you replace the firmware with OpenWRT or DD-WRT?

---

### Post by ian-weisser on 2013-11-02
> **kurt18947 said:**
>  DD-WRT has a function where a user can set the device to reboot itself periodically.  Why can't manufacturers add this function?

Then we would have a bunch of "My router reset in the middle of my upgrade and now my system is broken" and "The install .iso was interrupted during download but I installed anyway and now nothing works" and "My video-streaming/VPN/VNC-session/backup/whatever was interrupted by the stupid router resetting" help requests.

My cheap router has been solid for six months without a restart. Only gets flaky when too many connections at once...usually an unconstrained torrent client overwhelming it's connection tracking.

---

### Post by kostkon on 2013-11-02
Frequent disconnections are not good for your internet connection speed because it usually means that your ISP's switch thinks that there is a problem with your line and syncs you at lower speeds.

---

### Post by tgalati4 on 2013-11-02
I think that lockups happen when the router's operating system runs out of RAM.  dd-wrt has a pretty good handle on RAM management, but it will only run on routers with larger RAM footprints to begin with.  Cheaper routers with minimal RAM will have more problems.  Also, I've experienced the wireless card locking up in the router, but the network (wired) switch continues to work fine.  This I attribute to heat on the wireless chip and to the antenna being overwhelmed with spurious signals causing the dsp to lock up.

Sometimes opening the router and cleaning the wireless card contacts with an eraser will help.

---

### Post by kurt18947 on 2013-11-02
> **Lars Noodén said:**
> Can you replace the firmware with OpenWRT or DD-WRT?

Nice thought but I'd be hesitant to. The router that flaked is issued by Verizon and has a built-in MoCa bridge (I think that's the proper term) for their FiOS service.  I wouldn't be surprised to learn that the router firmware is customised though I don't know for sure.

---

### Post by kurt18947 on 2013-11-02
> **ian-weisser said:**
> Then we would have a bunch of "My router reset in the middle of my upgrade and now my system is broken" and "The install .iso was interrupted during download but I installed anyway and now nothing works" and "My video-streaming/VPN/VNC-session/backup/whatever was interrupted by the stupid router resetting" help requests.

My cheap router has been solid for six months without a restart. Only gets flaky when too many connections at once...usually an unconstrained torrent client overwhelming it's connection tracking.

I guess that'd be a risk but in DD-WRT the function is optional, just don't check the box.  I had the DD-WRT box rebooting at something like 4 A.M. on Sunday morning when it was HIGHLY unlikely I'd be using it for anything of consequence.

---

### Post by mdrag13 on 2013-11-03
> **ian-weisser said:**
> Then we would have a bunch of "My router  reset in the middle of my upgrade and now my system is broken" and "The  install .iso was interrupted during download but I installed anyway and  now nothing works" and "My  video-streaming/VPN/VNC-session/backup/whatever was interrupted by the  stupid router resetting" help requests.

> **kostkon said:**
> Frequent disconnections are not good for your  internet connection speed because it usually means that your ISP's  switch thinks that there is a problem with your line and syncs you at  lower speeds.

+1

---

### Post by pqwoerituytrueiwoq on 2013-11-03
had that issue with the old verizon modem/router all in one with the wifi , put a WTR54GL (tomato firmware) never gives a issue, would post the uptime but power went out a couple weeks ago, pretty sure it had over 1000 days on it before that happened
expensive router but it never gives a issue unless you count that it is a 10/100 speed and not a 10/100/1000 speed LAN

---

### Post by ssam on 2013-11-04
You could get a light timer, and set it to be on all the time apart from a minute in the early hours. The digital ones can do day of the week.

---

### Post by kurt18947 on 2013-11-04
> **ssam said:**
> You could get a light timer, and set it to be on all the time apart from a minute in the early hours. The digital ones can do day of the week.

Hmmm, now that's a possibility.

---

