---
title: "shutdown freezes whole laptop"
date: 2016-03-28
forum: Ubuntu Development Version
---

### Post by pumo on 2016-03-28
just installed couple days ago beta 2 version of kubuntu. (I tried ubuntu gnome but it didnt work at all, that whole another thing :-) )

now everytime I shutdown my computer it freezes to kernel panic lookalike screen and computer stays on.
couple lines from hang:
"BUG: unable to handle kernel NULL pointer dereference
IP:  [ffff.....fae2] amdgpu_vm_grab_id+0x122/0x310 [amdgpu]

my laptop is Toshiba*Satellite S50B14M

model name      : Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
09:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev ff)

I dont even know which GPU Kubuntu uses..

---

### Post by pumo on 2016-04-11
My laptopr shutdown normally if charger is connected. without it allways kernel panic/freeze. even that I have updated almost daily.

---

### Post by Bucky Ball on 2016-04-11
Your battery could be shot. Is it holding charge the way it always has and charging to 100% as it should?

* Nope. Flipped right off. But I am using Xubuntu-core and a different lappy, so ...

---

### Post by pumo on 2016-04-12
Battery is fine, I have dual boot windows10 and it works like it should, so did ubuntu gnome 15.10.

---

### Post by Bucky Ball on 2016-04-12
Still update/upgrading? I'll give it a go on my laptop and see if I can replicate later this arvo.

---

### Post by pumo on 2016-04-12
I think I will test to install ubuntu gnome in weekend. last time (beta1) it didnt start at all. 
but first I will tonight test with live, will it shutdown.

---

### Post by pumo on 2016-04-14
that succesfull shutdown with charger connected was onetime "miracle", after that I havent got it working. I will install ubuntu gnome tomorrow hope it work if not I will go back to 15.10.

I forgot to mention that even rebooting computer goes kernel panic/freeze.

---

### Post by pumo on 2016-04-14
same thing happened with kubuntu live stick, shutting down ended kernel freeze.

---

### Post by pumo on 2016-04-15
solved, Kind of :)
I installed ubuntu gnome last nights daily. with that I cannot logon to desktop just blackcscreen and halt.
sometimes it did freeze like kubuntu. first I blacklisted fglrx and amdgpu it didnt help.
Then I downloaded 4.5.(040500) kernel and now I can logon to gnome and shutting down laptop also works.

edit: gnome with 4.5 kernel doesnt need that blacklisting amd stuff.

---

