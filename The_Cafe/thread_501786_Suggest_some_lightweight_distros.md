---
title: "Suggest some lightweight distros?"
date: 2007-07-15
forum: The Cafe
---

### Post by Frak on 2007-07-15
I have an old laptop back from '00-'01 and I would like some suggestions for some lightweight distributions that come with lightweight apps. Vector like, not DSL like. This laptop will be for my mom for when she's at home and likes to do basic things such as email, browsing, or Word processing. She's not dumb, but she's not tech savy, nor linux savy.
I'll list the specs
Dell Inspiron 2500
Intel integrated graphics
Floppy and CD
Linksys WPC11 v4 card with the Realtek chipset (from which I know is heavily supported)
10GB HD (I am setting up a server though for storing files)
PIII
256MB RAM

Thanks for the suggestions!:guitar:

---

### Post by %hMa@?b&lt;C on 2007-07-15
puppy is nice, but the package management SUCKS
I would suggest [http://en.wikipedia.org/wiki/KolibriOS](http://en.wikipedia.org/wiki/KolibriOS)
it looks really nice, fits on one floppy, it should fly!

---

### Post by RAV TUX on 2007-07-15
> **Frak said:**
> I have an old laptop back from '00-'01 and I would like some suggestions for some lightweight distributions that come with lightweight apps. Vector like, not DSL like. This laptop will be for my mom for when she's at home and likes to do basic things such as email, browsing, or Word processing. She's not dumb, but she's not tech savy, nor linux savy.
I'll list the specs
Dell Inspiron 2500
Intel integrated graphics
Floppy and CD
Linksys WPC11 v4 card with the Realtek chipset (from which I know is heavily supported)
10GB HD (I am setting up a server though for storing files)
PIII
256MB RAM

Thanks for the suggestions!:guitar:
The absolute best lightweight distro is [Wolvix]("http://wolvix.org/") & [Wolvix Cub.]("http://wolvix.org/")

---

### Post by regomodo on 2007-07-15
dsl
zenwalk
feather
fluxbuntu
vector

i personally prefer a icewm ubuntu dapper server install. uses 28mb of ram

---

### Post by poohbear1616 on 2007-07-15
> The absolute best lightweight distro is Wolvix & Wolvix Cub.

Yep....I just started playing around with the live disk today and I'm impressed.

---

### Post by Frak on 2007-07-15
bump

---

### Post by wolfen69 on 2007-07-15
xubuntu would run on your machine.

---

### Post by xubu_caapn on 2007-07-15
The best solution is to do a server install and then install your own lightweight window manager. 

Otherwise, I suggest Zenwalk. it doesn't have a large package repository but it is very fast, stable and easy to use. I too have heard good things about Wolvix, and it uses fluxbox rather than xfwm so it's probably faster. they both have live cds, so try em' both out!

---

### Post by kerry_s on 2007-07-15
The best one is the 1 you build to fit your moms needs. You start from the bottom and build your way up. I just did a setup for grandma who has basically the exact same needs( [http://ubuntuforums.org/showthread.php?t=498808](http://ubuntuforums.org/showthread.php?t=498808) ). Just take your time and try to picture how she uses it and what she uses. Then setup along those lines.

I'll run through a basic start setup for xfce4, since that's what vector uses and you want something along that line, i recommend debian for the base, once it's installed you never have to install again, you can simply grab updated applications from lenny & sid repos from time to time to bring your whole system up to date, no more reinstalling with each release.

If your lazy and you want a basic full xfce4 install, grab this 1-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

If you want to try a custom read on->

Grab the net installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

start the install,type> installgui
for the pretty installer, when you get to the package selection uncheck all of them, we want from scratch.
after reboot, login as root and use the root password you put during setup.

type-> apt-get install xorg gdm synaptic xfce4 xfce4-appfinder mousepad iceweasel pidgin
after that's done press> ctrl+alt+delete <that will make it reboot, and this time it should startup to a nice gui login, login with the user name you made during install. you should have a basic desktop with thunar as your file manager, iceweasel is the web browser(firefox with a different name), pidgin is the instant messenger. I going to leave the rest of the software up to you, you just open synaptic and select what ever you want to install. i recommend you google around for app choices.

for example:
the office suite, the standard is open office, but it's huge and slow.
The alternative is a mix of light applications. for word/doc most people use "abiword" which is light and fast, but only does the the word,docs,rtf those kind of things. for things like powerpoint, if you need to edit them you have no choice but openoffice, but if you just need to view them you can just use pptveiw, which is a windows application run through wine, tip setup up wine desktop size to 800x600 if you don't want it going full screen, run> winecfg <in terminal.

there's several thread's on light applications here in the forum so do a search.

---

### Post by Frak on 2007-07-15
Thanks kerry_s, much appreciated :)

---

### Post by Pobega on 2007-07-15
Why not do a Debian base install, and manually pull in the packages you want/need? xserver obviously, and any WM you'd like. I find that it's better to build your own environment on older computers than to use a prebuilt one (Like what Ubuntu offers by default).

---

### Post by Motoxrdude on 2007-07-15
> **Frak said:**
> I have an old laptop back from '00-'01 and I would like some suggestions for some lightweight distributions that come with lightweight apps. Vector like, not DSL like. This laptop will be for my mom for when she's at home and likes to do basic things such as email, browsing, or Word processing. She's not dumb, but she's not tech savy, nor linux savy.
I'll list the specs
Dell Inspiron 2500
Intel integrated graphics
Floppy and CD
Linksys WPC11 v4 card with the Realtek chipset (from which I know is heavily supported)
10GB HD (I am setting up a server though for storing files)
PIII
256MB RAM

Thanks for the suggestions!:guitar:

Install[ ubuntu minimul]("https://help.ubuntu.com/community/Installation/MinimalCD")
Then once installed, run
```
sudo apt-get update
```
then
```
sudo apt-get install xorg gdm
```
If you want gnome then do
```
sudo apt-get install gnome-core gnome-applets
```
If you want [fluxbox]("http://fluxbox.sourceforge.net/") then do
```
sudo apt-get install fluxbox
```
Once that is done, restart and you you should see a friendly login screen. Btw, it will give you an error about the human theme not being installed and will revert back to the default gnome-theme.

Some basic applications:
Btw, you will not have the gnome terminal. To run this command press ctrl+alt+backspace. You might be stuck at a screen where you can't type in any commands. To get around this type "ctrl+alt+f2". Login and run
```
sudo apt-get install firefox abiword vlc synaptic gnome-terminal eog nautilas
```

This will provide a super-lean linux install that still remains functional.
BTW, i am probably forgetting a few packages for a functional desktop, feel free to add everyone!

EDIT: Damnit, didn't see kerry's post! :P

---

### Post by kerry_s on 2007-07-16
LOL, yeah there were alot of posts while i was typing away to. you know how it go's first come first served. :)

---

### Post by Frak on 2007-07-16
Thanks Motoxrdude, I'll try yours too, I like the thought of still  being able to use Ubuntu.

---

### Post by awakatanka on 2007-07-16
[http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)

> About antiX

antiX is a fast, lightweight and easy to install linux live CD distribution based on MEPIS for Intel-AMD x86 compatible systems. antiX offers users the "Magic of Mepis" in an environment suitable for old computers. So don't throw away that old computer yet! The goal of antiX is to provide a light, but fully functional and flexible free operating system for both newcomers and experienced users of Linux. It should run on most computers, ranging from 64MB old PII 266 systems with pre-configured 128MB RAM to the latest powerful boxes. 128MB RAM is recommended for antiX. antiX can also be used as a fast-booting rescue cd. 

Applications

    * 2.6.15 kernel
    * XOrg7
    * Fluxbox (default), IceWM (optional)
    * Rox-filer and Rox desktop (optional)
    * Firefox web browser
    * Sylpheed-claws email client
    * Gaim instant messaging
    * Xchat
    * AbiWord word processor
    * Gnumeric spreadsheet
    * Scite editor
    * The Gimp photo-editor
    * Xmms audio player
    * Xine and mplayer video players
    * Synaptic package manager
    * Graveman CDR/DVDR tool
    * All the MEPIS Utilities
    * Various CLI apps eg nano, mc, mutt, links2, irssi, raggle
    * And lots more! 


---

### Post by Frak on 2007-07-16
> **awakatanka said:**
> [http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)
That looks like a good prospect:)
I'll try this first.
(I'm lazy, I'd rather have someone have everything put together first, plus its good support when I screw it up:))

