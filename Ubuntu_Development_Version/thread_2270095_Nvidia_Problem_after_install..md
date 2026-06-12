---
title: "Nvidia Problem after install."
date: 2015-03-20
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2015-03-20
I have installed ubuntu 15.04 yesterday on my asus optimus notebook :) and everything seems ok except this two things:

- installation of nvidia 346.47 driver

- after installing 'nautilus-open-terminal' and 'nautilus-actions', I have a double 'open in terminal' option inside right click menu in Nautilus

---

### Post by howefield on 2015-03-20
Hello aljosa2,

I have moved your post from the thread in which you had posted it very unkindly hijacking a completely different topic.

---

### Post by dino99 on 2015-03-20
> **aljosa2 said:**
> I have installed ubuntu 15.04 yesterday on my asus optimus notebook :) and everything seems ok except this two things:

- installation of nvidia 346.47 driver

- after installing 'nautilus-open-terminal' and 'nautilus-actions', I have a double 'open in terminal' option inside right click menu in Nautilus

346.47-0ubuntu4 might solve your issue  (uvm now integrated, so purge the old package if installed)

---

### Post by aljosa2 on 2015-03-20
Hi 9d9, thanks for your reply.
I don't know what is "uvm".
Also I don't understand what do you mean by "346.47-0ubuntu4"?
I've tried to install Nvidia 346.47 both via Ubuntu additional drivers and via ppa:mamarley/nvidia. 

If I install via Ubuntu additional drivers, reboot is successful - however later I have a nice but dead desktop without launcher and mouse.
If I install via mamarley ppa, and before rebooting I try to select Intel graphics with nvidia-prime, I find that nvidia-prime and almost all other setting options within Nvidia control panel are missing.

Edit:
mu launcher is set to auto-hide, so maybe the missing launcer is caused by missing mouse cursor...not sure...

---

### Post by dino99 on 2015-03-20
that's what happen when you try everything without purging the previous installed

---

### Post by aljosa2 on 2015-03-20
It was a brand new clean Ubuntu 15.04 when I tried to install Nvidia via additional drivers

---

