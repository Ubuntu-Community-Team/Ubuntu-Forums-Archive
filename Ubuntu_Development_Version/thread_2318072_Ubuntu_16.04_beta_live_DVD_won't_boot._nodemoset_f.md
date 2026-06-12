---
title: "Ubuntu 16.04 beta live DVD won't boot. nodemoset fails too."
date: 2016-03-22
forum: Ubuntu Development Version
---

### Post by sanssadness on 2016-03-22
**Background**:

I've been having a huge number of problems trying to get Ubuntu installed on a new computer. 14.04 works just fine except for one huge problem: I have no sound. Under alsamixer, none of the sounds are muted. Someone suggested installing the latest Alsa driver.

I found these instructions:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

They led me to this page:

[https://code.launchpad.net/~ubuntu-a...aily/+packages]("https://code.launchpad.net/%7Eubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages")

The right driver for Ubuntu 14.04 LTS is oem-audio-hda-daily-dkms - 0.201603221016~ubuntu14.04.1

However, there is no .deb file. Extracting the tar.gz file gives a bunch  of folders and a Makefile. I run "make" in terminal, and it gives me  some error message:

make: *** No rule to make target  '.../oem-audio-hda-daily-dkms-0.201603221016-ubuntu14.04.1/buildroot/unpatched-source',  needed by 'patched-source'. Stop.

I can't figure out why it can't compile, and Google is unhelpful.

Someone suggests installing 16.04, which brings me to where I am now.

**The problem**:
I can boot from CD, but when I select "Try Ubuntu without installing," I freeze up at a purple screen. that looks like a desktop wallpaper. I tried it even with nodemoset, and it still fails. 14.04 and 15.10 both boot up fine (but I can't use them because they don't have sound)

Please help! Any sane person would have given up by now, but I've wasted an entire week trying to figure this out already, and the solutions look so ridiculously within reach...

---

### Post by deadflowr on 2016-03-23
Moved to the ***Ubuntu Development Version*** sub-forum

---

### Post by ventrical on 2016-03-23
What type of new computer do you have? Any specs?

Regards..

---

### Post by sudodus on 2016-03-23
The name of the boot option is **nomodeset**. Did you get it right or wrong? This boot option is a workaround with some graphics cards, to make it possible to boot into a system, where it is possible to install a proprietary driver to take advantage of the full power of the hardware.

---

### Post by sanssadness on 2016-03-23
It's a newer Skylake PC with a GTX 970 video card in it. Sorry for the misspelling on the boot option. Although I misspelled it here, I definitely used it correctly in the live DVD because I chose it in the GUI rather than typing it out.

With some testing, I've narrowed the problem down to graphics card (GTX 970). I did this by disabling discrete graphics in the BIOS, then booting into the live disc with integrated graphics, which fixed the problem. The problem only occurs on discrete graphics. It's a NVIDIA card, so I thought for sure nomodeset would work, but it doesn't.

Are there any other possible workarounds?

---

### Post by Bucky Ball on 2016-03-23
Installing an unreleased version is a strange way of going about fixing an audio issue in an otherwise faultless install. Did you post on the forums about your 14.04 LTS problems prior to making such a radical decision?

You're aware that 16.04 may have the identical issues? May have nothing to do with software. This is not uncommon and you'll be left with an unreleased version and exactly the same issues you have now with audio.

Anyhow, just throwing that in. My first line of attack would be to try fixing the audio in 14.04 (which is supported for another year and can be updated to 16.04 directly at any time until then via the net) by posting about it here.

Good luck however you choose to go about it. :)

