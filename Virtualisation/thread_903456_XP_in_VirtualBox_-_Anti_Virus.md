---
title: "XP in VirtualBox - Anti Virus?"
date: 2008-08-28
forum: Virtualisation
---

### Post by Pa100ka on 2008-08-28
Advice needed please. I've installed VirtualBox 1.6.4 - the debian package from Sun - onto Ubuntu 8.0.4, and installed XP in there for the handful of Windoze applications that I still need.

It's all gone swimmingly, I am pleased to report. However, one question remains:

Presumably, since it uses a virtual network card to connect to the internet, I still need anti-virus and anti-spyware for XP (though not a firewall, as Ubuntu will take care of that). Can anyone confirm?

Thanks,
Palooka

---

### Post by tuxxy on 2008-08-28
Anti VIrus yes if you like, think i got avast on mine :)

The virus will only have an effect on the virtual OS though, your ubuntu should be fine without.

---

### Post by HermanAB on 2008-08-28
Yes, you should at least install ClamWin.  However, since it is a VM, it is very easy to back-up the whole thing: Quit the VM and make a tar ball of the VM directory.  Then, if it gets infected, simply untar the backup.

---

### Post by cszikszoy on 2008-08-28
> **HermanAB said:**
> Yes, you should at least install ClamWin.  However, since it is a VM, it is very easy to back-up the whole thing: Quit the VM and make a tar ball of the VM directory.  Then, if it gets infected, simply untar the backup.


Why mess with tarballs when you can just use the snapshots feature already built into VBox?

---

### Post by Pa100ka on 2008-08-28
Thanks people, for the advice. I'll put in AVG and Spybot then, just to keep it clean.

Palooka

---

### Post by HermanAB on 2008-08-28
Snapshots are usually rather slow compared to tar balls, but they work too.

---

### Post by tuxxy on 2008-08-28
> **HermanAB said:**
> Yes, you should at least install ClamWin.  However, since it is a VM, it is very easy to back-up the whole thing: Quit the VM and make a tar ball of the VM directory.  Then, if it gets infected, simply untar the backup.

Good one, or you could boot into windows safe mode and just restore it back a couple of days

---

