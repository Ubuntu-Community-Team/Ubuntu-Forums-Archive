---
title: "Cannot get Ubutntu 10.04 to run Oblivion"
date: 2010-10-23
forum: Wine
---

### Post by ZeroCore on 2010-10-23
Okay, this is the up-teenth time I've tried to play any of my games on Ubuntu without any success, and it's just about to the point where I'm considering just shelling out the $150 to Microsoft for a copy of windows 7 and abandoning everything Linux.

I just cannot get any of my games to run in Ubuntu, especially Oblivion for that matter, and I consider that an inexcusable thing for an operating system.

Anyway,

I have an ATI radeon 9600 graphics card, WITH the X.org open source driver installed.
I'm running Ubuntu 10.04 lucid linux.


Despite following the advice of others AND the wiki on how to configure Ubuntu, Wine, and Oblivion to run, as well as the X.org configuration advice, I still have yet to get anything to run at all.

All I've been able to get so far is the intro title to the companies that made the game come up, watched them lag VERY slowly, before having the title screen come up, lag really slowly, the music barely playing, all before having the game quit when I try to start a new game (which then causes my desktop to malfunction when it crashes, as all the icons become enlarged until I restart my machine).

I also think that something may have become corrupted, as I removed the game from my hard drive soon after, and then when I try to load the disk again, it says that I don't have the permissions to do it (saying that it's not authorized). 


I really am about to give up hope on EVER playing any of my games again on this computer, and am seriously thinking about saving up enough money (which will most likely take half a year or more) to purchase windows 7 and do away with Linux forever. Any help would be more than appreciated.

---

### Post by Half-Left on 2010-10-23
The problem is that your graphics card is weak and old. I remember playing Oblivion on my NVIDIA 7800GTX years ago and it was slow and it's a lot more powerful then your ATI 9600.

It would be slow on Windows never mind Wine.

---

### Post by Jammy4041 on 2010-10-25
Yep, you will definetly need to consider a nvidia card. i got a 8500GT, and it runs oblivion fine.

---

### Post by cwwilson721 on 2010-10-25
The issue is your video card/chip and not having proprietary drivers installed.

If I try to run my Oblivion install with xorg/standard drivers (not Nvidia ones), the same thing happens as with you.

I run it with the Nvidia drivers, and it runs smooth and fine.

The major issue is that ATi/AMD doesn't support your chip/card with drivers. Update that, and you'll be fine (If you do decide to update/upgrade your card, get an Nvidia one. While ATi makes a fine product, Linux support/drivers are a bit 'lacking', like NOT supporting older cards. I found my Nvidia 9600GSO 768MB DDRIII card on eBay for $15USD, and it ROCKS. However, what you get depends on what you can use., PCI, AGP, PCI-Ex16)

---

### Post by mastablasta on 2010-10-25
> **ZeroCore said:**
> I just cannot get any of my games to run in Ubuntu, especially Oblivion for that matter, and I consider that an inexcusable thing for an operating system.
 
 
Operating sytsem not running programmes designed for a TOTALLY DIFFERENT Operating systemi is an inexcusable thing? How is that? i mean Oblivion was designed to play well in IWndows, why should it run in linux at all?
 
Ok let's put that aside...
 
WINE (eventhough not really an emulator) still emulates certian things and just  for that it needs extra processing power, RAM etc. now on top of this you add a relatively demanding game  - ofcourse you can't expect it to run blazingly fast. add an old graphics card to all this and poor drivers and you have a plan for "disaster"
 
Ok now as for the Radeon 9600 i have played oblivion on 9600XT (which is quite a bit faster than normal 9600) and could get away with it in WnXP with medium settings, shadows off, distance increased... basically a tweaked version that got me to settings between medium and high. resolution was 1024x768. any higher and it got too slow. 
 
in your case i would suggest to start with very low/low settin and work from there upwards. increasing the settings slowly. i hope i helped a bit and that you can get through to enjoy the game. otherwise you have the mentioned option of upgrading the card or installing windows to play it.
 
also 9600 doesn't have very good drivers in WindowsXP as well at least to my experience.

---

### Post by Half-Left on 2010-10-25
The simple fact is that the ATI 9600 makes the minimum specs for this game but you won't have a great experience playing it in my view.

---

### Post by Jammy4041 on 2010-10-26
Wine runs better on nvidia cards because the way the instructions are processed. 

The only problem that I have is that the waer is this weird shade of purple, but that can be easily sorted out. BTW, I have the GOTY version (with Knights of the Nine and Shivering Isles) and Knights of the Nine (Oblivion DLC disk) installed.

I remember editing the wine registry, to make sure that it used up all my video ram. Wine recognises my 8500GT as a 8300GS.

---

### Post by Grenage on 2010-10-26
> **ZeroCore said:**
> I really am about to give up hope on EVER playing any of my games again on this computer, and am seriously thinking about saving up enough money (which will most likely take half a year or more) to purchase windows 7 and do away with Linux forever. Any help would be more than appreciated.

If one of the main reasons you have a computer is to play games, do just that; I dual-boot Windows 7 for steam games.  Wine is really something, but for the cost of a Windows license...

---

### Post by Progressive on 2010-10-26
To fix any permissions issue go into the console and type > sudo chmod -R 777 ~/.wine/

I wouldn't recommend buying Windows or a newer card before getting the latest software, optimizing Oblivion, and turning down all the settings.

Step 1) Add [Xorg Edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") to your repositories and do an upgrade to get the latest graphics stack with the r300g driver

Step 2) Download the latest [official patches]("http://elderscrolls.com/downloads/updates_patches.htm") to Oblivion

Step 3) Download the following performance-enhancing mods into your Oblivion data folder... to avoid case insensitivity issues it is recommended that you extract these using the 32 bit windows version of [7zip]("http://www.7-zip.org/") via WINE:

(Read the instructions on these since there are often options to consider)

[Operation Optimization ]("http://www.tesnexus.com/downloads/file.php?id=10510")
[Oblivion Script Optimization]("http://www.tesnexus.com/downloads/file.php?id=13092") 
[Oblivion Polygone Overhaul ]("http://www.tesnexus.com/downloads/file.php?id=6981")
[Optimised Distant Land MAX]("http://www.tesnexus.com/downloads/file.php?id=15278")
[LowPoly Grass]("http://www.tesnexus.com/downloads/file.php?id=5434")
[Quiet Feet MAX]("http://www.tesnexus.com/downloads/file.php?id=12331")
[Enhanced Vegetation]("http://www.tesnexus.com/downloads/file.php?id=23783")

None of these noticeably affect visual quality, and the Enhanced Vegetation actually improves quality.

Step 4) Activate the newly added esps using the Data Files selection on the oblivion menu. Then, set the game's settings and resolution on the lowest, and see if it works... and raise them as needed. 

(may want to use winecfg, the WINE configuration menu, to allow a Virtual Desktop in the Graphics tab to prevent your ubuntu resolution from getting messed up)

Step 5) If that still isn't enough look into tweaking your [INI file]("http://www.uesp.net/wiki/Oblivion:Ini_Settings#Performance_tweaks") or ask me for further advice. There's lots more that could be done.

The INI tweaks to turn off the startup videos may be especially handy in your case.

---

