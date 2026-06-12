---
title: "Vista Guest on VirtualBox internet connection."
date: 2007-07-13
forum: Virtualisation
---

### Post by xl_cheese on 2007-07-13
For forum reference:

I had trouble making the ethernet card work within my Vista Ultimate VM guest.

After many efforts and time spent to make it work I found this.
[http://www.arsgeek.com/?p=1348](http://www.arsgeek.com/?p=1348)

Bingo.  All works now.

---

### Post by alecjw on 2007-07-21
Thanks. This worked great for me :)
For anyone else attempting this, the bzipped finished ISO image is attached, and you can get un-bzipped versions from [here]("http://www.sendspace.com/file/0rf5v4") or [here]("http://rapidshare.com/files/44236562/VistaVBoxNetDrivers.iso").

---

### Post by damastax68 on 2007-12-20
when i try to use the iso it says application not found /d.....:mad:

---

### Post by Kiliankoe on 2009-04-10
My Vista says it already has the newest drivers and won't accept this packet. When I uninstall the current drivers the Network Adapters aren't shown in the Device Manager anymore.

Any ideas?

---

### Post by Perryg on 2009-04-10
> **Kiliankoe said:**
> My Vista says it already has the newest drivers and won't accept this packet. When I uninstall the current drivers the Network Adapters aren't shown in the Device Manager anymore.

Any ideas?

Have you tried to use the Intel virtual adapter in VBox to get this to work?
Might want to look at chapter 6 of the VBox users manual.  It covers this there.

---

