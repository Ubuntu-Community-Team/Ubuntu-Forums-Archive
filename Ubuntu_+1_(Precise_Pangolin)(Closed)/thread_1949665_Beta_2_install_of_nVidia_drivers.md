---
title: "Beta 2 install of nVidia drivers"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-03-30
I just downloaded and performed a fresh install of beta 2 amd64 on a system with nVidia GTS250 video card and two monitors, the second monitor being in portrait orientation. The installation defaults to activating the closed source proprietary nVidia driver, which presents two potential problems that I can see:

1. A user who opens System Settings / Monitors will find that it does not allow the second monitor to be configured, and there is no indication anywhere that the user needs to run nvidia-settings in order to achieve this.

2. The only way to have monitors in different orientations with the closed source driver is to configure them as separate X screens and then manually edit xorg.conf to add the necessary commands for rotation.

Neither of these problems exist when using the nouveau driver. After removing the nVidia driver through System Settings / Additional Drivers, configuring the resolution and orientation of both monitors is very simply performed from the System Settings / Monitors window.

Better I think to have the Nouveau driver as default when installing.

---

### Post by grahammechanical on 2012-03-30
I am curious about this. Last night I did a fresh 12.04 Beta 2 install and I was also surprised that it activated the Nvidia driver.

But then again, I do have few other installs of Ubuntu on my hard disk. so, I was wondering if the install process detected these other Ubuntus and worked out that the Nvidia driver was needed. Or did something else happen.

Do you have more than one copy of Ubuntu installed?

Regards.

---

### Post by Nick Payne on 2012-03-30
> **grahammechanical said:**
> I am curious about this. Last night I did a fresh 12.04 Beta 2 install and I was also surprised that it activated the Nvidia driver.

But then again, I do have few other installs of Ubuntu on my hard disk. so, I was wondering if the install process detected these other Ubuntus and worked out that the Nvidia driver was needed. Or did something else happen.

Do you have more than one copy of Ubuntu installed?

Yes, I already had 10.04 (using nVidia driver) and 12.04 beta 1 (using nouveau driver) installed on the machine when I ran the beta 2 installation.

I don't have a virgin machine on which I can try an install to see if it defaults to the nVidia driver in that situation (anyone?).

---

### Post by cariboo on 2012-03-30
When doing an install, if you marked the third party packages to be installed, you automagically get the closed source driver installed as a part of the process.

---

### Post by sgage on 2012-03-30
I did a fresh Beta 2 install this afternoon, and it came up nouveau. (32-bit Ubuntu, 8500GT nvidia graphics card).

---

### Post by Nick Payne on 2012-03-31
> **cariboo907 said:**
> When doing an install, if you marked the third party packages to be installed, you automagically get the closed source driver installed as a part of the process.
The message that comes up during the install is badly worded, then. My reading of it was that I was choosing whether to install some codecs, nothing more.

---

### Post by grahammechanical on 2012-03-31
> The message that comes up during the install is badly worded, then. I would agree with that. Although I do think that for many first time installers it will save a lot of trouble.

Regards.

---

