---
title: "Xserver 1.11.2 is released"
date: 2011-11-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-05
Those, who are using 1.11 series xserver might have noticed that there is a new release (1.11.2) available from Xorg-edgers PPA.
This is in the Oneiric branch, but it works very well with Precise too.

For people using xserver 1.10, upgrading to xserver 1.11 demands you to update all input and video drivers too. These are also available from Xorg-edgers.
So go ahead and break your X  :D .

---

### Post by VinDSL on 2011-11-06
> **Harry33 said:**
> So go ahead and break your X  :D .
You crystallized my thoughts exactly...  :D

---

### Post by dino99 on 2011-11-06
i've seen somewhere that ATI driver dont work with 1.11 yet

" Meanwhile the AMD Catalyst driver still doesn't support the X.Org Server 1.11 series, but it will later in the month. " [phoronix]

---

### Post by Harry33 on 2011-11-06
> **dino99 said:**
> i've seen somewhere that ATI driver dont work with 1.11 yet

" Meanwhile the AMD Catalyst driver still doesn't support the X.Org Server 1.11 series, but it will later in the month. " [phoronix]

Right, it will take time for AMD. Nvidia is already there.

---

### Post by Harry33 on 2011-11-09
And now the xserver 1.11.2 + git 20111109 is available from Xorg-edgers (precise branch) too.

---

### Post by Starks on 2011-11-09
Remember, 1.11 doesn't work with Unity yet because of the hard dependency on Unity.

---

### Post by Harry33 on 2011-11-10
> **Starks said:**
> Remember, 1.11 doesn't work with Unity yet because of the hard dependency on Unity.

That is the way it is now.
Anyway, no problem for me because I do not use nor have installed Unity.
I am using Gnome-shell (from Ricotz testing PPA)
and Xserver 1.11.2 (from Xorg-edgers).
With nvidia-current (290.06) these work pretty well now.

---

### Post by Starks on 2011-11-10
Meant to say "hard dependency on Utouch", but Unity works too.

---

### Post by Harry33 on 2011-11-10
> **Starks said:**
> Meant to say "hard dependency on Utouch", but Unity works too.

Perhaps you meant to say that in setups with xserver 1.11 series installed, Compiz segfaults when starting unity.
This is because xserver 1.11 does not have the multitouch support at the moment and Compiz needs to have it.


Se this bug (# 860707) report of Robert Hooker:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707)

---

### Post by rockorequin on 2011-11-19
Robert Hooker added a patched unity to xorg-edgers, so now unity doesn't crash if you're using the PPA.

Everything works fine on my intel system except for google-earth, which can't see glx so it asks if I want to switch to DirectX mode (!).

---

