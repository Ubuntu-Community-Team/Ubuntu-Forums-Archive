---
title: "Problem with Unity Greeter"
date: 2013-03-24
forum: Ubuntu Development Version
---

### Post by SkylineGTR on 2013-03-24
Hi

I recently installed RR, but many times when starting my laptop I hear the ubuntu sound but can't see Unity Greeter, just a black screen.
After some reboots I finally can see it..

Anyone knows what could be the problem?

Thanks.

---

### Post by SkylineGTR on 2013-03-25
Am I the only one having this problem?

Basically what happens is that when I boot my laptop I hear ubuntu but can't see the login interface, just a black screen.
After some reboots eventually Ubuntu Greeter is loaded, but it's very annoying..

---

### Post by dino99 on 2013-03-25
i suppose its time you glance closet at your logs and/or use dconf to adjust the settings, specially those not set to default

dconf-tools is needed of course

---

### Post by grahammechanical on 2013-03-25
Questions

1) Did you install from an daily ISO image or upgrade?
2) Did you run a live session first? Any issues with the live session?
3) Did you need to use any of the F6 options to get the live session working or to get the installer working?
4) Did you install with the box for install third party software ticked? That will give you a proprietary video driver which is not used in a live session.
5) Have you tried any of the Recovery Mode options. Recovery>Resume or Recovery>FailsafeX may get you to a desktop. From there you can go to System Settings>Software & Updates>Additional Drivers tab. From there you can experiment with different video drivers.

Based upon my experience in testing several Raing ISO images over the past few months I would suggest to never install third party software during the installation. I always get to a desktop on reboot with the Noveau driver. But not always with a proprietary driver. I install third party software after installation and I may even try (as an experiment) a proprietary video driver.

Regards & welcome to testing.

---

### Post by SkylineGTR on 2013-03-25
> **grahammechanical said:**
> Questions

1) Did you install from an daily ISO image or upgrade?
2) Did you run a live session first? Any issues with the live session?
3) Did you need to use any of the F6 options to get the live session working or to get the installer working?
4) Did you install with the box for install third party software ticked? That will give you a proprietary video driver which is not used in a live session.
5) Have you tried any of the Recovery Mode options. Recovery>Resume or Recovery>FailsafeX may get you to a desktop. From there you can go to System Settings>Software & Updates>Additional Drivers tab. From there you can experiment with different video drivers.

Based upon my experience in testing several Raing ISO images over the past few months I would suggest to never install third party software during the installation. I always get to a desktop on reboot with the Noveau driver. But not always with a proprietary driver. I install third party software after installation and I may even try (as an experiment) a proprietary video driver.

Regards & welcome to testing.

1) Daily ISO image, a few days ago.
2) No. I went straight to install.
3) N/A
4) No. I never check the "third party software" checkbox.
5) Haven't tried that yet.

I have a laptop with integrated Intel HD4000 and NVIDIA GT650. I suppose that most of the time it's using the Intel graphic card, right? Is there any driver I should try for the Intel graphic card?

---

### Post by SkylineGTR on 2013-03-26
Apparently the problem was with the latest kernels:

3.8.0-13
3.8.0-14

I've installed kernel 3.9 RC4 and everything is working great.
Zero problems, and boots very fast.

---

