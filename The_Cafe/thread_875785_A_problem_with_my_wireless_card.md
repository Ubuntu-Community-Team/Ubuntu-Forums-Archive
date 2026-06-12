---
title: "A problem with my wireless card?"
date: 2008-07-31
forum: The Cafe
---

### Post by miggols99 on 2008-07-31
I think this is really strange. I bought a new wireless card, with it being advertised as Linux compatible and recommended by someone here on the forums. At first it worked great. Then when I rebooted Ubuntu it suddenly refused to work. Network manager, Wicd and wifi-radar all didn't connect. I even tried to make the network stop using WPA, but it still didn't connect. The module is rt61pci I think...or something like that.

---

### Post by miggols99 on 2008-08-01
*bump*

And also, it can detect wireless networks, and it can't connect in Windows either...

---

### Post by perce on 2008-08-01
If it doesn't work in two different OSs than you probably have a hardware problem.

---

### Post by miggols99 on 2008-08-01
> **perce said:**
> If it doesn't work in two different OSs than you probably have a hardware problem.
Well I don't think so...I just loaded up a Kubuntu 8.04 live CD and it's working fine. I'm posting this from it right now. Maybe it's sorted itself out?

*reboots to check if Ubuntu can connect*

---

### Post by miggols99 on 2008-08-01
Ok it looks like the wireless card is actually working fine. In the live CD, it works perfect. But when I install (even on a fresh install) it just doesn't work. Maybe I could try a different distro?

---

### Post by FuturePilot on 2008-08-01
Perhaps the module isn't getting loaded on an actual install?
I'm not sure what module it uses but if you know you could check with 
```
lsmod
```

If it happens to not be loaded you could try and load it with
```
sudo modprobe module-name
```

Just kind of a guess, might be worth a shot.

---

### Post by miggols99 on 2008-08-01
Well I'm sure it is, because it can still detect the wireless networks..I'll try it anyway ;)

---

### Post by miggols99 on 2008-08-02
Nope, doesn't seem to work. Maybe I should try the 8.04.1 disk instead? Or a different distro?

---