### Post by grahammechanical on 2015-03-20
> [COLOR=#000000] I find that nvidia-prime and almost all other setting options within Nvidia control panel are missing.[/COLOR]

That will happen if the driver is not building or compiling for the Linux kernel. When I first tried the Linux kernel 3.19.0-rc I could not get any Nvidia driver to build. And I noticed that the Nvidia Xserver settings manager was empty of settings, just as you have noticed.

I removed the kernel 3.019.0-rc. Later through normal updates I got kernel 3.19.0-7 and that would build for Nvidia 340 but not for 346. Then I got kernel 3.19.0-9 and that would not build for any Nvidia driver. So, I had to use kernel 3.19.0-7 with Nvidia 340. I now things have improved and I am using kernel 3.19.0-9 with nvidia 340.

The driver from the PPA might be newer than the driver from Additional Drivers and it might not be building for Kernel 3.19.0-9 which is present kernel in 15.04. Try using an older Nvidia driver.

Did things work fine when you first installed Ubuntu? When we install Ubuntu and we tick the box "install third party software" the installer will install a proprietary video driver. If things worked well when you rebooted then use the driver that Ubuntu installed and do not use the 346 driver until things have been fixed.

I also found that these failures to build did mess up Additional Drivers a bit and I had to purge the Nvidia driver and do a couple of restarts.

```
sudo apt-get purge nvidia*
```

Regards.

---

### Post by dino99 on 2015-03-20
@graham

sorry but you are wrong; i've already seen your other posts about bad nvidia installation for you; but the vivid nvidia driver is the most fixed and up to date.
I'm a nvidia 346 user and it works with all the kernels tested/used (aka 3.19.xx); there is no compilation issue (if the required compiling packages are installed of course) mainly the kernel headers

---

### Post by aljosa2 on 2015-03-20
> grahammechanical:
When we install Ubuntu and we tick the box "install third party software" the installer will install a proprietary video driver.

I didn't know for that, are you sure? I always install restricted extras later, and not through software center but through terminal. Also, bear in mind that there are several proprietary driver choices inside settings-additional drivers, so it seems to me better that the decision of which driver to choose is made by me.

I don't know **when** and **how** this Nvidia drivers were inserted into Vivid World, but your bad experience with Nvidia and various kernels is quite interesting, and very similar to my problems:

> *aljosa2, today:*
If I install via Ubuntu additional drivers, reboot is successful - however later I have a nice but **dead desktop without launcher and mouse**.

> *aljosa2, 3 days ago:*
live dvd experience: with 20150316/16-Mar-2015 daily image **no mouse, no touchpad**, so i just wasted 1,5 euro for dvd.

Anyway, I've made another clean installation, without Nvidia. Will wait few days...

---

### Post by ventrical on 2015-03-20
> **aljosa2 said:**
> I didn't know for that, are you sure? I always install restricted extras later, and not through software center but through terminal. Also, bear in mind that there are several proprietary driver choices inside settings-additional drivers, so it seems to me better that the decision of which driver to choose is made by me.

I don't know **when** and **how** this Nvidia drivers were inserted into Vivid World, but your bad experience with Nvidia and various kernels is quite interesting, and very similar to my problems:
Anyway, I've made another clean installation, without Nvidia. Will wait few days...

> 
grahammechanical:
When we install Ubuntu and we tick the box "install third party software" the installer will install a proprietary video driver.                      


Yes .. he is sure.  In development  testing it is par for the course that most of us do not choose that option . The result is that you will most likely end up with a broken or seriously limited install - re - llvmpipe. Ubuntu does not really cover every single different PC motherboard and there are several different variants of BIOSes on the same board with many different configurations - so this is a hardware jockeying problem and proprietary nVidia drivers are notorious for breaking systems and kernels breaking nVidia during development.

> 

Anyway, I've made another clean installation, without Nvidia. Will wait few days...

As testers, this is sometimes the best option when there is a  proprietary nVidia problem. The same goes for nouveau-firmware on nVidia adapters.

Regards..

---

### Post by grahammechanical on 2015-03-21
@9d9

How can I be wrong when I am relating my own experience? Nvidia 346 might be the most fixed and up to date for you with your hardware but not for me and my hardware. At least not yet. One of the reasons for this section of the forum is to relate our experiences using the development release. Just because I am having a different experience from you does not make me wrong.

At the moment ubuntu-drivers is only listing nvidia 304 and 340 for my adapter. It maybe that nvidia has dropped support for my adapter or to put it another way, they did not include support for my adapter in nvidia 346. Who knows, I might never be able to use 346 and later. That does not make me wrong.

---

### Post by Cavsfan on 2015-03-21
After you've purged nvidia packages when you install nvidia-340 (340.76) in terminal it will automagically pull in all needed packages including uvm. 
This is what I did. And my system is running fine on this old nVidia Geforce 9800GT card.

```
sudo apt-get install nvidia-340
```

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-340                                  340.76-0ubuntu1                            amd64        NVIDIA binary driver - version 340.76
ii  nvidia-340-uvm                              340.76-0ubuntu1                            amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-340                       340.76-0ubuntu1                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8                                        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             346.35-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by ventrical on 2015-03-21
Op is talking about nVidia Optimus!!

Please watch whole video and listen to the first speaker (nVidia) "famous Optimus chip"....


[https://www.youtube.com/watch?v=IVpOyKCNZYw](https://www.youtube.com/watch?v=IVpOyKCNZYw)

---

### Post by ventrical on 2015-03-21
..and if you have patience .. here is a really good DebConf14 Q&A with Linus Torvalds on many of these issues (if you got an hour and a half to listen).

[https://www.youtube.com/watch?v=5PmHRSeA2c8](https://www.youtube.com/watch?v=5PmHRSeA2c8)

---

### Post by Cavsfan on 2015-03-21
> **ventrical said:**
> Op is talking about nVidia Optimus!!

Please watch whole video and listen to the first speaker (nVidia) "famous Optimus chip"....


[https://www.youtube.com/watch?v=IVpOyKCNZYw](https://www.youtube.com/watch?v=IVpOyKCNZYw)

Oh, didn't realize that it made a difference. Still don't see any difference after looking it up but then again I don't have a laptop.
It sounded to me the OP just didn't get all of the packages needed which is why I posted what I did.

I watched that video. :lol:

I don't have the patience the to watch the 2nd one though.

Edit: I get it now Optimus is a chip but still don't see why that matters but I see that the lady (1st speaker in the video) had a problem with her dual card laptop with an Optimus chip?
Didn't know they made dual video card laptops. Guess I am behind the times.

---

### Post by Cavsfan on 2015-03-23
So OP, problem solved?

---

### Post by ventrical on 2015-03-23
> **Cavsfan said:**
> Oh, didn't realize that it made a difference. Still don't see any difference after looking it up but then again I don't have a laptop.
It sounded to me the OP just didn't get all of the packages needed which is why I posted what I did.

I watched that video. :lol:

I don't have the patience the to watch the 2nd one though.



It's interesting in that it discusses, in part, some of the difficulties that developers and driver writers have with the kernel and how a fix commit in the kernel can so easily break something else. If you can stand the swearing, course language, rants from Linus (and rants from questioners telling Linus how unprofessional he is for calling his co-workers and helpers more terrible things than lemmings with frost bite) then enjoy.. but , if not , then be warned.

:)

---

### Post by Cavsfan on 2015-03-23
Yeah I can't watch something that long. But I just don't understand why nVidia can not be more cooperative about providing updates for Linux drivers.

I mean that seems stupid to me as Linus points out in the first video. :lol: It's not like we aren't buying nVidia cards or systems with them already installed.
I've always preferred nVidia cards. nVidia had no problem providing micro$oft windows with driver updates. They do it way to much IMO.

My windows 7 install with the GeForce 9800GT card has not been able to update the drivers for more than a year now. 
It just can't handle it although the card is mentioned as supported.

The last driver for windows 7 and my card is 341.44 released on 2015.2.24 but I dare not install it.

I guess micro$oft might pad their pockets from time to time, something which should not be necessary.

---

### Post by ventrical on 2015-03-23
In the case of nVidia (and most other hardware driver developers) it's about putting food on their tables. There is no money in writing proprietary software for ubuntu. They do , however, get a lot of free adspace for their hardware chipsets when ubuntu and the other linuxes run without issue. It does seem to correct itself usually during near the end of a cycle.

I have had great success with Intel graphics and nouveau running on nVidia but when I go looking for surplus hardware I usually try to aquire Intel mother boards with  Intel graphics chipsets. It gives me the option to swap in a PCIe nVidia card and if it doesn't work or rolls to llvmpipe then I can still use the mobo for it's working Intel graphics and not waste time and money.

Regards..

---

### Post by Cavsfan on 2015-03-24
> **ventrical said:**
> In the case of nVidia (and most other hardware driver developers) it's about putting food on their tables. There is no money in writing proprietary software for ubuntu. They do , however, get a lot of free adspace for their hardware chipsets when ubuntu and the other linuxes run without issue. It does seem to correct itself usually during near the end of a cycle.

I have had great success with Intel graphics and nouveau running on nVidia but when I go looking for surplus hardware I usually try to aquire Intel mother boards with  Intel graphics chipsets. It gives me the option to swap in a PCIe nVidia card and if it doesn't work or rolls to llvmpipe then I can still use the mobo for it's working Intel graphics and not waste time and money.

Regards..

Yes, you'd think they would do it for the advertisement of success on Linux systems. When all there is is talk about how bad nVidia drivers are on Linux it gives them a bad name one would think.

I don't see the difference between writing proprietary software for either windows or ubuntu is going to put food on their tables. They make the money when they sell the cards.
The driver updates always come free.

That reminds me of my son getting this souped up gamer laptop that had both an intel chipset and a nice nVidia card in it. He said on batteries it would use the intel chipset and when plugged in it would use the nVidia driver. He has since sold that laptop and opted for this super i7 system full tower 780ti nVidia card booting from a 1TB SSD and 2 1TB SATA drives that were RAID plus a couple of other SSDs. He said it boots in about 2 seconds. :) My PC boots ubuntu in several seconds but windows takes so long you can go make a sandwich or get a cup of coffee while it's booting up. :p

Any how I wonder if the OP ever got his Optimus working or not...

Regards...

---

### Post by aljosa2 on 2015-03-24
i still haven't tried to install nvidia again. please let me know if something's wrong here:

this one is a command with which i'm removing nvidia:

> sudo apt-get remove nvidia-346 nvidia-settings nvidia-primewhat command do you guys use to purge nvidia?

> sudo apt-get remove --purge nvidia-*i have read somewhere that by doing so you need to reinstall some dependencies of the ubuntu-desktop package?

---

### Post by Cavsfan on 2015-03-24
> **aljosa2 said:**
> i still haven't tried to install nvidia again. please let me know if something's wrong here:

this one is a command with which i'm removing nvidia:

what command do you guys use to purge nvidia?

i have read somewhere that by doing so you need to reinstall some dependencies of the ubuntu-desktop package?
[B]
sudo apt-get purge nvidia*[/B] will do the trick.

You should see at the bottom that is will uninstall anything this command shows is installed: **dpkg -l | grep nvidia**

Edit: You should not see anything about ubuntu-desktop at all.

---

### Post by aljosa2 on 2015-03-27
i have just purged nvidia in my wife's optimus notebook (ubuntu 14.04.2)... installed new kernel 3.19.3... since there is nothing inside additional drivers, i installed nvidia 346 via mamarley ppa... it's not working, control panel is almost empty - there's no settings... so waiting remains my only choice...

---

### Post by QDR06VV9 on 2015-03-27
> **aljosa2 said:**
> i have just purged nvidia in my wife's optimus notebook (ubuntu 14.04.2)... installed new kernel 3.19.3... since there is nothing inside additional drivers, i installed nvidia 346 via mamarley ppa... it's not working, control panel is almost empty - there's no settings... so waiting remains my only choice...
 
I'm confused this post says you are using 14.04 if this is the Case then kernel 3.19 and nvidia won't work.
I have kernel 3.18 on trusty and nvidia 346 runs very nice.

---

### Post by tokyobadger on 2015-03-28
> **runrickus said:**
> I'm confused this post says you are using 14.04 if this is the Case then kernel 3.19 and nvidia won't work.
I have kernel 3.18 on trusty and nvidia 347 runs very nice.
My turn to be confused: there's an nvidia driver 347 release? I'm using [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") and I see versions 340, 346, and 349. I have 349 installed on a desktop with 2 GTX680 cards in SLI with 15.04, standard kernel 3.19.0-10 and it works fine.

@aljosa2: you must have married an angel - my wife would flip her lid (and probably worse) if I screwed up her laptop and then said it was **my** only choice to wait ;-)
According to [wiki.ubuntu.com]("https://wiki.ubunutu.com/TrustyTahr/ReleaseNotes")
[quote="wiki.ubuntu"]By default, the 14.04.2 point release will ship with a newer [3.16]("https://launchpad.net/ubuntu/+source/linux-lts-utopic") Linux kernel from Ubuntu 14.10, and a matching X.org stack.  This is based on the [3.16.0]("http://kernel.ubuntu.com/git?p=ubuntu/linux.git") [Extended Upstream Stable Kernel Release]("https://wiki.ubuntu.com/Kernel/Dev/ExtendedStable").  The purpose of providing a newer kernel in the 14.04.2 point release is for hardware enablement.[/quote]
The latest kernel for Trusty (14.04.1) seems to be 3.16.0-33 though there is 3.16.0-34 in [proposed]("http://www.ubuntuupdates.org/package/core/trusty/main/proposed/linux-image-generic-lts-utopic")
You'll need to share what the hardware is and what you've got installed in detail (and accurately) in order for others to help.

---

### Post by aljosa2 on 2015-03-28
> **runrickus:**
I'm confused this post says you are using 14.04

hi,
i have 2 optimus notebooks, one with ubuntu 14.04.2 and another with ubuntu 15.04... i'm comparing two systems and experimenting...

> **tokyobadger:**
you must have married an angel - my wife would flip her lid (and probably worse) if I screwed up her laptop and then said it was my only choice to wait

hi,
after installing nvidia, before restarting i've chosen intel graphics with nvidia-prime selector, so everything is just wonderful :)
her optimus notebook is pretty problematic and behave much better with ubuntu 15.04 (livecd experiment), but i'm waiting the official release

---

### Post by dino99 on 2015-03-28
That one works well: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-346](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-346)

---

### Post by aljosa2 on 2015-03-28
> **aljosa2 said:**
> I have installed ubuntu 15.04 yesterday on my asus optimus notebook :) and everything seems ok except this two things:

