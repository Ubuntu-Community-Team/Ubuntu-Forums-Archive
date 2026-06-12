---
title: "Ubuntu Xenial Error"
date: 2016-04-01
forum: Ubuntu Development Version
---

### Post by duran2 on 2016-04-01
Dear Ubuntu Community

I tried to run the latest version (Final Beta) of Ubuntu Xenial without installation. After a few seconds I arrived at an empty (Ubuntu colored) screen. After hitting ctrl+alt+del several times the task manager appeared, but was flickering (appearing/vanishing every second). I can enter login prompt with ctrl+alt+F1, but not more. 

My System: 

Windows 10 Home 64 bit
i7-6700K
Nvidia gtx 970

I attached two Images of the Error that appeared when i tried to poweroff the Computer. I also tried to upload a Gif of the flickering Screen, but I don't know if that works.

Tell me if you need more information to help me. Thank you for your support!

[ATTACH=CONFIG]268121[/ATTACH][ATTACH=CONFIG]268120[/ATTACH][ATTACH=CONFIG]268124[/ATTACH]

---

### Post by Bucky Ball on 2016-04-01
*Thread moved to **Ubuntu Development Version**.*

Not quite cooked yet. All posts regarding 16.04 LTS go here for the time being.

The error message in your first post tells it all by the looks. Have you tried researching that? 3D rendering. Software rendering rather than hardware? In the BIOS, have you got the internal graphics off and the PCI-E graphics on?

---

### Post by buzzingrobot on 2016-04-01
The first image, about "software rendering", happened because the GPU -- Nvidia card -- isn't being used to render 3d elements. That's the "hardware acceleration".  So, those requests are being routed through the CPU. This is much slower than using the GPU, and substantially increases the load on the CPU. 

Compiz is required for Unity, and it's failure is linked to that.

One likely cause is that the open source driver used by default in the installer and by Ubuntu -- called Nouveau -- doesn't fully support your video card. Many Nvidia cards are out there, sometimes altered a bit by individual card vendors.  Nvidia releases no source code, so open source drivers are essentially reverse-engineered affairs.  Support is typically weakest among newer cards, like the one you have.

There is  commonly used technique to boot the install ISO in "safe" mode that will avoid this problem.  This is usually done just long enough to install a proprietary driver from Nvidia.  These are not shipped with Ubuntu but are available in Ubuntu's repositories.  See the "If Your are trying to install Ubuntu..." section here:  [https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

If it works, it will result in a degraded but functional boot. Screen resolution and quality will be poor. Do the installation.  When it reboots, apply the same technique. Ubuntu should boot up in the degraded video mode.  Tap the Windows key and enter "Additional Drivers".  An icon with that label should display,  Click on it. The app's purpose is to list, and allow the installation of, the proprietary drivers maintained in Ubuntu's repositories. Allow it to display the drivers available for your Nvidia card. Select the one that is recommended. Click the button to do the install, and wait.  It may take several minutes or more to do the download and the processing involved in installing the driver. When the driver is installed, reboot and, fingers crossed, you should come into a nice display courtesy of that new proprietary driver from Nvidia.

Also remember that 16.04 is still in development, even if it's getting close to release day.

---

### Post by duran2 on 2016-04-02
Thank you all for the responses. Probably it's best if I wait until 16.04 is released and then try to install the correct NVIDIA driver in safe mode.

---

