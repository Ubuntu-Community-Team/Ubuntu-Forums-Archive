---
title: "Linux/Ubuntu Wishlist"
date: 2005-09-16
forum: The Cafe
---

### Post by Gibbz on 2005-09-16
Ok guys this is my running wishlist for all linux distoros, not just ubuntu. But ubuntu is my favorite atm so i thought at least i should post it somewhere. Hopefully the devs see it and implement some stuff :)

These are just the things that really get to me about linux, most of them are small anoying things. But they add to the whole experience i think.





righclick + drag = pulldown menu(ala windows)

better copy/paste support between apps

ntfs support default, or easily obtainable via synaptic/cd(at least ntfs automatic mounting when botting into the os,like mepis)

easy to setup audio(i use onboard realtek and usb mic, 2 diffrent devices)

fonts that dont look so odd

tweaked UI for less "chunky" look(options to use small icons in the file browser etc)

DVD release with more of the common stuff(include 32 and 64bit on same dvd?) to save downloading (to give to those with dialup)

simple Gui editor for fstab(mounting)/bootloader

brightness/contrast/gamma settings GUI

fasterboot/shutdown times

a better compression tool, something like winrar but for linux would be nice

right click an exe(or other files)>"run with" so i can say run a windows exe file with cedega or something without using the console

right click an .deb(and other files)>"run as" so i can launch a file as an admin without needing the console(simmilar to the windows run as user)

Num Lock to stay on when i press it, and reboot. It is always off(works fine in suse/windows)!

Crtl-adlt-del similar to windows so i can kill programs that freeze, check cpu/memory/network usage. Check running applications.

Option to rename applications/places/system menus or just replace with icons

Skype/openvpn installed by default would be nice.

Power/sleep/wake to work on the keyboard buttons

windows key to open the applications menu(you dont realize how hard it is to navigate linux without a mouse, works in mepis linux)

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=Gibbz]Ok guys this is my running wishlist for all linux distoros, not just ubuntu. But ubuntu is my favorite atm so i thought at least i should post it somewhere. Hopefully the devs see it and implement some stuff :)
[/QUOTE]

Hello.. I don't want to burst your bubble, but the developers don't really read the forum. The forum is official, but they communicate through mailing lists and irc. The official feedback channel is bugzilla:

[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

Posting suggestion there will get them seen by someone who can make decisions.

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=Gibbz]
Num Lock to stay on when i press it, and reboot. It is always off(works fine in suse/windows)!
[/QUOTE]

[http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)

---

