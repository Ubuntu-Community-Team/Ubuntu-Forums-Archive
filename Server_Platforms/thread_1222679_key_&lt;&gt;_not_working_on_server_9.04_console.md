---
title: "key &lt;&gt;| not working on server 9.04 console"
date: 2009-07-25
forum: Server Platforms
---

### Post by kuchenmann on 2009-07-25
Hi! A strange thing happens on my ubuntu 9.04. I can not use the key "<>|" (it is the same key on a german keyboard). All other keys work fine. I am using german keyboard layout. 
It is not a hardware problem! 

This is how the settings in /etc/default/console-setup look like:

XKBMODEL="pc105"
XKBLAYOUT="de"
XKBVARIANT="nodeadkeys"
XKBOPTIONS="lv3:ralt_switch"

---

### Post by LepeKaname on 2009-07-27
Is that only happening in console? or also in other applications?

> 
XKBVARIANT="nodeadkeys"
XKBOPTIONS="lv3:ralt_switch"

Are you sure those values correspond to your keyboard model?

---

