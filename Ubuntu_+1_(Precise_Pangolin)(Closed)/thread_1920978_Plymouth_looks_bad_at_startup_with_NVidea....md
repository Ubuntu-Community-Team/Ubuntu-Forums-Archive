---
title: "Plymouth looks bad at startup with NVidea..."
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by exploder on 2012-02-05
Plymouth looks pretty bad on startup with a NVidea GT-220 graphics card, it looks fine on shutdown. I am using the open source drivers right now. I tried the proprietary drivers but got the huge ugly text and the open source drivers seem to work alright for the most part.

Plymouth is just displaying a purple screen and get some lines with green on the top of the screen just before the greeter comes up.

Does anyone have any suggestions on this? I would even use the proprietary drivers if there is a fix for plymouth.

---

### Post by mc4man on 2012-02-05
The plymouth boot splash with nvidia looks fine here for the 2 sec's it shows, the splash with nouveau has been broken since 11.10 & lasts longer.

The last thing I'd do is base driver choice on plymouth which as far as the splash has been a complete flop

I would  prefer karmic's splash any time over the plymouth splash nonsense

---

### Post by exploder on 2012-02-05
Thanks for the information about plymouth and the nouveau driver. I installed the pre-release nvidea driver and used startup manager. The screen artifacts on boot are gone. Plymouth now displays a purple screen and then goes to black before the greeter shows, it's not perfect but considerably better. I appreciate the information you gave me. The proprietary driver is much better than nouveau.

---

### Post by effenberg0x0 on 2012-02-05
As ridiculous as it may sound, until a couple weeks ago I had never even seen Plymouth in its full glory (Ubuntu logo, the dots, etc) in any real hardware, just on VMs. I got to see it for the first time on Intel hardware. Nvidia (proprietary) has always been the same and still is: Pink screen with random black lines or black squares. Very beautiful.

---

### Post by dino99 on 2012-02-06
My experience is worst with 290.10 & 8500gt here on Precise i386:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/919928](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/919928)

if plymouth could be completly purged i beleive we got less issues ( agree that plymouth is a non sense)

---

### Post by lucazade on 2012-02-06
I would purge plymouth as well but we need a better resolution detect via grub.
At the moment VBE resolution is poor, should be improved, and thanks to vt.handoff=7 the framebuffer is displayed until X loads up, without flickering and logging verbosity.

---

### Post by dino99 on 2012-02-06
Do i need to add vt.handoff=7 to grub ?

---

### Post by lucazade on 2012-02-06
@Dino
It is enabled by default and it works smoothly with opensource drivers (intel, radeon and nouveau) that use KMS. When using proprietary drivers, instead, vt.handoff doens't work good because it is killed at the beginnig by plymouth and afterward by X, showing also a lot of junk messages by kernel and system services. A disaster :)

Also vbe has some issue to detect resolution if the monitor has a broken EDID and sometimes also if the DVI/HDMI cable is not compilant (like in my case with a 23'' LCD Samsung).

So I would invest some developing on Grub.

---

### Post by dino99 on 2012-02-06
Clear explanation, thanks :)

---

### Post by awam66 on 2012-02-06
Ever since maverick I have had a completely blank screen on my Dell C250 64bit system. Noything ever shows after grub and even a disk check doesn't show or pressing "C" when I guess it is doing a check does nothing. Eventually I get the desktop (auto login). Have searched for ages but can't find a solution. Any ideas?

Edit: I should have said I've tried both the Nvidea drivers and Nouveau but it makes no difference!

---

### Post by effenberg0x0 on 2012-02-06
We talked a lot about Plymouth in Oneiric cycle, there were reports, etc. Nothing changed and I guess we gave up complaining. It will still look like this for the LTS which is a pity.

Regarding the interesting points raised by Lucazade, there seems to be a fix to allow for proper Plymouth when on proprietary drivers. It is visually implemented by super-boot-manager. I don't use it, but know of people that have successfully used it.

Regards,
Effenberg

---

