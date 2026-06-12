---
title: "Magic Workstation (MWS) under WINE"
date: 2009-05-29
forum: Wine
---

### Post by KingAlanI on 2009-05-29
Any of you Magic the Gathering fans out there try running MWS under WINE? MWS/Magic Workstation is a system for playing trading card games online; the software itself is a bare engine; card databases are available for various trading card games [This separation enables you to play games besides MtG, and may help keep the devs out of legal hot water with the producers of the TCG's played on the system)

I'd like to hear your stories about it; I recently tried this myself.

I normally use MWS on my Windows box, but I'm trying to get it working on my Linux machine (Ubuntu 9.04, GNOME, Intel x86 32-bit) as a side project.

I have it working, somewhat

I got (whatever the latest version of WINE is) from Applications | Add/Remove; that part worked fine.

Then, as WINE's appDB suggested, I downloaded [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
and ran the following terminal command (after I did sudo apt-get install coreutils):

sh winetricks corefonts [Make sure that the 'winetricks' section of the command is refferring to the directory where the script as actually located]

Download the MWS executable like usual, just open it with WINE.
Then do the same thing with the executable that installs the card database.

Then run Magic Workstation. (Applications/WINE/Programs/Magic Workstation/Magic Workstation)

It works pretty much like native Windows until you actually get a game started (connect to server and join works like normal)

You can still play, but it's choppy/slow. Disconnections also seem more frequent. (Even though I'm only a few feet away from the router, that may be partially blame-able on the laptop's WiFi as opposed to the Windows desktop's hardwired Internet connection. Eventually, I may get the laptop on a hardwired connection, see if that helps.)

Also, the cards and card pictures are readable, but are upside down.
Sometimes, the game's keyboard shortcuts don't work; I haven't noticed any shortcuts that are *consistent* failures

---

### Post by asdfoo on 2009-05-29
> **KingAlanI said:**
> Any of you Magic the Gathering fans out there try running MWS under Wine? MWS/Magic Workstation is a system for playing trading card games online; the software itself is a bare engine; card databases are available for various trading card games [This separation enables you to play games besides MtG, and may help keep the devs out of legal hot water with the producers of the TCG's played on the system)

I'd like to hear your stories about it; I recently tried this myself.

I normally use MWS on my Windows box, but I'm trying to get it working on my Linux machine (Ubuntu 9.04, GNOME, Intel x86 32-bit) as a side project.

I have it working, somewhat

I got (whatever the latest version of Wine is) from Applications | Add/Remove; that part worked fine.

Then, as Wine's AppDB suggested, I downloaded [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
and ran the following terminal command (after I did sudo apt-get install coreutils):

sh winetricks corefonts [Make sure that the 'winetricks' section of the command is refferring to the directory where the script as actually located]

Download the MWS executable like usual, just open it with Wine.
Then do the same thing with the executable that installs the card database.

Then run Magic Workstation. (Applications/Wine/Programs/Magic Workstation/Magic Workstation)

It works pretty much like native Windows until you actually get a game started (connect to server and join works like normal)

You can still play, but it's choppy/slow. Disconnections also seem more frequent. (Even though I'm only a few feet away from the router, that may be partially blame-able on the laptop's WiFi as opposed to the Windows desktop's hardwired Internet connection. Eventually, I may get the laptop on a hardwired connection, see if that helps.)

Also, the cards and card pictures are readable, but are upside down.
Sometimes, the game's keyboard shortcuts don't work; I haven't noticed any shortcuts that are *consistent* failures

Which version of Wine are you using?

---

### Post by KingAlanI on 2009-06-08
How does oen figure that out?

---

### Post by hikaricore on 2009-06-09
> wine --version

^

---

