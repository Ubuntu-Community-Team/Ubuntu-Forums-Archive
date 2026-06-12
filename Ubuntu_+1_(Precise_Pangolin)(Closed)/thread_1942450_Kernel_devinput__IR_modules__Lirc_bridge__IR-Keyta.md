---
title: "Kernel devinput / IR modules / Lirc bridge / IR-Keytable failing with kernel .15+"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-17
This is a little specific, but I thought maybe I could find someone here that uses it and wants to engage in talks about it.

I'm having problems with devinput / streamzap module with kernel .16+. Apparently the LIRC bridge doesn't catch the created events, so IR commands are displayed as ASCII garbage in console, instead of being redirected to the created /dev/lirc* device and then to the target application. I have two streamzap USB IR receivers, thus two /dev/lirc* linked to two xbmc instances. It has worked OK until kernel .15.

It's funny cause all correct modules load with no error and there's no useful info in debug output. It's unusual for me to not understand and have no idea how to fix something. This one is still a mystery to me.

I have seen some reports about ir-keytable problems in its previous versions and some patches available, but I don't feel like that's the way to go.

Regards,
Effenberg

---

