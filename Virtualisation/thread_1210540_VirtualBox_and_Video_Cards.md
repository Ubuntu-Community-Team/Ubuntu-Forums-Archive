---
title: "VirtualBox and Video Cards"
date: 2009-07-11
forum: Virtualisation
---

### Post by razorboy5 on 2009-07-11
Hi

i'm running Ubuntu on my Laptop with ATI Radeon Graphics (512MB) so i set my video on my Windows XP guest for 128MB. However when i try to play a game on XP (which is recommended to have 64MB graphics) it will not run it.

I installed directX 9.0 and everything i dont see why it's not working

thx

---

### Post by Perryg on 2009-07-11
Kind of depends on the version of VBox that you are using.  Version 3.0.X has support for this but is so new (experimental) it has been known to have some problems.  I snipped this from the known limitations section of the VBox Users Guide.  Note the part about being in safe mode to install the Guest additions. Also there were problems using 128 meg of Vram and it is still suggested to use 64 Meg.

<snip>
Direct 3D support in Windows guests. For this to work, the Guest Additions must be installed in Windows "safe mode". Press F8 when the Windows guest is booting and select "Safe mode", then install the Guest Additions. Otherwise Windows' file protection mechanism will interfere with the replacement DLLs installed by VirtualBox and keep restoring the original Windows system DLLs.

---

