---
title: "Virtualizing Win 8"
date: 2012-10-29
forum: Virtualisation
---

### Post by Nick_C on 2012-10-29
Just wondering if anyone has got a Win 8 or Server 2012 VM running under KVM/QEMU on Ubuntu?

---

### Post by cybergalvez on 2012-10-29
> **Nick_C said:**
> Just wondering if anyone has got a Win 8 or Server 2012 VM running under KVM/QEMU on Ubuntu?

I have Win8 runing under VirtualBox, little issues excpet the native netflix app does not work

---

### Post by c911darkwolf on 2012-10-31
> **Nick_C said:**
> Just wondering if anyone has got a Win 8 or Server 2012 VM running under KVM/QEMU on Ubuntu?

Why would you want too?

Just kidding : ) 


Virtualbox seems to run it ok, seemed a little laggy at first, but a restart seemed to clear it up.  

Other then just checking it out WinXp is prob the better windows to emulator for actually doing something.

---

### Post by Nick_C on 2012-11-03
Done a bit more experimenting and it seems that Win 8 cannot be virtualised by KVM yet because there are no VirtIO drivers written for it yet.  Also no Spice driver written yet either.

---

