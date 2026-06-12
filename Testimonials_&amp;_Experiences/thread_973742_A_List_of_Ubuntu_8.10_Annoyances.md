---
title: "A List of Ubuntu 8.10 Annoyances"
date: 2008-11-07
forum: Testimonials &amp; Experiences
---

### Post by yman on 2008-11-07
I already made A List of Ubuntu 8.04 Annoyances ([http://ubuntuforums.org/showthread.php?t=939242](http://ubuntuforums.org/showthread.php?t=939242)), and loads of that stuff has already been fixed, although that's got nothing to do with me. I did nothing really except maybe report 1 or 2 bugs. Here's the humble beginning of the 8.10 annoyances list:
[LIST=1]
[*] Ekiga doesn't integrate with the system-wide online status.
[*] Empathy by default is missing packages for various protocols, including IRC and SIP.
[*] Errors in Empathy are displayed as a list of huge oversized boxes that can expand the Contact List window infinitely. Pidgin's approach to displaying error messages is better.
[*] Every so often when expanding Empathy from the system tray, the window borders don't appear, and it gets stuck in between the open and closed state. In this condition it appears neither in Ctrl+Alt+Tab nor in Alt+Tab, and it remains always on top, thus permanently obscuring other windows until it is closed.
[*] I think linux-backports-modules-intrepid should be installed by default for systems with iw4965, since system lockups and kernel panics are serious issues.
[*] Missing menu entries (and apparently icons as well) for Globulation 2 and Xshogi.
[*] Closing the main window of Firefox 3.0 while its downloads window is open causes the loss of all open tabs.
[*] Since Ubuntu 8.10 is never going to be directly upgraded to an LTS release, having the option to only show LTS upgrades could cause problems for end users.
[*] After exiting Funguloids, the "key presses repeat when key is held down" is checked in the configuration panel, but in reality is disabled. One needs to uncheck and then check it for it to truly be enabled. ([Bug #278904]("https://bugs.launchpad.net/ubuntu/+source/funguloids/+bug/278904"))
[*] Some of the recommended packages seem to have been removed during the upgrade, including some fonts and wesnoth-music. This is in spite of the recommending packages remaining on the system.
[*] CrossOver creates folders by the names of My Music, My Pictures, and My Videos under ~/Documents, when it could instead use ~/Music, ~/Pictures, ~/Videos.
[*] If I enable both English and Hebrew spell-checking simultaneously, then English spell-checking doesn't work but Hebrew does. ([Bug #295209]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/295209"))
[*] Evolution crashes a lot when I switch the view (Mail, Tasks, Calendar, etc).
[*] Sometimes Ubuntu freezes completely when I resume. In this case I have to shut down.
[*] Sometimes Ubuntu freezes when trying to unlock the screen. In this case I have to restart X.
[/LIST]

And I'll try to put in proper bug reports, but it's late and I need my sleep.

This system is an upgrade from Ubuntu 8.04 on HP Pavilion dv2910us.

---

### Post by tvtech on 2008-11-07
1. the backlight and light sensors in many notebooks this is especially apparent in Asus notebooks; [bug reports]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251278") have been filed;does not work by default, a second party program must be installed.
2.The boot log still seems to be an issue.  This problem was found in Fiesty and hasn't been addressed yet [bug # 98955]("https://bugs.launchpad.net/upstart/+bug/98955")it's not just a Ubuntu problem as it has been found in Fedora as well.
3. usplash being enabled causes a horrible beep to eminate on boot from my machine again, [Bug # 292121]("https://bugs.launchpad.net/ubuntu/+bug/292121") 
4. My network interface is unusually slow on boot up, this may just be a problem in general since it's slow in windows as well.  
5. again and persistently suspend does not work on initial install.  it does suspend and it does resume from suspend what it doesn't do is turn the backlight for the LCD back on which really honestly makes it impossible to actually see what's on the screen. 
6. The biometrics device which seems to not work at all, doesn't even seem to exist/ same with my multimedia touch pad and remote control. I think this is a job for Ndiswrapper perhaps. 
7. the onboard camera works with some of the apps in the main repositories but not others and it is referencing the same mount point in both applications, specifically camorama cannot see the camera at /dev/video0 but cheese camera can. 
8. when installing ubuntu server 8.04 or 8.10 it no longer builds grub properly and you cannot boot if you have a primary hardrive and a secondary storage on a raid controller, unless you install the os to the raid controller. it also recognizes the drives improperly assigning hd 1,0 differently from grub again making boot impossible. 
9. I haven't upgraded my other laptop to 8.10, and cannot/ haven't been able to upgrade my server to 8.04 lts because of the drive recognition. 
10. Boot speed is extremely slow, The kernal loads many modules for hardware I DONT HAVE, this is more a linux gripe than a Ubuntu issue. but it causes my slow boot.
11. Cups-pdf is not installed by default anymore. it also gives the following error```
Fri Nov  7 20:12:04 2008  [ERROR] failed to create directory (/home/username/PDF)
Fri Nov  7 20:12:04 2008  [ERROR] failed to create user output directory (/home/username/PDF)
```  You can manually create the directory and it will work fine.  but this should be automatic.  [bug # 295318]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295318")

Please note these aren't bugs filed by me so I'm not the only one having problems. 
[COLOR="Red"]This is a fresh install of 8.10 X64 on an Asus M70VM-C1 dual boot with Vista on two separate hard drives.[/COLOR]

---

### Post by 3rdalbum on 2008-11-07
I haven't encountered any of those, but I have encountered these:

23. Suspend and hibernate are, once again, broken,
24. Gnome sound effects do not work anymore
25. Pulseaudio occasionally causes certain programs to not open
26. Pulseaudio causes high latency with sound effects (i.e. the sounds play too late) in games and the login screen.
27. Jockey (Hardware Drivers) and the Appearance panel would not enable restricted drivers for my Nvidia card straight after install when I chose the "Install Ubuntu" option, and Appearance still "searches" for drivers before enabling Compiz.
28. My wireless now drops to slow speeds and often drops out
29. Login speed is slow.

---

### Post by Idefix82 on 2008-11-07
I like your lists :)
Can't comment on it this time, since I am sticking with Hardy. Good luck in sorting all these out!

---

### Post by yman on 2008-11-07
> **tvtech said:**
> 
22. I've got some serious issues it's probably because of my mother, I'm sure Freud would agree.


I don't see how that's a bug in Ubuntu. You can hardly open a bug report over having a mother.

Aside from that, I think you should start the numbering on your lists from number 1, not number 10 or number 23.

---

### Post by Burigufutsushide on 2008-11-07
I'm pretty sure your empty "My" folders in Documents is the result of you using Wine or CrossOver, as Documents is the default location of the Windows folders

---

### Post by yman on 2008-11-07
> **Burigufutsushide said:**
> I'm pretty sure your empty "My" folders in Documents is the result of you using Wine or CrossOver, as Documents is the default location of the Windows folders

That would explain it. How annoying though, since it could just use ~/Music, ~/Pictures, and ~/Videos. So maybe that entry doesn't belong here, since this is about Ubuntu annoyances. I need to think about it.

In any case, I checked it out. These directories are created when creating a bottle in CrossOver Pro 7.1.0.

---

### Post by yman on 2008-11-07
> **Idefix82 said:**
> I like your lists :)

When Aaron Seigo talked about how he hates problem lists and likes solution lists, I tried to take it to heart and thus these lists aren't meant to be rants and are meant as a first, casual step towards me helping to create a solution.

I didn't realize you've become a fan of this, especially because it's a tool born of laziness.
> 
Can't comment on it this time, since I am sticking with Hardy. Good luck in sorting all these out!

I'm sure everything will be fixed with the release of Jaunty, just like how so much of my previous list was made obsolete with the release of Intrepid.

---

### Post by tvtech on 2008-11-08
> CrossOver creates folders by the names of My Music, My Pictures, and My Videos under ~/Documents, when it could instead use ~/Music, ~/Pictures, ~/Videos.

This is the default Documents directory in my opinion it is a bug, because on complex programs with indepth file associations it creates problems in Wine/Crossover such as Cadd programs that use linked file associations to access program features, link document libraries etc.  It makes it so you can't describe the link associations properly in the native windows program and because of this can't use the program.  The developers don't feel it is a bug. so what do I know?

---

### Post by Alexia_Death on 2008-11-08
> 
2.the boot log has been disabled because of a bad library somewhere???? this is a pretty big issue because my boot automatically fails 2 out of 3 times and I have no clue why and no log to check.


Boot log? may be your boot fails before any log can be writen to the drive... What you need is to disable usplash and remove quiet from your kernel options. If grubs menu.list gets replaced during update it makes is default, that is splash and quiet. You need to edit your menu list to remove these two options from your kernel parameters.

---

### Post by tvtech on 2008-11-08
> Boot log? may be your boot fails before any log can be writen to the drive... What you need is to disable usplash and remove quiet from your kernel options. If grubs menu.list gets replaced during update it makes is default, that is splash and quiet. You need to edit your menu list to remove these two options from your kernel parameters.

Unfortunately it doesn't always fail, usplash and quiet have both been removed, since usplash caused a horrible beeping noise to eminate from my computer on boot.  I found another [Thread]("http://ge.ubuntuforums.com/showthread.php?p=6108940")  That appears to deal with the boot problem, not the noise but the failed mount issue, if I do in fact solve it with this information I"ll update. 

Since it doesn't mount and doesn't generate a boot log during the failure I can't do anything to see what is going on.  Does grub create a log?  

the specific failure is as follows. every 2-3 boots it locks out my secondary hard drive and fails to go any further all it shows is a black screen with the backlight on and nothing else.requiring a hard shutdown and reboot.  My secondary hardrive is where Ubuntu is installed. If I find a good solution to this I"ll let you know.  Still the Boot log not working on a normal boot is a problem.

---

