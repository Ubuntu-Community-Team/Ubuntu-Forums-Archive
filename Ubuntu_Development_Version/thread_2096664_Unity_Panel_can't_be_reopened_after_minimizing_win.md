---
title: "Unity Panel can't be reopened after minimizing windows"
date: 2012-12-20
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-12-20
Unity panel is busted. When minimizing a window to panel they cannot be reopened. Logout or reboot required.

---

### Post by fjgaude on 2012-12-20
> **ventrical said:**
> Unity panel is busted. When minimizing a window to panel they cannot be reopened. Logout or reboot required.

I can't get what you describe. My setup works just fine, 3.7.0-7 kernel. Unity, fast, fast.

Observing how the windows open and close, lots of details, what you experience is likely a non-Intel graphics thing.

---

### Post by ventrical on 2012-12-20
> **fjgaude said:**
> I can't get what you describe. My setup works just fine, 3.7.0-7 kernel. Unity, fast, fast.

Observing how the windows open and close, lots of details, what you experience is likely a non-Intel graphics thing.


 This activity taking place on nvidia adpater Gforce 210/218 with nvidia-current.

---

### Post by rrnbtter on 2012-12-20
Greetings,
Windows are working fine on 3.7.0-7 on a Intel GM45 chipset. The only problem I am having is my shutdown link logs out instead of shutdown. Currently using a shutdown bash script. This started with Tuesday's updates. Actually with the install of the current kernel. And I agree with the fast, fast, fast.

---

### Post by ventrical on 2012-12-21
There is a new feature when you minimize windows to panel. There is this sort of wavy-pan of the icon. Actually a nice little effect (eyecandy of course). For some reason it has locked up on machine testing nvidia-current.

---

### Post by ventrical on 2012-12-21
I removed nvidia-current and installed nouveau-firmware, but, to no avail.

---

### Post by ventrical on 2012-12-21
Here is the link to the bug I filed.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1092884](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1092884)

---

### Post by ventrical on 2012-12-21
I logged off and then logged on to another account on the same install and the Unity Panel/launcher works perfectly. I suspect then a compiz problem.
Edit:
I made an addendum to the bug.

---

