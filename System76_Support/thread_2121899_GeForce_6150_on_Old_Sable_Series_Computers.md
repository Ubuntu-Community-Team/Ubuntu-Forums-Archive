---
title: "GeForce 6150 on Old Sable Series Computers"
date: 2013-03-03
forum: System76 Support
---

### Post by jvslice on 2013-03-03
I have 2 old Sable Series computers (sabv2) which were bought back in 2007 and have Nvidia GeForce 6150 cards.  With Ubuntu 12.04 installed on the system it used 2D not using the Nvidia drivers, i think it was backlisted but i may be wrong.  After Ungrading to 12.11 the system is slow so now I am using XUBUNTU and thing are better but still not great but i would really love to use Ubuntu since that is the way it appears to be going for Desktops, Phones, etc.  Any help on what I should do to use the power of the old Nvidia graphic card.

thanks

---

### Post by isantop on 2013-03-04
Which driver are you using for your Nvidia card? You can find out by checking in System Settings > Software Sources > Additional Drivers tab.

---

### Post by jvslice on 2013-03-04
Nvidia Corp C51PV (GeForce 6150)

The selected driver is the top selection labeled Using Nvidia binary Xorg driver, kernel module and VDPAU library from Nvidia-current (proprietary, tested)

---

### Post by isantop on 2013-03-07
I really couldn't say for sure what would be causing that. Are you sure the issue is graphics? When does the computer feel slow, or slowest?

---

### Post by jvslice on 2013-03-09
I guess the computers are slow or sluggish when I am using the Ubuntu-desktop (Unity) and i get much better performance using XUBUNTU.  The thing that started the origional post was initially when running Ubuntu 12.04 (Unity) the only way to run Unity was with 2D even though 3D was available.  I had heard or though that I heard or read somewhere that the older NVIDIA cards were blacklisted and after 2D went away in 12.10 a software implementation would be used in Unity for older cards.  This caused me to write thie initial question about which driver I should use, I should have been more specific on my question.  Aditionally if Unity has black listed my older card i guess I am stuck with a lighter desktop which raises an aditional question, NVIDIA driver or Nouveau for my older Sable computer?

---

### Post by isantop on 2013-03-11
If the Nvidia driver supports your card, then definitely go with that. It's much faster than the standard driver for most cards.

---

### Post by jvslice on 2013-03-11
Thannk you for the information, I will be sticking with XUBUNTU for now and consider the post closed.

---

