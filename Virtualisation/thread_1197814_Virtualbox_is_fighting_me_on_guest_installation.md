---
title: "Virtualbox is fighting me on guest installation"
date: 2009-06-26
forum: Virtualisation
---

### Post by factotum218 on 2009-06-26
I began with Ubuntu 9.04 last week. Overall it's a pretty solid system. All of the hardware on my laptop was up and working without any problems. I did, however, have a problem with running a virtual system inside of it. It would lock up during the guest install. No matter what I did. Some information I've found points to the BIOS having been limited to exclude the support for AMD's virtual system. This was done probably by an OEM before I got the computer. But I question that because I did have virtualbox up and running before in 9.04 beta. Wierd.

I checked out what Pheonix Systems had to offer for BIOS upgrades. They offered a piece of software to help automate the task of checking for updates and installing them for a $29.95 annual fee. I feel like I stepped in dog crap.

As much as I want to get Linux running full time on my computer there are still issues that need to be either fixed or circumvented. Anything released including version Xorg verions below 1.6.x are a no go with my graphics card. It's an ATI Radeon Mobility 3650 HD. I've heard rumors of pulling out up to 2GB of RAM will somehow allow the card to function properly. This was in the beta stage of Ubunutu's 9.04 release and now have support for the card, if a bit buggy.

I've considered openSUSE and Debian Stretch (testing) as alternatives, but I feel that the Virtualbox issue is still going to be the deciding factor in the consideration of a switch. I've tried disabling the AMD V support only to have the XP installation freeze up during the hardware setup section of the installation, marked at 34 minutes remaining. Really puts a kink in the hose not having InDesign and Fireworks available. I work at a newspaper and deal with updating their website (without a CMS) from the InDesign layout. It's pure genius, they wait until the pages are laid out before proof reading them, making the .doc files of the original articles useless for me.

Dual booting is too much of a pain for me now. I do all the web work in Linux with the server available right in Nautilus, I use an editor not available in Windows, and I can't see crawling through mud on a Vista installation for the sake of keeping InDesign available. All I need is a XP virtual machine to grab at every once in a while.

I'm looking for some ideas. Should I consider the kernel or the version of Virtualbox as the culprit? Or the BIOS?

---

### Post by bodhi.zazen on 2009-06-26
1. Probably not your bios.

2. I would enable virtualization in your bios.

3. I also advise you install the PUEL edition, the one you download from the sun site, seems to have less problems.

4. Last I suggest less ranting and a better description of your problem. We understand you are frustrated, but come to the point, describe the problem, and skip long ranting.

---

### Post by factotum218 on 2009-06-26
I wasn't ranting, that would instil anger. Just describing the situation.

As far as enabling AMD V I would, but there is no setting available. The BIOS is by Phoenix the laptop is an Acer 6530.

Hardy x64 

My copy of Virtualbox is fresh from java, 2.6.28-13-generic SMP x86_64 kernel on 9.04.

AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-82

I checked the vbox-install.log, nothing odd


**From syslog:**
slowpoke kernel: [   15.076855] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Jun 26 00:23:15 slowpoke kernel: [   15.076859] vboxdrv: Successfully done.
Jun 26 00:23:15 slowpoke kernel: [   15.076861] vboxdrv: Found 2 processor cores.
Jun 26 00:23:15 slowpoke kernel: [   15.076925] VBoxDrv: dbg - g_abExecMemory=ffffffffa0332f00
Jun 26 00:23:15 slowpoke kernel: [   15.076978] vboxdrv: fAsync=1 offMin=0x64041e8 offMax=0x64041e8
Jun 26 00:23:15 slowpoke kernel: [   15.077067] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Jun 26 00:23:15 slowpoke kernel: [   15.077069] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
Jun 26 00:23:15 slowpoke kernel: [   15.286021] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa04d2bc0

---

### Post by sdowney717 on 2009-06-29
could your OS install disk be the problem?

have you tried vmware server?

so far I have discovered virtualbox has poor networking dropped packets
vmware has good networking but usb does not work.

---

