---
title: "USB Capture Very Buggy"
date: 2010-08-12
forum: Virtualisation
---

### Post by X5-655 on 2010-08-12
I aint flashing my cars PCM when it sees the datastream like that..  VirtualBox with my USB to GM OBD adapter, with XP as the guest OS.

[http://www.youtube.com/watch?v=dCAhyUQQfNc](http://www.youtube.com/watch?v=dCAhyUQQfNc)

Any ideas why it's capturing the USB data so flakey like that?

---

### Post by X5-655 on 2010-08-14
*bump*

I'm starting to find linux forums and help rather slow and painful to get answers for...

PLEASE help me!!

---

### Post by Tamalin on 2010-08-17
I don't think that XP works out of the box with VirtualBox in all instances.  I've had problems with USB as well, with the inability to connect to certain devices.  The answer for me was to view XP's drivers (Under "Administrative Tools" > Computer Management > System Tools > Device Manager) and I saw the USB ports on my computer were listed with a ? indicating that they were missing the proper driver.  So I installed the driver provided by VB, and all was well after that.

Good Luck!

---

### Post by X5-655 on 2010-08-17
No driver issue here, it's not that it's not detected, but it seems that the USB timing isn't very reliable, as it can't sync with my cars computer, whereas booted actually into windows doesn't have this issue.

---

