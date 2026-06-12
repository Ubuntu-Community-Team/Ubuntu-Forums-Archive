---
title: "what drivers fgrlx or ati, should use?"
date: 2010-02-02
forum: Wine
---

### Post by Mana Whyrl on 2010-02-02
At last time, when i am upgrade 9.04 to 9.10, i have some problems with drivers, as a result some windows application don`t work correctly.

i`m in confusion. What drive should i use: ati or fglrx ?
ati drivers - just open source, cause Karmic has newest xorg. Ati don`t support it version.

I can`t run my GAMES(it`s _depend_ from driver).
but AGP(dxdiag->display) disable .... SO i can`t run for exp. CS 1.6 in OPENGL mode, just software(it`s terrible), can`t run LINEAGE ][ ...

and i think directX don`t work correctly, on ati drivers, but well on fglrx.

p.s. Now i use just ati. fglrx - purged.
pps. when i use fglrx, - noone application, by wine, can be launched.(even fglrxinfo, or gears)
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  152 (XFIXES)
  Minor opcode of failed request:  23 (XFixesSetCursorName)
  Serial number of failed request:  86
  Current serial number in output stream:  87
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012) - nothing from here help me.
ppps. sry for my bad engl.

---

### Post by alex.rayu on 2010-02-03
That depends on a video card. With most cards, 3d will not work well without fglrx.

---

### Post by Mana Whyrl on 2010-02-04
> **alex.rayu said:**
> That depends on a video card. With most cards, 3d will not work well without fglrx.
ok
**I just read [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)**
but in Prerequisites for installing[SIZE=2]:[/SIZE]
3. Identify whether your ATI graphics card model series is available on pages 2 or 3 of this pdf file.  
i cannt find my video card(x1650)

when i go to amd->drivers->linux x86->x1650([http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English")) they says:

The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Is it mean that, Karmic not supported? what i should do for playing(openGL)?

Thank you.

---

### Post by Melcar on 2010-02-04
Your card is no longer supported by the current driver.  You got two options:

- Move to Ubuntu 8.10 (I think 9.04 will work too) so you can install the "legacy" fglrx (9.3) which does support your card.  The card will now have full OpenGL hardware acceleration.

- Use the open source drivers (radeon or radeonhd, out of which radeon is better) and stay on Ubuntu 9.10.  Your card will still function but you will be limited to OpenGL1.5 hardware acceleration, which means that many 3D apps. may not work (some games with WINE for example).

---

### Post by Mana Whyrl on 2010-02-04
I guess that the answer will be like that...
Thanks a lot.
I think I would use second.
ps. btw. ati drivers support u904.

---