---

### Post by ThinkBuntu on 2007-07-16
Zenwalk for speed and stability. Debian for flexibility, speed, and package selection. In fact, I'd go with Debian for this.

---

### Post by Frak on 2007-07-16
I'm installing Zenwalk right now, but I most likely will try debian or AntiX on it too.
I don't do live cd's, I do the full experience. Its better to have the full experience IMHO.

---

### Post by ThinkBuntu on 2007-07-16
> **Frak said:**
> I'm installing Zenwalk right now, but I most likely will try debian or AntiX on it too.
I don't do live cd's, I do the full experience. Its better to have the full experience IMHO.
LiveCD is just a bonus to keep you entertained while it installs, in my opinion :^)

By the way, Zenwalk has a text-based installer (curses, actually) but is very, very easy. It's probably the best I've seen, although cfdisk can be tough for newcomers.

---

### Post by scrooge_74 on 2007-07-16
Debian net install, and pick and choose what you need

---

### Post by Frak on 2007-07-16
> **ThinkBuntu said:**
> LiveCD is just a bonus to keep you entertained while it installs, in my opinion :^)

By the way, Zenwalk has a text-based installer (curses, actually) but is very, very easy. It's probably the best I've seen, although cfdisk can be tough for newcomers.
I've installed Gentoo before, nothing really scares me away.

---

### Post by Max_Kbrown on 2007-07-17
I am using Absolute Linux on an old Compaq Presario 4508, Pentium 200 Mhz, 48 MB. It has everything I need,
give a try, you won't be dissapointed.

[http://www.pcbypaul.com/absolute/index.html](http://www.pcbypaul.com/absolute/index.html)

---

### Post by Frak on 2007-07-17
Thanks Max, I'll try that, looks great for a lightweight.

---