- installation of nvidia 346.47 driver

- after installing 'nautilus-open-terminal' and 'nautilus-actions', I have a double 'open in terminal' option inside right click menu in Nautilus
after installing some updates this morning, the problem with two icons in the unity launcher for nautilus seems solved. double 'open in terminal' option inside right click menu in nautilus is still here.

---

### Post by QDR06VV9 on 2015-03-28
> **tokyobadger said:**
> My turn to be confused: there's an nvidia driver 347 release? I'm using [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") and I see versions 340, 346, and 349. I have 349 installed on a desktop with 2 GTX680 cards in SLI with 15.04, standard kernel 3.19.0-10 and it works fine.

The latest kernel for Trusty (14.04.1) seems to be 3.16.0-33 though there is 3.16.0-34 in [proposed]("http://www.ubuntuupdates.org/package/core/trusty/main/proposed/linux-image-generic-lts-utopic")
You'll need to share what the hardware is and what you've got installed in detail (and accurately) in order for others to help.

Thanks for pointing that out fixed now(nividia-346)
I am running a non stock kernel on trusty 3.18.10-031810-generic

---

### Post by Cavsfan on 2015-04-12
Found this and thought it might be useful for Optimus cards.

[http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)

This is just before step 6 and since it specifically mentions Optimus I thought I'd mention it. I don't have an Optimus card so I can't verify the link.

```
For Bumblebee (NVIDIA Optimus) you can use the following PPA:

     sudo add-apt-repository ppa:bumblebee/stable
     sudo apt-get update
     sudo apt-get install bumblebee

```

There is other potentially useful information in that link I hope.

---

### Post by aljosa2 on 2015-04-12
Hi, current situation is as follows:

on my wife's Ubuntu 14.04.2 with kernel 4.0-rc7, driver Optimus Nvidia 346.47 from Xorg-Edgers PPA doesn't work

on my wife's Ubuntu 14.04.2 with kernel 4.0-rc7, driver Optimus Nvidia 349.12 from Xorg-Edgers works perfectly

Since the new Nvidia 346.59 driver has been released just a few days ago, and since the final Linux kernel 4.0 is to be released later today, I will try tomorrow if on my Ubuntu 15.04 this optimus combination works ok.

---

### Post by aljosa2 on 2015-04-13
> **aljosa2 said:**
> Hi, current situation is as follows:

on my wife's Ubuntu 14.04.2 with kernel 4.0-rc7, driver Optimus Nvidia 346.47 from Xorg-Edgers PPA doesn't work

on my wife's Ubuntu 14.04.2 with kernel 4.0-rc7, driver Optimus Nvidia 349.12 from Xorg-Edgers works perfectly

Since the new Nvidia 346.59 driver has been released just a few days ago, and since the final Linux kernel 4.0 is to be released later today, I will try tomorrow if on my Ubuntu 15.04 this optimus combination works ok.

Ubuntu 15.04, original 3.19.0-13.13 kernel.
After installing Nvidia 346.59 optimus driver via "additional drivers", there was no "need to restart computer" message.
I rebooted notebook manually, and while loging into Ubuntu something bad happened and notebook restarted itself. Second login attempt was successful. Driver works somehow, but it's not ok: 

> [    2.122528] nvidia: module license 'NVIDIA' taints kernel.
[    2.122531] Disabling lock debugging due to kernel taint
[    2.124590] nvidia: module verification failed: signature and/or  required key missing - tainting kernel

[    3.715433] vgaarb: this pci device is not a vga device
[    3.717759] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717802] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717826] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717850] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717872] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717895] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717929] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.717952] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    3.726006] ACPI Error: Field [TMPB] at 274432 exceeds Buffer [ROM1] size 262144 (bits) (20141107/dsopcode-236)
[    3.726010] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP._ROM] (Node ffff88041e9021e0), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[    3.744060] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[    4.449221] r8169 0000:04:00.0 eth0: link up
[    6.136192] vgaarb: this pci device is not a vga device


