---
title: "Two&#8208;way personal firewall"
date: 2008-11-29
forum: Security
---

### Post by XMLove on 2008-11-29
Hi forum! This is my very first post in here! :grin:

I am looking for a two&#8208;way software based firewall for Ubuntu with a [preferably graphical] user interface that does not result in me doing this all the time:
](*,)

The user interface on most Windows firewalls are terrible. I hope the Linux community has come up with better solutions. (For anyone who might be interested, [Lavasoft’s firewall](http://www.lavasoft.com/products/lavasoft_personal_firewall.php) is the least bad for Windows).

What I would appreciate is a good network activity monitor view (too really see what is going in and out of my computer), a good way to deal with new uses/rules setup, and not being a memory hog. Web resource blocking based on URI/IRIs would be great too, but I guess I will not find that in the same software. (Though Lavasoft’s firewall actually support this on Windows.)

I am looking forward to all your great suggestions! :popcorn:

[SIZE="1"]PS: I hope I posted this in the right forum section.[/SIZE]

---

### Post by anthro398 on 2008-11-29
[Firestarter]("http://www.fs-security.com/") is a pretty usable GUI firewall front-end.

---

### Post by cariboo on 2008-11-29
Gufw is the preffered gui firewall interface in Hardy and up as firestarter is no longer being maintianed. 

Iptables is the firewall that is installed by default.

You can install gufw using Add/Remove Programs, Synaptic Package Manager, and of course the command line.

Jim

---

### Post by anthro398 on 2008-11-29
> **cariboo907 said:**
> Gufw is the preffered gui firewall interface in Hardy and up as firestarter is no longer being maintianed. 

Iptables is the firewall that is installed by default.

Jim

Thanks for pointing out Gufw.  It looks promising.  Having looked at the open issues, it looks like it the project has some work to do before it's ready, though.  I use iptables on everything but my laptop and find that firestarter works quite well there.  I wasn't aware that Firestarter was no longer maintained.  I'll keep on eye of Gufw.  Thanks.

---

### Post by bodhi.zazen on 2008-11-29
If you really wish to know what is going on you should look at a packet sniffer, such as snort or wireshark.

If this is too much detail , I understand. In that case as long as you are connected to the Internet you will be probed by would be crackers ;) The GUI tools that have been mentioned just give you some kind of feedback is all.

I also suggest you take a look at the Security thread stickied at the top of this forum.

---