### Post by coffeecat on 2012-02-06
It sounds as though it's a ymmv according to which particular nvidia video card you have. On my laptop with GeForce 410M + proprietary driver (repo nvidia-current) I get the big ugly version of the Ubuntu + dots on bootup and shutdown but not the psychedelic effects - that's fully up-to-date as of now.

My test rig has an old(ish) Geforce 8400GS card and last time I used it with 12.04 I was getting an undistorted Plymouth splash with the nvidia driver - which surprised me. That was a couple of weeks ago though - PP is proving to be so stable that I'm now using it as my main system on my laptop, and I've put the test rig away.

---

### Post by xyzzyman on 2012-02-06
I use: [http://www.plymouth-themes.org/earth-sunrise](http://www.plymouth-themes.org/earth-sunrise)

With a 9600M GS and the nvidia binary driver. Runs in just 640x480x32 but I haven't attempted to increase it.

---

### Post by philinux on 2012-02-06
Plymouth + nVidia on my 8600GT has always produced this.

Stage 1 = Blank aubergine screen for most of the boot time.

Stage 2 = Logo with animated dots appears for a couple seconds.

Stage 3 = Black screen flicker flash

Stage 4 = Login window appears.

Awful I reckon. I hope plymouth gets replaced with something much better very soon. I'd rather just see the boot text at the moment.

---

### Post by effenberg0x0 on 2012-02-06
> **philinux said:**
> [...]
 I hope plymouth gets replaced with something much better very soon. I'd rather just see the boot text at the moment.

Me too, but I am unaware of any move towards replacing it. Ubuntu apparently consider it to be a working and ideal solution (I never found information stating otherwise). In the last cycle we searched and found a couple potential replacements, but nothing mature and actively maintained. 

I had tried to study it in OO cycle, and verified that its own developers consider it to be incomplete, there's no proper documentation, customization options are flaky and the code itself is full of tweaks and workarounds. I guess it's one of those situations in which there's no real alternative.

Regards,
Effenberg

---

### Post by dino99 on 2012-02-06
Plymouth have been made to hide the verbose boot mode (like dust under the carpet).
No one needs something complicated nor dynamic like the colored dots during so early boot time. A static background or ubuntu logo should be enough and be easier to implement i suppose, with a small footprint memory not disturbing the video process.

An oyher solution is to simply redirect the verbose mode to >>null instead of the screen

---

### Post by bluenova on 2012-02-06
My GeForce 8600 GT (proprietary drivers) has always had the ugly in plymouth until Oneiric, with Oneiric I get a good looking bootup to login screen.

---

### Post by lucazade on 2012-02-06
> **dino99 said:**
> Plymouth have been made to hide the verbose boot mode (like dust under the carpet).
No one needs something complicated nor dynamic like the colored dots during so early boot time. A static background or ubuntu logo should be enough and be easier to implement i suppose, with a small footprint memory not disturbing the video process.

An oyher solution is to simply redirect the verbose mode to >>null instead of the screen

this is why I'd like only the vt.handoff option and no plymouth at all..
grub can display a hires picture for both entries menu and for post boot untill X comes up.

A static image like plymouth but without relying on KMS feature that is not available with proprietary drivers
and without swithing between consoles, ttys, plymouth. A flickerless startup.

---

### Post by BigSilly on 2012-02-06
> **philinux said:**
> Plymouth + nVidia on my 8600GT has always produced this.

Stage 1 = Blank aubergine screen for most of the boot time.

Stage 2 = Logo with animated dots appears for a couple seconds.

Stage 3 = Black screen flicker flash

Stage 4 = Login window appears.

Awful I reckon. I hope plymouth gets replaced with something much better very soon. I'd rather just see the boot text at the moment.

Same for me except - stage 2 = Logo with animated dots for a couple of seconds, at a really low resolution. Something like 640 x 480. Spec below. It's been like this for me since Plymouth was introduced in, what, 9.10? Something like that.

For me it's only marginally better than having a load of text rushing past during the boot process. I'd really hoped they might have fixed Plymouth up a bit for 12.04 for us proprietary driver users, but I suspect that this is just one of those things that isn't ever going to improve any. :(

---

### Post by effenberg0x0 on 2012-02-06
I can understand how hiding 5 seconds (at most) of console messages can be of some use to OEMs (that may prefer to put their log in there - although they already do that via BIOS if they want to). I just can't see a high-enough cost-benefit ratio for the end-user to justify the potential problems it causes.

We're talking about DRM access, developing and managing KMS drivers for every card brand out there, deploying a framebuffer as a workaround when no KMS is available (no distro does that automatically, so, broken plymouth screens are common), redirecting kernel standard print call, parsing any potential init message, ensure they aren't lost before they are dumped to logs, etc.

And all that as a way to provide **less** information to users. How many times, when helping a user with a crashed/stale boot  we have to ask them to disable Plymouth so we can get a lead on what's going on?

I'm sorry, I just never could really get it - it's not useful or good to end-users in any way IMO. And if hiding useful info from users just to show a 2 second logo (at the risk of creating system and low-level failures and crashes besides a garbled screen in many users systems) is really the goal, there has to be a better, easier, less intrusive way to do it.

Regards,
Effenberg

---

### Post by Harry33 on 2012-02-06
> **dino99 said:**
> My experience is worst with 290.10 & 8500gt here on Precise i386:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/919928](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/919928)