and who knows what else is wrong!?!

So, I purged all Nvidia stuff and installed final Linux kernel 4.0. Then I installed Nvidia 349.12 optimus driver from Xorg-Edgers.
Again, after rebooting, while loging into Ubuntu first time something bad happened and notebook restarted itself. Second login attempt was successful. Driver works somehow, but it's not ok: 

> [    1.933980] nvidia: module license 'NVIDIA' taints kernel.
[    1.933981] Disabling lock debugging due to kernel taint
[    1.936531] nvidia: module verification failed: signature and/or required key missing - tainting kernel

[    3.690140] vgaarb: this pci device is not a vga device
[    3.694568] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694611] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694634] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694654] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694675] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694695] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694727] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.694748] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.702502] ACPI Error: Field [TMPB] at 274432 exceeds Buffer [ROM1] size 262144 (bits) (20150204/dsopcode-236)
[    3.702506] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP._ROM] (Node ffff88041e9021e0), AE_AML_BUFFER_LIMIT (20150204/psparse-536)
[    3.720653] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    5.279258] r8169 0000:04:00.0 eth0: link up
[    6.139254] vgaarb: this pci device is not a vga device


Furthermore, I'm getting this bad messages:

> dmesg | grep i915
[    1.923450] [drm] Initialized i915 1.6.0 20150130 for 0000:00:02.0 on minor 0
[    1.923615] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    1.992168] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    3.060697] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.060698] i915 0000:00:02.0: registered panic notifier

