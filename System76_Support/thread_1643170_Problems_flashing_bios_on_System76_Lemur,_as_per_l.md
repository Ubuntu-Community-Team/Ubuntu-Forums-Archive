---
title: "Problems flashing bios on System76 Lemur, as per launchpad bug 640842"
date: 2010-12-11
forum: System76 Support
---

### Post by mjumbewu on 2010-12-11
I just bought a Lemur, and noticed that the fan runs a little loud.  After a little research, I found this resolved bug on launchpad from back in September of this year: [https://bugs.launchpad.net/system76/+bug/640842](https://bugs.launchpad.net/system76/+bug/640842).

I followed the steps successfully (I think) until step 5.  When I boot from my USB disk, I get a screen that says FreeDOS in the upper-left corner, followed by a blinking cursor.  That's it.  Pressing keys does nothing for me.  I have to reboot.

So, two questions:

1) If I just ordered m computer a couple weeks ago, would this bug (and the solution) still apply to me (i.e., is there any point in doing a bios upgrade, or is the bios already the latest version)?  FYI, the BIOS version on my machine is 1.00.05-sys.

2) Any ideas how to get past the FreeDOS screen?

Thanks,
Mjumbe

---

### Post by freechelmi on 2011-02-16
Hi dd you solved the fan noise problem ? I have the same problem with the same Board ( clevoS3101 ) and same Bios version

---

### Post by msrinath80 on 2011-02-16
I would not hang too much hope in any solution to this problem. I have the old Lemur (lemu1) and it has the same issue. Granted the fan kicks in and out automatically depending on the heat. But the noise is definitely present. I never heard it for the first 2 odd months of use. But since then I can hear it now almost everyday!

---

### Post by freechelmi on 2011-02-17
I've flashed the new EC firmware last night and it seems to make the fan problem almost disappear.

I've updated using a Freedos LiveUSB, worked perfectly. You don't need 2 USB sticks, just copy the firmware files at the root of the key and go C: under Freedos


However It seems to me it could be better but I can't find any clevo Bios updates for now.

---

