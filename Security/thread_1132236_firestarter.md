---
title: "firestarter?"
date: 2009-04-21
forum: Security
---

### Post by JakeHinojosa on 2009-04-21
is there a way for me to setup firestarter for a laptop using wireless internet? or is there anything like it?

---

### Post by ytsurk on 2009-04-21
hello

when you start firestarter,

under edit > preferences : Network Settings

you can choose the device
(for you probably Wireless Device (wlan0))

---

### Post by JakeHinojosa on 2009-04-21
> **ytsurk said:**
> hello

when you start firestarter,

under edit > preferences : Network Settings

you can choose the device
(for you probably Wireless Device (wlan0))

it doesnt show that. it says eth1 has some activity. should i use it on that?

---

### Post by ytsurk on 2009-04-21
eth1 propably is your ethernet - cable - connection ..

so, if you use internet via cable,
firestarter then will watch this 'device'

firestarter only cares about one 'device',
so you have to switch to wlan0,
after you managed to setup your wireless connection ;)
(just a guess,
else, maybe your firestarter isn't setup for wlan0 .. )

[edit: mine is setup for all 'devices', eth0, wlan0 .. and an unkown wmaster0]

---

### Post by lovinglinux on 2009-04-21
Have you tried ufw + [gufw](http://gufw.tuxfamily.org/index.html)? It is the recommended [firewall manager](http://www.google.com/search?q=firewall+manager+iptables+ufw+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) now.

---