---

### Post by dino99 on 2015-04-13
you have that acpi issue:
ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP._ROM] (Node ffff88041e9021e0), AE_AML_BUFFER_LIMIT (20150204/psparse-536)
ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)

the other 'error' are usual, not scary

you might need the latest clutter/mutter from gnome3-team staging ppa

---

### Post by cariboo on 2015-04-13
Jailed an off topic post.

---

### Post by aljosa2 on 2015-04-19
Xorg-Edgers PPA
**Most recent updates: 2015-04-18 / nvidia drivers 331, 340, 346 and 349**

So, I purged all Nvidia stuff and installed once again nvidia 346.59 (Ubuntu 15.04, final Linux kernel 4.0)
Apparently it works and seems ok, but here's dmesg output: 

> 
[    1.875733] nvidia: module license 'NVIDIA' taints kernel.
[    1.875735] Disabling lock debugging due to kernel taint
[    1.877959] nvidia: module verification failed: signature and/or required key missing - tainting kernel

[    1.867664] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem

[    0.237812] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.237814] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.237816] vgaarb: loaded
[    0.237817] vgaarb: bridge control possible 0000:00:02.0

[    3.576023] bbswitch: version 0.7
[    3.576029] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    3.576033] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    3.576051] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.576123] bbswitch: detected an Optimus _DSM function
[    3.576129] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    3.743595] vgaarb: this pci device is not a vga device
[    3.747903] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.747945] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.747968] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.747988] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.748009] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.748029] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.748060] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.748081] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.755753] ACPI Error: Field [TMPB] at 274432 exceeds Buffer [ROM1] size 262144 (bits) (20150204/dsopcode-236)
[    3.755757] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP._ROM] (Node ffff88041e9021e0), AE_AML_BUFFER_LIMIT (20150204/psparse-536)
[    3.773819] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    6.191374] vgaarb: this pci device is not a vga device


_edited_:

After rebooting the notebook a few times, with nvidia-prime selector I've chosen Intel graphics.
Here's my question:


> [    3.552227] bbswitch: version 0.7
[    3.552233] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    3.552237] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    3.552246] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)
[    3.552319] bbswitch: detected an Optimus _DSM function
[    3.552325] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    3.555776] [drm] Module unloaded
[    3.573115] bbswitch: disabling discrete graphics
[ 3.573125] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150204/nsarguments-95)


Nvidia is off, or bbswitch fails to turn off discrete graphics?

---