if plymouth could be completly purged i beleive we got less issues ( agree that plymouth is a non sense)

Well because of the dependencies of mountall, it is not possible.
However, you will get rid of it just by purging packages:
- plymouth-label
- plymouth-theme
- plymouth- x11

After that Plymouth will not bother you again. But file system checking (fsck) works.

I keep this line in my /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by BigSilly on 2012-02-06
> **effenberg0x0 said:**
> I can understand how hiding 5 seconds (at most) of console messages can be of some use to OEMs (that may prefer to put their log in there - although they already do that via BIOS if they want to). I just can't see a high-enough cost-benefit ratio for the end-user to justify the potential problems it causes.

We're talking about DRM access, developing and managing KMS drivers for every card brand out there, deploying a framebuffer as a workaround when no KMS is available (no distro does that automatically, so, broken plymouth screens are common), redirecting kernel standard print call, parsing any potential init message, ensure they aren't lost before they are dumped to logs, etc.

And all that as a way to provide **less** information to users. How many times, when helping a user with a crashed/stale boot  we have to ask them to disable Plymouth so we can get a lead on what's going on?

I'm sorry, I just never could really get it - it's not useful or good to end-users in any way IMO. And if hiding useful info from users just to show a 2 second logo (at the risk of creating system and low-level failures and crashes besides a garbled screen in many users systems) is really the goal, there has to be a better, easier, less intrusive way to do it.

Regards,
Effenberg

I'm currently using openSUSE (12.1) which hasn't switched to Plymouth yet, and the odd thing is that it looks so much better than Plymouth. It boots up just as quick, has something approaching my native resolution, and looks much better. And if I need to see any boot messages, I just have to press ESC as it's booting. Generally it's much less hassle than using Plymouth, and could still be a viable option, no?

---

### Post by effenberg0x0 on 2012-02-06
> **BigSilly said:**
> I'm currently using openSUSE (12.1) which hasn't switched to Plymouth yet, and the odd thing is that it looks so much better than Plymouth. It boots up just as quick, has something approaching my native resolution, and looks much better. And if I need to see any boot messages, I just have to press ESC as it's booting. Generally it's much less hassle than using Plymouth, and could still be a viable option, no?

Thank you for the info. I have been working exclusively with Ubuntu for the past years and shamefully am not familiar with other distros. I'll download it and give it a try in a VM as soon as I can find the time to check what is the bootsplash solution implemented by them.

Regards,
Effenberg

---

### Post by Yellow Pasque on 2012-02-06
I maintain a ppa with modified mountall (and cryptsetup) that don't depend on plymouth, so it can be removed completely: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

I'm a bit behind on the precise version of mountall right now because I can't access my Precise VM at the moment (until qemu-kvm packaging gets fixed in Debian sid).

---

### Post by Bobhuber on 2012-02-06
This will fix it and still works for 11.10.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by effenberg0x0 on 2012-02-06
> **Bobhuber said:**
> This will fix it and still works for 11.10.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Yes, the framebuffer alternative already mentioned in this thread. But for me, ideally, it would be nice to not have plymouth, not have a bootsplash, not have a framebuffer. Simply boot as fast as possible.

