---
title: "Intel / NVIDIA Dual Graphics on HP Envy 34&quot; All-in-one"
date: 2022-08-06
forum: Ubuntu/Debian BASED
---

### Post by nodrog2 on 2022-08-06
I've been trying to get  few Ubuntu flavors working  on my new HP Envy 34" All-in-one PC

The problem  I am experiencing with with the dual Graphics cards:

Graphics (integrated):Intel® UHD Graphics 750
Graphics (discrete):NVIDIA® GeForce RTX&#8482; 3060 (6 GB GDDR6 dedicated)

Although I am able to install the Proprietary Nvidia drivers there are a few issues:


[LIST=1]
[*]The system sees the large 34" screen as two separate displays of 2560 x 2160 instead of a single 5120 x 2160 display. Although when in Graphics Safe Mode it did see it as a single 5210 x 2160 display. 
[*]There is occasional flickering on the screen when first logging in which seems to go after a few minutes. 
[/LIST]

Switching to intel / nvidia / ondemand using prime seems to make no difference.
I've tried a few distros with no luck.
the attached screenshot is from my single 34" screen and shows how it is split into two displays.
The latest distro I tried was KDE NEON running on 20.04 LTS :
[FONT=monospace][COLOR=#000000]Linux hpenvy34 5.15.0-43-generic #46~20.04.1-Ubuntu SMP Thu Jul 14 15:20:17 UTC 2022 x86_64 x86_64 x86_64 GNU[/COLOR]
/Linux

Has anyone had any success with getting Ubuntu working well on this lovely bit of hardware?
Any suggestions on troubleshooting the graphics issues?

Thanks

[/FONT]

---

### Post by Yellow Pasque on 2022-08-09
Those screenshots are way too small to read. Take a screenshot of the active window instead of the whole desktop.

> **nodrog2 said:**
> Switching to intel / nvidia / ondemand using prime seems to make no difference.

Prime is for laptops where the GPU's are connected together. You don't have a Prime configuration.

---

### Post by pmils on 2022-12-30
[COLOR=#000000][FONT=Arial]I've got a very similar problem my new HP Envy 34" All-in-one PC while the HW configuration is a bit different:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Graphics (integrated): Intel(R) UHD Graphics 730[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Graphics (discrete): NVIDIA GeForce GTX 1650[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Before trying installing Kubuntu 20.10, I tried first to deploy on VMWARE above Windows 11 and it seemed to work perfectly fine.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The issue started when trying installing as a dual boot.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Did you make any progress on understanding what is the issue?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by cynthia007 on 2023-06-23
Hi Darlings...it has been almost a year for this issue with no response...is the resolution (see what I did there?) somewhere else, can you kindly direct me to it?  It is very difficult to believe the Ubuntu flavors _can not work with a 34/5K AIO screen_. I have the exact issue as Nodrog2 down to the same specs and refurbs and have**_ tried _almost everything under the sun to get it to work **and absolutely nothing has been successful and with no answer to this here are we saying nothing can? The Grub menu recognizes the 5120x2160 (yes not full on 5K) screen and as ND2 mentioned in safe (recovery) mode (where I am typing now) it is recognized and not divided into two screens. I am not greedy  - looking for the monitor to work as well, but at least if the main display does, we can move on from there. Ubuntu literally got me through some very rough times and though in certain aspects I consider myself to be a noob (is that still used?), I have been using one flavor or another for many, many years and really do not want to abandon it. I am fine with Windows for work, but the thought of using it at home, causes me to break out in hives. LinuxFX causes ghostly images and my favorites Deepin and UbuntuDDE (the most beautiful Linux OS' in the world, btw) produces the dual screens that ND2 reported.

---

### Post by him610 on 2023-06-24
> ....dual Graphics cards:
Graphics (integrated):Intel® UHD Graphics 750
Graphics (discrete):NVIDIA® GeForce RTX™ 3060
Not dual GFX, but two separate GFX processors.
Which do you prefer to use? Integrated or discrete?

In olden times, one could choose in the BIOS setup which GFX chip had priority. 
Nowadays with the advancement (?) in chips and processes, can one still choose in EUVE setup which GFX chip has priority?
Review your Motherboard manual to see if it is possible, and choose one.

---

### Post by cynthia007 on 2023-06-25
Many thanks for your response and suggestion, I will give it a go and only come back if it does (yes does) work. As anything else could be viewed as targeting you specifically for help (you know no good deed goes unpunished;) )

---

### Post by cynthia007 on 2023-06-26
How so very helpful as now (a bit late) I understand for the multiple displays because there are two GPU's!  Unfortunately HP locks the Advance Options in the BIOS so such a change as 'picking one' is not possible.   Is the only option now left removing out one of them....That seems a bit violent for such a beautiful unit.  If anyone is aware of a workaround, let me know! Thanks again!

---

