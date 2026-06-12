---
title: "Ubuntu on an old Dell Optiplex 745 - Thoughts?"
date: 2013-08-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Gilad_Pellaeon on 2013-08-08
Hi there. I'm debating lately on switching completly over to Ubuntu come 2014 or sooner because of Microsoft planning to stop Windows XP updates or perhaps even Kubuntu (As I do love the look and feel of KDE) but I am curious if Kubuntu would run better if it can be tweaked to use less ram and graphics features if it would be a better option then even Xubuntu simply because I find KDE looks the closest to a typical windows install. I currently use a Dell Optiplex 745 tower desktop with 1gb ram, Intel Q965 graphics (using up to 256mb system ram) and running Windows XP SP3. 

I typical use my desktop to browse on the net pretty much and watch netflix, BUT I find there's just a few concerns I have holding me back from switching. One is with the netflix-desktop package that apparantly installs its own modified version of WINE, is it possible to have a completly seperate WINE install that wouldn't interfere with netflix-desktop and vice versa? I ask because I do run Foobar2000 as my audio player/converter and i'd like to have the option to at least run it in it's own WINE install along with other windows programs I may need to run.

Also, for years I have used WinRAR extensivly to convert .zip file downloads to .rar files as well as using WinRAR since 2008 when I bought my license for it and I'm wondering is there any comparible GUI archiver/compression tool on Ubuntu that can handle all my old and new rar files? 

And finally, the bigger question has there been any headway in making Adobe flash actually run better under Firefox on Ubuntu because on my desktop it's pretty silly in my honest opinion to see a game such as Songpop on facebook run so bad that the sounds play before the graphics are even finished updating (IE sounds are not in sync with buttons and graphics generated in that game) but the minute I run google chrome with it's own built in Pepperflash in Ubuntu it runs just as fast as it does on Firefox on Windows XP. This was just testing from a live USB in various distributions including Lubuntu, Xubuntu, and Linux Mint 14 and 15.

I'd rather not have to end up next April 2014 running Windows XP still with a firewall and other tweaks and i'd feel more secure running Ubuntu and having updates at least, or would I be better off setting up a dual boot install with the bare minimum partition size needed for Windows XP to boot up if I absolutely needed it and go from there?

---

### Post by mJayk on 2013-08-08
Haya,

Firstly I would say try Kubuntu but KDE is, in my opinion, a heavy DE. Have something like LDXE or Xfce ready to try out in case you feel KDE is to slow.

Secondly yes you can have as many independent wine installs as you like play on linux takes this approach to install multipul programs (different versions of wine for different programs)

Thirdly Yes there are many GUI archive tools that can handle .rar's I THINK the default one that comes with Ubuntu can handle .rar's

Im not 100% sure on the flash issue but I use 13.04 and have had no flash problems, compared to 12.04 when I used to have a few flash problems (I use firefox)

Hope this helps.

---

### Post by 3rdalbum on 2013-08-08
> **Gilad_Pellaeon said:**
> I ask because I do run Foobar2000 as my audio player/converter and i'd like to have the option to at least run it in it's own WINE install along with other windows programs I may need to run.

Very little runs in Wine, so this issue is probably less important to you than you think. There are loads of music players for Linux that integrate nicely with the Linux desktop - why not use one of those? You'll have a bad experience trying to use programs from another operating system, and if you're moving to Ubuntu just to run Windows programs you might as well buy a copy of Windows 7.

> Also, for years I have used WinRAR extensivly to convert .zip file downloads to .rar files as well as using WinRAR since 2008 when I bought my license for it and I'm wondering is there any comparible GUI archiver/compression tool on Ubuntu that can handle all my old and new rar files? 

Yes. Install the unrar package and the default archive manager will understand RARs.

> And finally, the bigger question has there been any headway in making Adobe flash actually run better under Firefox on Ubuntu because on my desktop it's pretty silly in my honest opinion to see a game such as Songpop on facebook run so bad that the sounds play before the graphics are even finished updating (IE sounds are not in sync with buttons and graphics generated in that game) but the minute I run google chrome with it's own built in Pepperflash in Ubuntu it runs just as fast as it does on Firefox on Windows XP. This was just testing from a live USB in various distributions including Lubuntu, Xubuntu, and Linux Mint 14 and 15.