### Post by arnieboy on 2005-09-16
[QUOTE=Gibbz]simple Gui editor for fstab(mounting)/bootloader[/quote]
[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77) (for grub editing)
[QUOTE=Gibbz]brightness/contrast/gamma settings GUI[/quote]
apps like xine and webcam apps already have that.
[QUOTE=Gibbz]fasterboot/shutdown times[/quote]
install the following and uncheck the services u dont want to run at boot time. that will significantly speed up ur bootup/ shutdown times.
[http://ubuntuforums.org/forumdisplay.php?f=75](http://ubuntuforums.org/forumdisplay.php?f=75)

[QUOTE=Gibbz]a better compression tool, something like winrar but for linux would be nice[/QUOTE]
how did u find archive manager and/or ark inadequate?

[QUOTE=Gibbz]right click an exe(or other files)>"run with" so i can say run a windows exe file with cedega or something without using the console[/quote]
install wine and make all exe's run with wine (right click-->properties). that way all exe files will run with double clicks

[quote=Gibbz]right click an .deb(and other files)>"run as" so i can launch a file as an admin without needing the console(simmilar to the windows run as user)[/quote]
u can use a nautilus script to run a selected app as root.

[QUOTE=Gibbz]Ctrl-alt-del similar to windows so i can kill programs that freeze, check cpu/memory/network usage. Check running applications.[/quote]

[http://ubuntuforums.org/showthread.php?t=41174](http://ubuntuforums.org/showthread.php?t=41174)

[QUOTE=Gibbz]Option to rename applications/places/system menus or just replace with icons[/quote]

why do u want to rename System Menus? any special kick?

[QUOTE=Gibbz]windows key to open the applications menu(you dont realize how hard it is to navigate linux without a mouse, works in mepis linux)[/QUOTE]
System-->Preferences-->Keyboard Shortcuts . Look for "Show the Panel Menu" Hit the windows key (will show as "Super_L"). This is for the Gnome main menu though. I dont use separate menu launchers

---

### Post by Stormy Eyes on 2005-09-16
[QUOTE=Gibbz]fonts that dont look so odd[/quote]

What in Astarte's name do you mean by 'odd'? And if you don't like the existing fonts, what's to stop you from downloading your own TrueType fonts and unzipping them into ~/.fonts?

[QUOTE=Gibbz]tweaked UI for less "chunky" look(options to use small icons in the file browser etc)[/quote]

You can adjust the icon size in the file browser right now. Open a file browser window, and select **Edit -> Preferences** from the menu. Then find the "Default Zoom Level" under **Icon View Defaults** and select a different value. Try 75% and see how you like it.

[QUOTE=Gibbz]right click an exe(or other files)>"run with" so i can say run a windows exe file with cedega or something without using the console[/quote]

You can set up the file browser to do this now. Right-click on an *.EXE file in the file browser, select **Open With Other Application**, click on "Use Custom Command", and then type in "cedega" and then whatever options you normally use.

[QUOTE=Gibbz]right click an .deb(and other files)>"run as" so i can launch a file as an admin without needing the console(simmilar to the windows run as user)[/quote]

You should be able to make the file browser do this too. Right-click a *.DEB file, select **Open With Other Application**, click on "Use Custom Command", and then type in "gksudo dpkg -i". That'll prompt you for the password and then install the package. However, since you're using a commandline app, you'll have no way of knowing if it installed or threw an error.

[QUOTE=Gibbz]Crtl-adlt-del similar to windows so i can kill programs that freeze, check cpu/memory/network usage. Check running applications.[/quote]

From the **Applications** menu, select **System Tools > System Monitor**. Or open up a console, and type "top". Once in top, you can type 'k' to kill a frozen process by PID number.

Option to rename applications/places/system menus or just replace with icons

Skype/openvpn installed by default would be nice.

Power/sleep/wake to work on the keyboard buttons

windows key to open the applications menu(you dont realize how hard it is to navigate linux without a mouse, works in mepis linux)[/QUOTE]

---

### Post by Wolki on 2005-09-16
[QUOTE=Gibbz]
righclick + drag = pulldown menu(ala windows)[/quote]

Try middle click + drag.

> better copy/paste support between apps

You currently need to paste before closing any application. Some of this is fixed with GNOME 2.12 in Breezy.

> 
right click an .deb(and other files)>"run as" so i can launch a file as an admin without needing the console(simmilar to the windows run as user)

[http://www.ubuntuforums.org/showthread.php?t=33584](http://www.ubuntuforums.org/showthread.php?t=33584)

> 
Crtl-adlt-del similar to windows so i can kill programs that freeze, check cpu/memory/network usage. Check running applications.

[http://ubuntuforums.org/showthread.php?t=41174](http://ubuntuforums.org/showthread.php?t=41174)
> 
Option to rename applications/places/system menus or just replace with icons


You can replace them with one icon.

---

### Post by arnieboy on 2005-09-16
[QUOTE=Wolki]You currently need to paste before closing any application. Some of this is fixed with GNOME 2.12 in Breezy.
[/QUOTE]
though its not enabled in 2.10 by default, the following is a quickfix:
[http://ubuntuguide.org/#clipboard-daemon](http://ubuntuguide.org/#clipboard-daemon)

---

### Post by Gibbz on 2005-09-16
ok cool, thankns for the suggestions. Is there any way to backup my home folder to transfer between my laptop and PC so i dont have to configure everything twice?

---

### Post by aysiu on 2005-09-16
[QUOTE=Gibbz]ok cool, thankns for the suggestions. Is there any way to backup my home folder to transfer between my laptop and PC so i dont have to configure everything twice?[/QUOTE] Yeah, just copy and paste the folder.

---

### Post by arnieboy on 2005-09-16
[QUOTE=Gibbz]ok cool, thankns for the suggestions. Is there any way to backup my home folder to transfer between my laptop and PC so i dont have to configure everything twice?[/QUOTE]
do the following:
```
tar cvpzf backup.tgz /home/username/
```
where username is your account name. this will create an archive of your home folder.

---

### Post by Ubunted on 2005-09-17
Howzabout a way to make List View the default in all folders? Possible?

---

### Post by arnieboy on 2005-09-17
[QUOTE=Ubunted]Howzabout a way to make List View the default in all folders? Possible?[/QUOTE]
open up a nautilus window and go to edit -->preferences and change default view for new folders to "list view"

---

### Post by Ubunted on 2005-09-17
Ah okay, I've been there 3 or 4 times looking for that but I guess I was looking for a toggle button for some reason.

---

### Post by Boss 999 on 2009-07-28
I have just put up a wish-list for Ubuntu 10.04. Follow the link below:

[http://ubuntuforums.org/showthread.php?p=7691429#post7691429](http://ubuntuforums.org/showthread.php?p=7691429#post7691429)

---

### Post by bailbath on 2009-07-29
My wish is to find a new full size laptop preinstalled with Ubuntu in the UK.
Efficient pc did have some but no longer seem to? It is for my daughter and she has bout £300-400 to spend.
Ian

---

### Post by squiddy on 2009-12-27
what about adding ubuntu-tweak and acetoneiso to the repo ?

---

### Post by Ric_NYC on 2009-12-27
I wish Linux/Ubuntu gets rid of tarballs and command lines to install simple applications and drivers.

---

### Post by DeadSuperHero on 2009-12-27
Gotta love necroposting. :P

---

### Post by TheLions on 2009-12-27
[IMG]http://www.testriffic.com/resultfiles/25021necromancer.jpg[/IMG]

---

### Post by Keyper7 on 2009-12-27
> **Ric_NYC said:**
> I wish Linux/Ubuntu gets rid of tarballs and command lines to install simple applications and drivers.

I agree. I really wish someone, someday, creates something revolutionary like... I don't know... "packages" with precompiled software and... uh... "repositories" where you could easily download those packages. And maybe you could, like, upgrade software from such "repositories" too!

I know, I know... I'm dreaming too high here. Man, and what's up with those ridiculous names I'm bringing up? "Packages", "repository"... pfff, what ludicrous ideas...

Maybe in a future far, far away. For the time, I'll just have to accept that Linux only works with monochromatic monitors. Oh, well...

---

### Post by resolv_25 on 2010-03-05
Yes, quite some of the first suggestions are already functioning very well.
Not sure if anyone mention, but I have one regular problem with audio, i.e microphone settings, on different machines.
Seems that ALSA is having such a problems, hope it will be better.

My wish is to have as on windows XP and later - **Restore point**
Or Solaris has **Time Slider**
This would be a great thing.

---

### Post by Keyper7 on 2010-03-05
GOOD LORD.

The zombie rises AGAIN.

---

