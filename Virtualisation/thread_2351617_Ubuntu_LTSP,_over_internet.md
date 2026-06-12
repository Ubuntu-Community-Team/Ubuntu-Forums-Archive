---
title: "Ubuntu LTSP, over internet?"
date: 2017-02-05
forum: Virtualisation
---

### Post by unf0rg0tt3n on 2017-02-05
Hi all,

I got a dedicated server running with Proxmox VE.
On that server I got Ubuntu 16.04 with LTSP running.

As you know I can't physically go into the server room and plug in some thin clients to make something like LTSP happen, so I need it over internet.
How can this be achieved?
I got a several options which cam into my mind:
1) VPN (which I don't really like to, since it will only be a test/play setup) 
2) Just over the internet (but how?)
3) something like NoVnc(will that actually work?)
4) Replacing LTSP with a Linux Equivalent RDP / RDS ?

Can someone please help me with that?

Thanks in common,
Dennis

---

### Post by ODTech on 2017-02-05
Is it Ubuntu server or desktop?
I'd just use regular old teamviewer if it's the desktop version. If licensing is a issue you could also try Ammyy.

---

### Post by unf0rg0tt3n on 2017-02-05
Thanks for you reply, currently I'm using Ubuntu desktop.
I will check into ammyy, do you have an alternative? Would spice be an option? And how would a second user work in this environment?

---

### Post by ODTech on 2017-02-05
> **unf0rg0tt3n said:**
> Thanks for you reply, currently I'm using Ubuntu desktop.
I will check into ammyy, do you have an alternative? Would spice be an option? And how would a second user work in this environment?

Nevermind me. I didn't fully understand your question.

---

### Post by unf0rg0tt3n on 2017-02-05
Anyone?

---

### Post by Tadaen_Sylvermane on 2017-02-06
LTSP requires pxe booting. It only works on the lan, wont work over the actual internet. Is no way to tell your thin client where to look for the pxe boot file, that info is handed out by your dhcp server.

---

### Post by unf0rg0tt3n on 2017-02-07
> **Tadaen_Sylvermane said:**
> LTSP requires pxe booting. It only works on the lan, wont work over the actual internet. Is no way to tell your thin client where to look for the pxe boot file, that info is handed out by your dhcp server.

Thanks for your reply!
So is there a windows 2012 rds equilevant, terminal services or something?

---

