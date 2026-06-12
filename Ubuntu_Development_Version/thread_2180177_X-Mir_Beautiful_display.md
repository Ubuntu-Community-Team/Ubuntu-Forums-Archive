---
title: "X-Mir: Beautiful display"
date: 2013-10-11
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2013-10-11
Greetings,
I have been getting heavy updates for the last few days. After today's updates I now have the most beautiful desktop, webpages, etc I have ever seen.  And I'm getting this on a three year old Toshiba Laptop. If this is what Mir is coming to I'm all for it. Using Intel Mobile 4 chipset and running Ubuntu Unity with X-Mir.

---

### Post by grahammechanical on 2013-10-12
I stopped using Xmir but not because of problems. I wanted to test an ISO that installed Xmir by default. But that is now not going to happen until some time during the next development cycle. I am reviewing my plans for the next cycle. I will consider going back on to Xmir. I like to have an install where development happens naturally as well as installs where I test stuff through PPAs.

I, also thought that Xmir was working pretty well. I am looking forward to get bits and pieces of full Mir over the next six months. My machine dates back to 2007.

---

### Post by ventrical on 2013-10-13
I have to give credit to the developers who are writing the open source drivers for Intel Graphics hardware. I have Mir (unity-system-compositor) working on machines all the way back to 2003. On the newer nVidia cards also. 

a big +1! :)

One thing though .. when it borks out on an older card it really borks out ! :)

---

### Post by sammiev on 2013-10-13
I never noticed any difference using X-Mir with Intel Graphics hardware. Can also say I have no problems using it as well.

---

### Post by Baldrick_NZ on 2013-10-13
> **rrnbtter said:**
> Greetings,
I have been getting heavy updates for the last few days. After today's updates I now have the most beautiful desktop, webpages, etc I have ever seen.  And I'm getting this on a three year old Toshiba Laptop. If this is what Mir is coming to I'm all for it. Using Intel Mobile 4 chipset and running Ubuntu Unity with X-Mir.

Screenshots?

---

### Post by miguelpires on 2013-10-14
HI,
Anyone using Mir/Xmir with an Optimus Nvidea? 
I've an Laptop with Optimus tecnology, soo if is possible i don't mind to try Mir
Regards
Miguel

---

### Post by VMC on 2013-10-14
I tried it on a "**[nvidia 6150SE nforce 430]("https://wiki.ubuntu.com/Mir/GPUTesting")**", and it was gawd-awful.

---

### Post by mc4man on 2013-10-14
> **miguelpires said:**
> HI,
Anyone using Mir/Xmir with an Optimus Nvidea? 
I've an Laptop with Optimus tecnology, soo if is possible i don't mind to try Mir
Regards
Miguel

Well here I'm running 13.10 with a nvidia 660m gtx so by default it uses intel (4000
Overall the intel  works just fine, no real need for nvidia side unless I was playing games (not often, have win 7 anyway) or had some real high bitrate video

As far as the intel driver have installed libvdpau-va-gl1 so I get gpu vdpau decoding with mplayer with intel & also flash hardware (gpu) decoding with intel.
Bumblebee brings nothing to the table for me as it doesn't support video decoding & nvidia-primus just boots  to low graphics so for the moment will stick with intel in linux with this laptop.

As far as xmir - doesn't offer anything atm, the only reason to have installed in 13.10 is to see if it regresses anything. With intel 4000  it doesn't  other than an acknowledged  10% performance hit, with many nvidia cards it does regress when using nouveau.
(- the title of this thread doesn't make much sense

---

### Post by Mateusz Stachowski on 2013-10-15
XMir so far doesn't bring any advantages over Xorg and in fact it causes a regressions. I've been testing it for a couple of months in daily current live mode and using the Xubuntu 13.10 [testing]("http://vanir.unit193.tk/mir/") images (BTW they still get updates).

XMir uses a software cursor because the developers had problems with enabling hardware cursor of Xorg (it collides with Mir cursor). Apparently the software cursor is buggy and for example you will see graphic corruption in [maps]("https://bugs.launchpad.net/xmir/+bug/1211060") and [games]("https://bugs.launchpad.net/xmir/+bug/1216708"). The developers think that it's restricted to Nouveau but I think that it happens for all drivers. See the first [bug]("https://bugs.launchpad.net/xmir/+bug/1211060") which has reports from people using Intel and Radeon.

For users of Nouveau there is also screen [tearing on XMir]("https://bugs.launchpad.net/mir/+bug/1195811") which doesn't exist in Unity running on Xorg.

If they resolve that two bugs that will bring XMir experience on my GeForce 9600 GT to the level of Xorg.

---

### Post by gspe on 2013-10-15
> **Mateusz Stachowski said:**
> XMir so far doesn't bring any advantages over Xorg and in fact it causes a regressions. I've been testing it for a couple of months in daily current live mode and using the Xubuntu 13.10 [testing]("http://vanir.unit193.tk/mir/") images (BTW they still get updates).

XMir uses a software cursor because the developers had problems with enabling hardware cursor of Xorg (it collides with Mir cursor). Apparently the software cursor is buggy and for example you will see graphic corruption in [maps]("https://bugs.launchpad.net/xmir/+bug/1211060") and [games]("https://bugs.launchpad.net/xmir/+bug/1216708"). The developers think that it's restricted to Nouveau but I think that it happens for all drivers. See the first [bug]("https://bugs.launchpad.net/xmir/+bug/1211060") which has reports from people using Intel and Radeon.




Finally i understand why Java Apps, (likes eclipse, JetBrains IntelliJ, Scilab, etc...) doesn't works with Xmir.

---

