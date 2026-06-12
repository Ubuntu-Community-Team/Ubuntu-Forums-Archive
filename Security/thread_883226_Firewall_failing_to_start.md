---
title: "Firewall failing to start"
date: 2008-08-07
forum: Security
---

### Post by wbutchart on 2008-08-07
Hi up until today my ubuntu (8.04) was loading with the graphical loading screen.  Now it loads with the text stuff.  Everything is ok apart from it says it has failed to start firestarter firewall.  Does this mean my computer is now open to hacking? does anyone know how to fix this problem? thanks.

---

### Post by cariboo on 2008-08-08
Firestarter is no longer supported it is avised to use ufw which is installed by default to enable it in a terminal:

```
ufw enable
```

For more info about ufw see:

```
man ufw
```

If you haven't installed any servers you should be ok. to check for open ports go to System-->Administration-->Network Tools-->Scan
type in localhost and click the scan button. IF you have no extra servers running you should only see port 631 open. It is needed for the cups printing system and only be accessed from your computer by default.

Jim

---

### Post by hyper_ch on 2008-08-08
firestarter is no firewall

and very likely you don't even need to play around with the firewall anyway.

---

### Post by wbutchart on 2008-08-08
If thats the case then why has the start up changed from graphical to test.  Its as if my ubuntu is trying to alert me to the failure.  Why the sudden start up change?.

---

### Post by Titan8990 on 2008-08-08
Did you recently install KVM or vmware w/ networking?

---

