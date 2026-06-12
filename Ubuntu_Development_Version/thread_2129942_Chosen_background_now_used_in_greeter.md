---
title: "Chosen background now used in greeter"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by stinkeye on 2013-03-27
Just noticed my chosen desktop background is now used by the greeter,
and the transition from greeter to desktop is very smooth.
> VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Giga-byte Technology Device 351a
	Kernel driver in use: nouveau

---

### Post by mc4man on 2013-03-27
that was fixed about a week ago though it might not automatically take on an older install, see blue - 
> nautilus (1:3.6.3-0ubuntu11) raring; urgency=low

  * debian/patches/10_sync_background_to_accountsservice.patch:
    - write the background image to accountsservice [COLOR="#0000CD"]when it changes[/COLOR],
      gnome-settings-daemon was doing that but we stopped using that plugin
      to avoid duplication so we need to do it here

---

### Post by rburkartjo on 2013-03-27
yes and you can also choose any background image you have. and now i can use ubuntu tweak to set the greeter background image of my choice. never worked for me in 12.10.

---

