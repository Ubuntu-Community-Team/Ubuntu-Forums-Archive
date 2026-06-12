---
title: "Ubuntu 10.10 Remote user requests unknown."
date: 2011-05-23
forum: Security
---

### Post by BULLIT22 on 2011-05-23
Hey all, I'm having a bit of a problem. I seem to keep getting these requests. It just seems to happen every so often for the past half week. Does anyone have know what they may be from, I'm not very savvy on security but am willing to learn. Thanks for the help,

[[IMG]http://img37.imageshack.us/img37/3710/screenshotjvh.th.png[/IMG]](http://img37.imageshack.us/i/screenshotjvh.png/)

Uploaded with [ImageShack.us](http://imageshack.us)[IMG]http://img37.imageshack.us/i/screenshotjvh.png/[/IMG]

---

### Post by Irihapeti on 2011-05-24
It looks like you've got remote desktop enabled.

It comes disabled by default. Perhaps you (or someone else) had a look at it, turned it on and forgot about it.

Disable it, or, better, uninstall it if you don't need it. It's one of the most common ways that desktop users get hacked.

---

### Post by spynappels on 2011-05-24
I hope you clicked Deny every time? Is it the same IP address every time? You could add it to hosts.deny or block it in iptables (not sure if hosts.deny works with VNC traffic, iptables definitely will)

---

### Post by BULLIT22 on 2011-05-24
I did disable remote desktop after I realized it had been left on. I don't use that desktop much and was just curious as to what may be happening. Thanks for the info, and I'll look into IPtables, seems useful.

---

### Post by spynappels on 2011-05-24
iptables is the default Ubuntu firewall, and often unnecessary on desktop machines, but it would stop the attempts in your case. Have a look at Bodhi.Zazen's security stickies, they are invaluable.

---