@Temüjin
I had tested your PPA in Oneiric cycle and was looking for it again. Hope you manage to update it soon :) Thank you for your work!

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-02-06
@all

What would be the Ubuntu procedure to suggest (and hopefully get approval) for Temujin's work as a /etc/alternatives/bootsplash like:
[0] (Default) Plymouth
[1] No Bootsplash

?

Regards,
Effenberg

---

### Post by cariboo on 2012-02-06
So again I'm disappointed that Plymouth works for me on both my netbook, and my desktop system. My desktop system uses a GeForce 210 [noparse](GT218)[/noparse] and the Nvidia 290.10 driver, and my netbook is using the Intel 945 chipset with the i915 driver.

---

### Post by xyzzyman on 2012-02-06
> **Bobhuber said:**
> This will fix it and still works for 11.10.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Thanks for the link. Had to also remove vt7 handoff, but my bootchart is still at 35seconds so no change, and I have a high resolution plymouth of the earth-sunrise animated theme instead of just 640x480. It even is staying at a high resolution during shutdown. This is with nvidia 295.09 drivers. 

(Had to recompile my kernel as I had no uvesafb in my build. lol)

---

### Post by lucazade on 2012-02-07
> **cariboo907 said:**
> So again I'm disappointed that Plymouth works for me on both my netbook, and my desktop system. My desktop system uses a GeForce 210 [noparse](GT218)[/noparse] and the Nvidia 290.10 driver, and my netbook is using the Intel 945 chipset with the i915 driver.

Cariboo plymouth cannot be defended, it never worked flawlessly.. just some examples:
low res with proprietary drivers, broken colors on old cards (colorful dots on radeon), late plymouth display in startup process (just few sec on a 15sec startup), absent splashscreen during shutdown, visible services messages in the background, a lot of flicker during switch grub->vts->X.

These are the cards I tested plymouth with in all these years:
Nvidia 250Gts 1gb, Nvidia 555Gtm 1gb, Ati Radeon 7500 32mb, Ati Radeon 3200 256mb, Intel HD3000, Intel GMA500 8mb.
I think it is a heterogeneous test base :)

Old Usplash and Xsplash were a lot better.

---

### Post by BigSilly on 2012-02-07
> **lucazade said:**
> Old Usplash and Xsplash were a lot better.

I absolutely agree. It's popular to just blame those of us using proprietary drivers, and say it's our fault because we use nvidia-current. But I run Ubuntu on a Dell laptop with Intel graphics and an EeePC as well as my desktop, and Plymouth has never worked as it should on any of them. It looks rubbish across all of them at one point or another, with text interrupting the boot, flashing displays before log in, and as mentioned above only ever the briefest of glimpses of the actual boot animation.

---

### Post by Yellow Pasque on 2012-02-07
> **effenberg0x0 said:**
> @all

What would be the Ubuntu procedure to suggest (and hopefully get approval) for Temujin's work as a /etc/alternatives/bootsplash like:
[0] (Default) Plymouth
[1] No Bootsplash

?

Regards,
Effenberg
The Ubuntu devs don't like the idea of removing plymouth: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372)

---

### Post by dino99 on 2012-02-07
dependancies on plymouth removed for Precise: mediahacks ppa

---

### Post by Harry33 on 2012-02-07
One more time.

Scott James Remnant put it in this way, the explanation to why there is Plymouth:

"The graphical parts of plymouth are contained in the plymouth-theme-*  packages which are Recommends only, without them Plymouth merely  regulates access to the system console in cases of filesystem decryption  and error."

So, removing Plymouth themes does solve the graphical part of this issue. No more visible Plymouth.
Then again, Plymouth does also other jobs in Ubuntu systems. That is the reason Canonical believes it should not be removed.

---

### Post by exploder on 2012-02-07
I would be happy if plymouth at least worked right with the open source drivers. This is an LTS release after all. I see a lot of effort going into consistency in Unity. The same kind of attention to detail needs to be given to plymouth and the boot experience.

---