The Mozilla plugin for Flash is discontinued and the only Flash player that will be kept updated is the Pepperflash one in Chrome. If this gives you what you want, why not just use it?

> I'd rather not have to end up next April 2014 running Windows XP still with a firewall and other tweaks and i'd feel more secure running Ubuntu and having updates at least, or would I be better off setting up a dual boot install with the bare minimum partition size needed for Windows XP to boot up if I absolutely needed it and go from there?

Dual-boot is always a good idea if you're new or uncertain whether you'll still need Windows. Most people tell me - and I experienced it myself - that you get a gut feeling of "I want to run Ubuntu only, and I have no need for Windows anymore" after running Ubuntu for a year or so. When you get that feeling, you can erase Windows. Or at least restrict it to its own little virtual machine where it can't hurt anything! I need Windows for filing my tax once a year, so I have a Vista virtual machine for only that purpose.

---

### Post by Gilad_Pellaeon on 2013-08-08
> **3rdalbum said:**
> Very little runs in Wine, so this issue is probably less important to you than you think. There are loads of music players for Linux that integrate nicely with the Linux desktop - why not use one of those? You'll have a bad experience trying to use programs from another operating system, and if you're moving to Ubuntu just to run Windows programs you might as well buy a copy of Windows 7.


Out of the music players I've tried on a few *buntu distro's the only one I actually liked and that actually worked flawlessly showing the embedded artwork in my ogg vorbis music collection was Audacious. However, I've yet to find comparible programs in Ubuntu that has a built in replaygain scanner like foobar2000 does, and a program called mp3tag v2.55a is what I use to add that embedded coverart, if anything that'd be the only real purpose to using WINE is to run foobar2000 for that replaygain scanner/tagger and mp3tag to add in the embedded coverart. Otherwise all the other windows programs I currently use such as CdisplayEX, Irfanview, Xnview, Keepass 2 and Notepad++ have equivalents in the Ubuntu apps directory.

> 
Yes. Install the unrar package and the default archive manager will understand RARs.


I saw that in the apps directory but does it allow the default archive manager to then make rar files as well or am I limited to just uncompressing rar files?

> 
The Mozilla plugin for Flash is discontinued and the only Flash player that will be kept updated is the Pepperflash one in Chrome. If this gives you what you want, why not just use it?


Couple of reasons actually. There is no "Noscript" plugin/extension for Chrome like there is in firefox and even Adblock plus extension in Firefox is a LOT more powerful and more configurable compared to Chrome where it is vastly crippled to the point you can't even do much with it. And it is kind of an annoyance when one has to end up using two browsers with chrome being meant to run facebook or other flash games with acceleration in Ubuntu, and then Firefox for everything else with better extension support.

> 
Dual-boot is always a good idea if you're new or uncertain whether you'll still need Windows. Most people tell me - and I experienced it myself - that you get a gut feeling of "I want to run Ubuntu only, and I have no need for Windows anymore" after running Ubuntu for a year or so. When you get that feeling, you can erase Windows. Or at least restrict it to its own little virtual machine where it can't hurt anything! I need Windows for filing my tax once a year, so I have a Vista virtual machine for only that purpose.

If I do take the Ubuntu plunge I think this is what I would end up doing. If it wasn't for that whole Adobe flash versus Pepperflash issue because of Adobe deciding not to support it anymore officially with proper hardware acceleration in Ubuntu then it would probably be a bigger incentive for more people to switch and not having to use two browsers with two different versions of flash.

---

### Post by lykwydchykyn on 2013-08-09
First, I have Kubuntu installed on an opti 745 (though with 2 GB of RAM), and it runs pretty well.  The visual effects can be toned down, but they aren't necessarily what makes it heavier to run; KDE/Plasma also runs several background processes that can be a bit heavy (file indexing, PIM services, etc).  "Fast enough" is subjective, of course, but you will just have to see which desktop strikes the right balance of looks and performance for your tastes.  Pretty much all of them (perhaps barring Unity) can be heavily customized to look like whatever you want, within certain limits.

---

