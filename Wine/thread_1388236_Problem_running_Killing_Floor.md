---
title: "Problem running Killing Floor"
date: 2010-01-22
forum: Wine
---

### Post by khaosfaktor on 2010-01-22
Apologies if this was posted earlier, but I searched and couldn't find anything helpful. I have Steam and Killing Floor installed, but whenever I try to run Killing Floor, I get this error message.

 Build UT2004_Build_[2004-11-11_10.48]

OS: Windows XP 5.1 (Build: 2600)
CPU: GenuineIntel PentiumPro-class processor @ 2095 MHz with 2047MB RAM
Video: NVIDIA GeForce3 (9371)

Error setting display mode: CheckDeviceFormat failed (D3DERR_NOTAVAILABLE). Please delete your KillingFloor.ini file if this error prevents you from starting the game.

History: UD3D9RenderDevice::UnSetRes <- DetermineFormats <- SetupPresentParms <- UD3D9RenderDevice::SetRes <- UWindowsViewport::TryRenderDevice <- UWindowsViewport::OpenWindow <- UGameEngine::Init <- InitEngine <- FMallocWindows::Free <- FMallocWindows::Free

I'm not sure what this means, and I'm still an Ubuntu newbie. I've tried deleting the KillingFloor.ini, its located in ~/.wine/drive_c/Program Files/Steam/steamapps/common/killingfloor/System, but it keeps reappearing every time I try to start Killing Floor back up. 

I'm running 9.10 (Karmic) and I've got Wine 1.1.36, and the AppDB said Killing Floor should work. Please help!

---

### Post by beastrace91 on 2010-01-22
Try an older Wine version - Last time I tried Killing Floor was under Wine 1.1.32

I'll update my version to 1.1.36 later this evening and see if I can reproduce your error - what nVidia drive version are you using and what graphics card do you have?

Regards,
~Jeff

---

### Post by khaosfaktor on 2010-01-22
My graphics card is an 
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
and I'm using NVIDIA GeForce GTX 295 drive.

---

### Post by Soulcage on 2010-01-23
Did you install the drivers? System > administration > hardware drivers.

---

### Post by beastrace91 on 2010-01-23
> **khaosfaktor said:**
> My graphics card is an 
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
and I'm using NVIDIA GeForce GTX 295 drive.

Wait... What? So you have two graphics card then? (in a laptop - because you are saying your intel chip is a mobile one). :confused:

~Jeff

---

