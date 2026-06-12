---
title: "VirtualBox Guest Additions"
date: 2010-01-01
forum: Virtualisation
---

### Post by ..::| Dave89 |::.. on 2010-01-01
I'm running Kubuntu 9.10 in VirtualBox 3.1.2 under Ubuntu 9.10, and would like to know how to enable higher desktop resolutions. I installed Guest Additions, but all it did was enable the mouse integration thing.  I have VirtualBox set up to think it's running Ubuntu, since there was no Kubuntu option.

TIA

---

### Post by jocampo on 2010-01-02
> **..::| Dave89 |::.. said:**
> I'm running Kubuntu 9.10 in VirtualBox 3.1.2 under Ubuntu 9.10, and would like to know how to enable higher desktop resolutions. I installed Guest Additions, but all it did was enable the mouse integration thing.  I have VirtualBox set up to think it's running Ubuntu, since there was no Kubuntu option.

TIA

Did you try the obvious, changing the resolution (after install vbox additions) via Ubuntu: System>Preferences>Display

---

### Post by ..::| Dave89 |::.. on 2010-01-02
Yes, only allows 640x480, 800x600.

---

### Post by Dennis N on 2010-01-02
My recollection (which could be wrong) is that the first time after installing the guest additions, you may have to manually adjust to the correct size. Maximize the window, or drag it out to the desired size. Once its set, VB uses the same size next time you start up. (To guarantee that, use "save machine state" instead of "power down" when quitting.)

---

### Post by ..::| Dave89 |::.. on 2010-01-02
That worked, thanks.  Now I can enjoy it full screen!

---