### Post by Gilad_Pellaeon on 2013-08-09
For now I took the time this evening to setup Lubuntu 13.04 as an exclusive on this tower. My fiance's machine will remain running Windows XP if I absolutely have any desperate need to run a windows program that bad if I decide not to setup WINE and or a VM. :)

---

### Post by lykwydchykyn on 2013-08-10
> **Gilad_Pellaeon said:**
> 
I saw that in the apps directory but does it allow the default archive manager to then make rar files as well or am I limited to just uncompressing rar files?

If you have the "multiverse" repositories enabled, there is a package called "rar" which can create rar files.  It claims to be shareware, so it's probably from the rarlabs folks.  Have you tried a non-encumbered option like lzma compression for your purposes?  I personally have learned the hard way that it's best not to rely on proprietary formats for long-term archiving.

> 
Couple of reasons actually. There is no "Noscript" plugin/extension for Chrome like there is in firefox and even Adblock plus extension in Firefox is a LOT more powerful and more configurable compared to Chrome where it is vastly crippled to the point you can't even do much with it. And it is kind of an annoyance when one has to end up using two browsers with chrome being meant to run facebook or other flash games with acceleration in Ubuntu, and then Firefox for everything else with better extension support.


The flash situation is frustrating, though personally I haven't really noticed issues with Adobe flash (yet); it performs well enough for my needs.  I don't know that there will be a solution forthcoming, unless:

- Mozilla changes its mind and implements Pepper API (not likely)
- Adobe changes its mind and continues flash development for Linux (not likely)
- One of the FOSS implementations of flash matures and becomes performant (very not likely)
- Flash is put out of our misery and everyone starts doing things in HTML5 & Javascript (possible, but not likely to happen soon)

---

### Post by Gilad_Pellaeon on 2013-08-10
> 
The flash situation is frustrating, though personally I haven't really noticed issues with Adobe flash (yet); it performs well enough for my needs.  I don't know that there will be a solution forthcoming, unless:

- Mozilla changes its mind and implements Pepper API (not likely)
- Adobe changes its mind and continues flash development for Linux (not likely)
- One of the FOSS implementations of flash matures and becomes performant (very not likely)
- Flash is put out of our misery and everyone starts doing things in HTML5 & Javascript (possible, but not likely to happen soon)


To my suprise adobe flash running under Firefox 23 with Lubuntu 13.04 on this machine had no lag running a popular game called Songpop on facebook. I was almost floored that the sounds kept up with the animation in that I didn't hear extra popping noises after buttons were rendered. I'm chalking it up to either less overheard with Lubuntu OR better intel drivers this time around. Haven't tried running a 720p flash video yet on Youtube but if that is laggy then i'll resort to installing Google Chrome and use it's pepperflash just for youtube. :roll:

---

### Post by mamamia88 on 2013-08-11
Funny I just got one of these on ebay for about $100.  It has 2gb ram though.  I have arch with xfce on it and it runs great.   I would use windows if you absolutely need to watch netflix.  Or get an xbox from someone dumping it before the new one comes out for cheap.   Maybe try one of those apps that allow you to build an lighter weight version of windows?

---

### Post by Gilad_Pellaeon on 2013-08-11
> **mamamia88 said:**
> Funny I just got one of these on ebay for about $100.  It has 2gb ram though.  I have arch with xfce on it and it runs great.   I would use windows if you absolutely need to watch netflix.  Or get an xbox from someone dumping it before the new one comes out for cheap.   Maybe try one of those apps that allow you to build an lighter weight version of windows?

Actually, i installed netflix-desktop and made one change to it which was adding in the Media Hint extension in Firefox so I can access american netflix content here in Canada and it seems to work fine. If you've ever seen what canadian netflix offers in comparison to american it's like "Woah I had no idea american netflix has ten times more content". Even added Media Hint to Google Chrome so I can watch TV shows on Hulu complete with american commercials :roll: since normally hulu doesn't like canadians trying to watch american TV shows I guess. :P

Also have another tower with windows xp that has netflix running so my fiance can watch her favorite shows :roll: and a PS3 and Wii to watch Netflix if I absolutely want to watch canadian netflix content on the TV. :)

---

