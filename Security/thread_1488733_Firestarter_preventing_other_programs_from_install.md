---
title: "Firestarter preventing other programs from installing"
date: 2010-05-20
forum: Security
---

### Post by rob22941 on 2010-05-20
I have an issue with Firestarter, it's not allowing me to install or update any files. This is the error message I'm getting.

[I]A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.[/I]

Now I try to open Firestarter to see what the issue is and I get the same error message. I've tried completely removing and reinstalling firestarter through the package manager and it doesn't allow me to do so. Any ideas would be much appreciated.

---

### Post by bodhi.zazen on 2010-05-20
> **rob22941 said:**
> I have an issue with Firestarter, it's not allowing me to install or update any files. This is the error message I'm getting.

[I]A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.[/I]

Now I try to open Firestarter to see what the issue is and I get the same error message. I've tried completely removing and reinstalling firestarter through the package manager and it doesn't allow me to do so. Any ideas would be much appreciated.

I would remove firestarter and use an alternate tool, either ufw or gufw.

```
sudo apt-get install -y firestarter && sudo apt-get -y purge firestarter
```

You need to purge firestarter or it leave config files which can cause problems.

---

### Post by uRock on 2010-05-20
I second bodhi.zazen's advice. Firestarter is out dated. GUFW is a great, yet simple, GUI application for making adjustments.

---

### Post by rob22941 on 2010-05-21
Ok, I got firestarter removed. I'm checking out ufw and gufw as we speak thanks fellas.

---

### Post by LukeKendall on 2010-05-26
I had the same problem.  Elsewhere I found a message about (temporarily) starting Firestarter by doing something like dbus-launch firestart, which worked.  Still didn't allow it to start normally (I mean, I always had to use the dbus-launch).

But this Firestarter failure was happening during a weird network problem, in which access to the internet was fine, but the local network, 192.168.1.0, was not working at all.  E.g. errors of "Network is unreachable" when I tried to ping anything on the local network.

Then one of the older 3 local machines (all run Ubuntu) spontaneously rebooted (it's never done that before), and the local network came good basically as soon as it went down (even a stalled print job from one of the other PCs to the print server, sent days before, suddenly printed).

And Firestarter now starts up just fine.

A friend suggested that if the old machine had been responding to ARPs for addresses it shouldn't, then I might see a 'network unreachable'.

Anyway, just thought I'd share that snippet of data.  It might be relevant.

luke

---

