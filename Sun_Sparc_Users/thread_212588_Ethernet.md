---
title: "Ethernet?"
date: 2006-07-10
forum: Sun Sparc Users
---

### Post by gevans on 2006-07-10
So now that my machine is up and running all is good, except that ubuntu doesn't detect my network card.

I know that the card is working because i was ssh'ed into that box 5 minutes prior to installing ubuntu (it was running NetBSD). In NetBSD the network card is labeled as le0 and works great, so can someone help me and explain how I go about getting it working in ubuntu?

Thanks

Greg

---

### Post by bigken on 2006-07-10
try changing it to eth0

---

### Post by gevans on 2006-07-10
Sadly I have tried that. Ubuntu doesn't (from what I can see in dmesg and /dev) even recognize that the card is there :/  

any good cli utilities that I can use to try and find it?

Thanks

Greg

---

### Post by gevans on 2006-07-10
"sudo modprobe sunlance" made it work. Got the idea from [HERE]("http://mland98.rc.kyushu-u.ac.jp/text/NIC_info.txt")

w00t! now how do I make that a permanent change so it always loads at boot?

---

### Post by GTvulse on 2006-07-10
1) Add the name of the module to the /etc/modules file

or (I think this is a better approach),

2) Create a file in /etc/modprobe.d with whatever name you fancy and place there the line:
```
alias eth0 sunlance
```

Only one of the two are needed.

As well I suggest you run a "sudo depmod -a", it would seem the kernel dependencies database is not up to date

---

### Post by gevans on 2006-07-11
Thanks dradul! the alias file in /etc/modprobe.d worked like a charm.

---

