---
title: "In XP (for work) how do you disable the CAPS LOCK function? [SOLVED]"
date: 2007-03-15
forum: Windows
---

### Post by RAV TUX on 2007-03-15
This drives me crazy!....is there any way to disable the caps lock function?

---

### Post by Trebuchet on 2007-03-15
Registry hack: [http://dev.kanngard.net/Permalinks/ID_20050509163712.html](http://dev.kanngard.net/Permalinks/ID_20050509163712.html)

There's also a linked application on that page that permits turning it on and off and might be a better idea than permanently disabling Caps Lock.

---

### Post by RAV TUX on 2007-03-16
> **Trebuchet said:**
> Registry hack: [http://dev.kanngard.net/Permalinks/ID_20050509163712.html](http://dev.kanngard.net/Permalinks/ID_20050509163712.html)

There's also a linked application on that page that permits turning it on and off and might be a better idea than permanently disabling Caps Lock.
thanks I did find this also:
[http://johnhaller.com/jh/useful_stuff/disable_caps_lock/](http://johnhaller.com/jh/useful_stuff/disable_caps_lock/)

---

### Post by RAV TUX on 2007-03-16
> **RAV TUX said:**
> thanks I did find this also:
[http://johnhaller.com/jh/useful_stuff/disable_caps_lock/](http://johnhaller.com/jh/useful_stuff/disable_caps_lock/)trying this now:
Disable Caps Lock entirely: [disable_caps_lock.reg]("http://johnhaller.com/jh/useful_stuff/disable_caps_lock/disable_caps_lock.reg")

---

### Post by RAV TUX on 2007-03-16
> **RAV TUX said:**
> trying this now:
Disable Caps Lock entirely: [disable_caps_lock.reg]("http://johnhaller.com/jh/useful_stuff/disable_caps_lock/disable_caps_lock.reg")

This works great!!!!:)

I scanned it for viruses, it comes up completely clean and this works great!

simple awesome!

[http://johnhaller.com/jh/useful_stuff/disable_caps_lock/disable_caps_lock.reg](http://johnhaller.com/jh/useful_stuff/disable_caps_lock/disable_caps_lock.reg)

The YubNub "command prompt" for this is:

> ncl
ncl="no caps lock"
[http://yubnub.org/](http://yubnub.org/)

---

### Post by RAV TUX on 2007-03-16
> **RAV TUX said:**
> This works great!!!!:)

I scanned it for viruses, it comes up completely clean and this works great!

simple awesome!

[http://johnhaller.com/jh/useful_stuff/disable_caps_lock/disable_caps_lock.reg](http://johnhaller.com/jh/useful_stuff/disable_caps_lock/disable_caps_lock.reg)

The YubNub "command prompt" for this is:


ncl="no caps lock"
[http://yubnub.org/](http://yubnub.org/)

to disable this use the YubNub command prompt

> rncl

rncl=remove "no caps lock"

[http://johnhaller.com/jh/useful_stuff/disable_caps_lock/remove_scancode_mappings.reg](http://johnhaller.com/jh/useful_stuff/disable_caps_lock/remove_scancode_mappings.reg)

---

### Post by RAV TUX on 2007-03-19
just to recap this is the most helpful YubNub command prompt I have made....those caps lock people drove me crazy!

here is a random helpful link:
[http://freenode.net/faq.shtml#helpfromstaff](http://freenode.net/faq.shtml#helpfromstaff)

---

