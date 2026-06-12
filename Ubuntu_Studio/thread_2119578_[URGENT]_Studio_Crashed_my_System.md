---
title: "[URGENT] Studio Crashed my System"
date: 2013-02-24
forum: Ubuntu Studio
---

### Post by n4pgw on 2013-02-24
I was using Ubuntu 12.04 LTS and added xubuntu-desktop, kubuntu-desktop and gnome classic.  

I am guessing that one of these installed Studio.  I don't know which one, probably kubuntu.

Now my computer boots with a Ubuntu Studio symbol circling in the center of the screen, and then locks up with a dead screen that looks like two-color gray-scale picture of sun rays radiating from the bottom right corner.

I originally got to grub once and tried to load the safe mode for graphics restricted version, but then it rebooted and I no longer can get to grub.  The computer just starts with the center piece for Ubuntu Studio and stops with a blank desktop as described above.

alt-t, ctrl-t, alt-ctrl-t, alt-win-t, ctrl-win-t, win-t, none of these brings up the terminal window.

I am now DIW and would hate to have to reinstall again.

Thanks

---

### Post by n4pgw on 2013-02-24
Reinstalling!

---

### Post by tartalo on 2013-02-24
> **n4pgw said:**
> I am guessing that one of these installed Studio.  I don't know which one, probably kubuntu.

Nothing in Kubuntu-desktop's dependencies points to Ubuntu studio.

You can try this to check yourself:
sudo apt-get install -s kubuntu-desktop
(-s means simulate, nothing gets actually installed)

---

### Post by n4pgw on 2013-02-24
LOL, too late to simulate, but I am back up and running again.  

Well, I need to fix lunch and then start finding all the software packages I installed again.

---