(PS: The person suggesting 'try installing 16.04' is relying on pot luck and pretty much saying 'I've no idea how to help you fix your problem in 14.04 so install 16.04 and I have no idea whether that will make any difference either'.)

---

### Post by sanssadness on 2016-03-24
I did post about it, but unfortunately nobody could help. I know it sounded crazy to go to 16.04, but when I tested sound in 16.04, it actually did work. I went through so much trouble to try fixing it, including updating to the latest Alsa driver, but they didn't have the .deb file posted even though a help page said to look for it, and the source code wouldn't compile. Then people told me NOT to compile my own software even though it was my most promising lead because then I would become a developer and be responsible for all the associated problems. If sound works in 16.04, it's very likely that a newer driver fixed it. Imagine that, right? I'm not even a programmer and I have to debug code I can't even read just to get sound to work! But it's Ubuntu, and I've been told that I'm participating in an open source project so I should essentially just keep my mouth shut and live with it.

So yea, I know 14.04 is stable, but 16.06 is close to release date anyways, and I can update the beta to the stable version in a month. If all my hardware just works in 16.06 as it seems to when I tested with integrated graphics, I would gladly accept any instability it brings.

---

### Post by Bucky Ball on 2016-03-24
In that case, go right ahead! You didn't mention that sound worked in 16.04. Your thread is about the fact that you can't get the 16.04 DVD working so not sure how you could have tried it on 16.04 unless I'm missing something. :-k

---

### Post by sanssadness on 2016-03-24
Yeah, integrated graphics does work. I'm sorry my explanation wasn't that great. It's the consequence of wasting 10 hours per day for an entire week straight doing nothing but trying to figure out how to get sound working. After I get this problem fixed (IF I do that is), I'm going to retreat into a cave and will probably do nothing to explore the world of Ubuntu until support for whatever LTS version I happen to get to work runs out. I'm totally burned out and just want something that works.

Also, the last time I combined 2 problems into one thread, it went nowhere. I think it's my fault for not being as specific as possible. That's why I wanted (and still do) this thread to be purely about the graphics problem that leads to me being unable to boot. I only brought up sound to explain why I'm so desperate to get 16.04 working, even if it's not officially released yet.

If nomodeset hangs at the purple screen of the live disc (occasionally with 2 flashing desktop icons) on a computer with a GTX 970 graphics card that's known to boot the live disc properly on integrated graphics, what should I try next?

---

### Post by cariboo on 2016-03-24
Are you selecting install 3rd party packages when doing the Installation? If so just do a plain installation without downloading drivers and updates, and see what happens.

---

### Post by VMC on 2016-03-24
Is this the one you downloaded:[COLOR=#000000]
[/COLOR][COLOR=#000000]"xenial-desktop-amd64.iso  23-Mar-2016 08:45  1.5G  Desktop image for 64-bit PC (AMD64) computers (standard download"
[/COLOR][COLOR=#000000]
If so, did the md5sum match:
"[/COLOR][COLOR=#000000]3efcd738cff03d2d579e08f55117111d *xenial-desktop-amd64.iso"[/COLOR]

[COLOR=#000000]Also how and where did you place: "nomodeset" ???[/COLOR]

[COLOR=#000000]Also you post #9 states that your integrated graphics works. What do you mean by that. Does Ubuntu boot okay with [/COLOR] [COLOR=#000000]integrated graphics, but freezes using "[/COLOR][COLOR=#000000]GTX 970 video card"   ?

My [/COLOR][COLOR=#000000]integrated[/COLOR][COLOR=#000000] graphics chip will freeze using nouveau but works using nvidia driver. But always works under nouveau using "nomodeset". (I prefer "[/COLOR]nouveau.noaccel=1" instead of  "nomodest" , because then I have full resolution.)

---

### Post by sanssadness on 2016-03-24
Yep, that's the image I downloaded; except the copy I got was from yesterday (March 22). The SHA256 checksum matched the one posted alongside the image.

I'm not at the point where I can actually do an installation yet, unfortunately. I have a weird requirement to use Luks/LVM and I haven't figured out that part yet. I'm taking on the problems one at a time. For the purposes of this thread, if I can just get the dvd to boot into the environment where I can "try Ubuntu" I'll be pretty happy already. All the problems I'm describing are pre-installation.

I selected nomodeset in one of the options in the GUI by pressing F6, then hitting Enter next to the "nomodeset" option, so I couldn't have mistyped it.

Now here's what happens in both situations:
1. I boot with integrated graphics: No problem. I get to play around with Ubuntu without doing an installation.

2. I boot with GTX 970: The boot process hangs at the purple screen. I see 4 triangles with their tips meeting at the center of the screen. I'm guessing that's the default wallpaper. I've tried booting many times, with nearly identical results. Sometimes, instead of a purely purple screen with 4 triangles, I get 2 flashing desktop icons. If I press Ctrl + Alt + Del, I get some process manager listing active processes.

---

### Post by sudodus on 2016-03-24
Is your final goal with this computer to have a dual boot system (with Windows), or a single boot system with only Ubuntu? Are you installing in UEFI mode or BIOS mode?

1. If you must ***install alongside*** an already installed Windows system, that is installed in ***UEFI*** mode, it is best to install Ubuntu in UEFI mode too. And you should continue along the path you have already started: try to find some boot option, that helps make the graphics work :-)

Now that it works with the integrated graphics chip, you can install the system, and the installed system will probably work with integrated graphics chip too. Make sure it works like it should.

Learn to use the soft reboot method ***SysRq  r e i s u b*** in order to avoid corrupting the file system of the installed Ubuntu system, if it does not respond to your normal method to reboot.

Press the hotkey combination for SysRq (often ***alt + PrtScrn***) at the same time as you slowly press each of the keys ***r e i s u b***. See this link [Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

Then you can connect the nvidia card again, and boot the installed system. I suggest that you try nomodeset again in the installed system. It might work better than in the live system. If no luck, [COLOR="#cc0000"]try with the boot option **text**[/COLOR] (instead of nomodeset, but entered manually at the grub menu), and install an nvidia proprietary driver. After reboot your graphics might work :-)

2. ***Otherwise*** you can install Ubuntu in whatever mode you prefer, and it is easier in ***BIOS*** mode (alias CSM).

In BIOS mode you can use a ***text mode installer:*** Get ***Ubuntu mini.iso*** and make a boot CD/DVD/USB drive, and you can install in text mode.

Then in the installed system, you can use the boot option **text** (instead of nomodeset, but entered manually at the grub menu), and install an nvidia proprietary driver. After reboot your graphics might work :-)

See the tips in this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by sanssadness on 2016-03-24
Wow what a detailed reply! I appreciate the help and I'm trying some of what you said right now.

> **sudodus]Is your final goal with this computer to have a dual boot system (with Windows), or a single boot system with only Ubuntu? Are you installing in UEFI mode or BIOS mode?

1. If you must ***install alongside*** an already installed Windows system, that is installed in ***UEFI*** mode, it is best to install Ubuntu in UEFI mode too. And you should continue along the path you have already started: try to find some boot option, that helps make the graphics work :-)

Now that it works with the integrated graphics chip, you can install the system, and the installed system will probably work with integrated graphics chip too. Make sure it works like it should.

Learn to use the soft reboot method ***SysRq  r e i s u b*** in order to avoid corrupting the file system of the installed Ubuntu system, if it does not respond to your normal method to reboot.

Press the hotkey combination for SysRq (often ***alt + PrtScrn***) at the same time as you slowly press each of the keys ***r e i s u b***. See this link [URL="https://en.wikipedia.org/wiki/Magic_SysRq_key"]Magic SysRq key
[/URL][/QUOTE]

Yes, dual booting encrypted Truecrypt and LUKS/LVM encrypted Ubuntu is indeed my final goal. I wish I had the ambition to do more, but honestly I think I got many white hairs this week from just trying to achieve this. I know when I've had enough. Actually, strange though it may sound, Windows is in fact installed in BIOS rather than UEFI. You can do this if before installing Windows you use an MBR partition table and boot in BIOS said:**
> 
Then you can connect the nvidia card again, and boot the installed system. I suggest that you try nomodeset again in the installed system. It might work better than in the live system. If no luck, [COLOR=#cc0000]try with the boot option **text**[/COLOR] (instead of nomodeset, but entered manually at the grub menu), and install an nvidia proprietary driver. After reboot your graphics might work :-)


I'm going to have to try this. If nomodeset really works better than in the live system, then I'm out of excuses to try to get the installation working. Not that I need an excuse. I've spent a whole week trying to figure out a way to get LUKS to play nice with LVM. I seriously don't understand why Ubuntu took out the alternate CD. That move ruined my YEARS of stability. If you have a moment, take a look at what I used to be able to do: [http://ubuntuforums.org/showthread.php?t=2318208](http://ubuntuforums.org/showthread.php?t=2318208)

That guide worked perfectly for 12.04. I managed to get around the lack of an alternate installer for 14.04 by upgrading my system, but that method no longer works now. Upgrading from 12.04 to 14.04 to 15.10 was apparently too much; my install was ruined by the upgrade and wouldn't boot again. After many years with this nice setup, I got a new computer and things went bad fast.

[QUOTE=sudodus]
2. ***Otherwise*** you can install Ubuntu in whatever mode you prefer, and it is easier in ***BIOS*** mode (alias CSM).

In BIOS mode you can use a ***text mode installer:*** Get ***Ubuntu mini.iso*** and make a boot CD/DVD/USB drive, and you can install in text mode.

Then in the installed system, you can use the boot option **text** (instead of nomodeset, but entered manually at the grub menu), and install an nvidia proprietary driver. After reboot your graphics might work :-)

See the tips in this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")[/QUOTE]

Am I even using nomodeset properly? I select the option in the F6 menu, but I don't see the line of text with "quiet" and "splash" changed at all. I added nomodeset before quiet and splash to see if it would work, but it didn't; I still hang at a purple screen.

I have to find a way to fix this; my graphics problem is so bad that when in the installer, when I use Ctrl + Alt + F2 to open a new terminal, all I see is black background with a blinking white cursor that doesn't respond. I tried "text" mode for the installer, but I don't know if boot options apply to it too. I'm testing it right now.

---

### Post by sudodus on 2016-03-24
There are three ways to use a text mode (alias debian) installer with Ubuntu.

***1. Ubuntu mini.iso*** (mentioned in my previous post)

***2. Ubuntu Server***. You can install the desktop environments with meta-packages after installing a minimal system without server packages.

After reboot into the installed minimal text based system:

```
sudo apt-get install ubuntu-desktop  # to get standard Ubuntu
sudo apt-get install lubuntu-desktop  # to get Lubuntu
sudo apt-get install xubuntu-desktop  # to get Xubuntu
...
```

***3. Lubuntu alternate***. There are still alternate installers for Lubuntu (even Xenial to be released as 16.04 LTS).

---

### Post by sudodus on 2016-03-24
See this link and links from it for more details about boot options: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by sudodus on 2016-03-24
I am testing 'encrypted disk with LVM and LUKS' and 'encrypted home with ecryptfs' as part of the iso-testing of Lubuntu Xenial. I can check that things can be installed and work according to the standard methods in the installers. But I am no security expert, and no expert on LVM. So I can't really help you with those tasks.

---

### Post by sanssadness on 2016-03-25
I noticed a while ago that there is such an option for Lubuntu. Why doesn't that feature exist in Ubuntu? There used to be an alternative disc for 12.04. I know they only wanted to maintain one disc, but I thought by now they'd have added the LVM and LUKS (or vice versa) feature to the newer versions of Ubuntu desktop.

As far as I can tell, the installer is a stripped-down version of 12.04 alternate. I think I can set up LUKS partitions, but not an encrypted LVM that contains LUKS. The latter is better because you only have to type the password once to unlock the LVM.

---

### Post by Bucky Ball on 2016-03-25
Have you tried using the minimal installer? That is basically what used to be the alternative but stripped back further from what I see. You might be able to do what you want there and then simply:

> sudo apt-get install ubuntu-desktop

That will get you Ubuntu desktop version.

---

### Post by sanssadness on 2016-03-25
Does the minimal installer have something the regular installer doesn't?

---

### Post by sudodus on 2016-03-26
You have asked for a text mode debian installer with some options to install LVM. Then you have two alternatives which can be used to install standard Ubuntu

- the Ubuntu mini.iso
- the Ubuntu Server iso file

You can try both. Maybe you can use one of them to solve your problem.

---

### Post by VMC on 2016-03-26
I don't think going from minimal and build from there you buy you anything over the full dvd. Once the minimal is built up you will still have to work out the "[COLOR=#000000]GTX 970" problem.[/COLOR]

[COLOR=#000000]So using onboard integrated graphic chip everything works OK, correct? Once you plug in the nvidia [/COLOR][COLOR=#000000]GTX 970, have you checked what options are set in your BIOS? Make sure onboard graphics is turned off.[/COLOR][COLOR=#000000] [/COLOR]

---

### Post by VMC on 2016-03-26
What exact Skylake do you have?
This one: [Skylake i7 6700]("http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work"). Read the Mint users post. He has a similar issue as yours.  Is your integrated chip intel?

---

