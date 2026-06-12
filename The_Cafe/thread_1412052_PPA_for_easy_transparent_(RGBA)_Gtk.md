---
title: "PPA for easy transparent (RGBA) Gtk"
date: 2010-02-20
forum: The Cafe
---

### Post by SoftwareExplorer on 2010-02-20
I was following[ [COLOR="DeepSkyBlue"]this tutorial[/COLOR]]("http://janhouse.deviantart.com/art/Gnome-quot-Aero-look-quot-tutorial-142265951") and decided to try to package it.
I put it in a ppa along with other packages that I patched so they work well with transparent Gtk. Here are some screenshots:
[[IMG]http://img26.imageshack.us/img26/4540/rgbagtk.th.png[/IMG]](http://img26.imageshack.us/img26/4540/rgbagtk.png) [[IMG]http://img69.imageshack.us/img69/7495/rgbagtk3.th.png[/IMG]](http://img69.imageshack.us/img69/7495/rgbagtk3.png) [[IMG]http://img651.imageshack.us/img651/1074/rgbagtk2.th.png[/IMG]](http://img651.imageshack.us/img651/1074/rgbagtk2.png)

[[COLOR="DeepSkyBlue"]PPA homepage[/COLOR]]("https://launchpad.net/~erik-b-andersen/+archive/rgba-gtk")

[SIZE="3"][[COLOR="DeepSkyBlue"]Instructions: https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA[/COLOR]]("https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA/").[/SIZE]
Enjoy! :)

[SIZE="2"]Edit:I made a Maverick entry in the PPA, but I haven't had time to test it. So it would be great if someone would tell me if it's working.[/SIZE]

Also, thanks to Aleksey Shaferov who wrote the RGBA module.

---

### Post by juancarlospaco on 2010-02-20
*The method to add the PPA is not correct on the Wiki...*

EDIT: *Wiki edited by me, i hope you agree.*

---

### Post by SoftwareExplorer on 2010-02-20
> **juancarlospaco said:**
> *The method to add the PPA is not correct on the Wiki...*

EDIT: *Wiki edited by me, i hope you agree.*

Thanks, I agree. :)

---

### Post by FuturePilot on 2010-02-20
I've always wondered why the Murrine RGBA stuff makes the shadows disappear from under menus. As you can see in the screenshot there is no shadow under the menu.

---

### Post by VCoolio on 2010-02-20
Nice but since you can only set transparancy values before building I'd rather compile myself. Or has that changed?

---

### Post by NightwishFan on 2010-02-20
If tweaked a bit this could end up making a nice visual effect. I am not very fond of transparency though, so I doubt I would use it unless it is very subtle.

---

### Post by 3rdalbum on 2010-02-20
> **FuturePilot said:**
> I've always wondered why the Murrine RGBA stuff makes the shadows disappear from under menus. As you can see in the screenshot there is no shadow under the menu.

It's a bug in Compiz; it won't draw shadows for RGBA windows. This also explains why there's no shadow behind the Google Chrome window when you don't have native titlebars. (because the round corners of the Google Chrome window are drawn using RGBA)

If you want a composited desktop with shadows behind RGBA windows, you can use gconf-editor to enable compositing in Metacity.

---

### Post by FuturePilot on 2010-02-20
> **3rdalbum said:**
> It's a bug in Compiz; it won't draw shadows for RGBA windows. This also explains why there's no shadow behind the Google Chrome window when you don't have native titlebars. (because the round corners of the Google Chrome window are drawn using RGBA)

If you want a composited desktop with shadows behind RGBA windows, you can use gconf-editor to enable compositing in Metacity.

Ah thanks for that explanation. Solves that mystery for me. :)

---

### Post by SoftwareExplorer on 2010-02-21
> **VCoolio said:**
> Or has that changed?
As far as I know it hasn't. If you want to recompile, you have to modify a few lines near the top of src/support.h if you want to change the opacity.
See [[COLOR="DeepSkyBlue"]http://www.cimitan.com/murrine/node/204[/COLOR]]("http://www.cimitan.com/murrine/node/204")

---

### Post by blacknymph on 2010-02-21
How can I uninstall?

---

### Post by blacknymph on 2010-02-21
I found a way ;

Go Synaptic Package Manager and search "gtk2-engines-murrine"
Select "gtk2-engines-murrine" and Package > Force Version and choosing the previous version of that package.

worked ;)

---

### Post by bluebyt on 2010-02-21
I uninstalled the RGBA PPA, but truecrypt doesn't work  anymore?

error on the terminal:
progname=truecrypt; RGBA=on
The program 'truecrypt' received an X Window System error.

edit:
Now thunderbird refuse to start, same error?
progname=thunderbird-bin; RGBA=on

---

### Post by VCoolio on 2010-02-21
Check if there is a line
```
export GTK_MODULES=rgba
```
in ~/.profile; if yes, delete it or put a '#' in front.

Also, if you uninstall a ppa, you don't uninstall the packages that you previously installed from it.

---

### Post by bluebyt on 2010-02-21
There is no line "export GTK_MODULES=rgba" in the file ~/.profile

I uninstalled the PPA following this instruction:
Go Synaptic Package Manager and search "gtk2-engines-murrine"
Select "gtk2-engines-murrine" and Package > Force Version and choosing the previous version of that package.

But I still have the same errors message :(

---

### Post by SoftwareExplorer on 2010-02-21
(I moved the uninstall instructions to the wiki.)

---

### Post by SoftwareExplorer on 2010-02-21
bluebyt, I didn't see your problem before. 

Press Alt-F2 and run ```
gksudo gedit
```.
Click Open and go to /etc/profile.d/gtkrgba.sh.
In the line that says 
```
export GTK_RGBA_APPS=allbut:firefox:firefox-3.5:gksudo:ooffice:soffice:inkscape:gksu:gtk-recordMyDesktop:kompozer-bin:gpaint:lernid:totem
```, add
```
:thunderbird-bin:truecrypt
```
and save. Re login and I think those programs should work.

I will update the package.
(Edit:The package should be updated now)

---

### Post by bluebyt on 2010-02-21
Thanks SoftwareExplorer, Thunderbird and truecrypt work now.

But If I Mark for removal "gtk2-module-rgba" or "gnome-color-chooser" Synaptic want to remove nautilus, nautilus-desktop, nautilus-share and ubuntu-desktop is that ok?

edit:
Must be a better way that to add a line in the gtkrgba.sh, because now I need to do this for a lot of programs?

---

### Post by SoftwareExplorer on 2010-02-21
> **bluebyt said:**
> Thanks SoftwareExplorer, Thunderbird and truecrypt work now.

But If I Mark for removal "gtk2-module-rgba" or "gnome-color-chooser" Synaptic want to remove nautilus, nautilus-desktop, nautilus-share and ubuntu-desktop is that ok?

I edited the instructions to say to apply the downgrades before you try to remove the other packages. I think that will work. (This should remove Gtk RGBA.)

> **bluebyt said:**
> 
edit:
Must be a better way that to add a line in the gtkrgba.sh, because now I need to do this for a lot of programs?
That last line in gtkrgba.sh works like this:
(all items are separated by a ':')
If the first item is allbut, run all programs with RGBA, except for the ones listed.
If the first item is not allbut, run all the programs listed with RGBA, don't run unlisted programs with rgba.
(This method turns RGBA on or off for each program)

---

### Post by marlonbr on 2010-02-21
Well, want to share my experience with RGBA with everybody.

Installed everything like its suggested, and it worked great. But I had one issue with it: flash player crashed with it. That was the only thing that made me come back. If it was an isolated browser problem, ok, but it was in all browsers, then I gave up.

So, forced previous versions of the ppa's packages, and noticed that  gtk2-module-rgba didn't have a previous version, so I thought: maybe if everything is disabled having it installed may not give any issue. Logged out, logged on, and background image was all black, and changing it did nothing, and flash also didn't work. Tried several stuffs but the only solution was removign the package gtk2-module-rgba.

Resuming: don't forget to remove gtk2-module-rgba.

My opnion: When the RGBA is totally integrated in Ubuntu, it will be a impressive tool that will greatly improve user-interface. I think with it should come a interface with options to set in which gtk-widgets (or whatever the names are) where RGBA will be applicable, giving the power to create stunning interfaces like [[this]]("http://lh3.ggpht.com/_58gbj7FEdro/S4HrN4tugjI/AAAAAAAAAtg/Yw913a3YrVc/s800/banshee%2520rgba%2520mockup1.png") (pic posted by Lucd [[here]]("http://www.omgubuntu.co.uk/2010/02/enable-rgba-window-transparency-in.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Reader")).

Thanks to all people involved in this project. It will certainlly raise the bar on free software all over the world. You make us proud! 8-)

---

### Post by bluebyt on 2010-02-22
I have visual problem with nautilus, How can I get rid of the gray square
upper right? (the throbber icon)

---

### Post by themusicalduck on 2010-02-22
> **marlonbr said:**
> 
Installed everything like its suggested, and it worked great. But I had one issue with it: flash player crashed with it. That was the only thing that made me come back. If it was an isolated browser problem, ok, but it was in all browsers, then I gave up.


Don't know if you're still interested in using it, but I fixed the flash problem by adding "exe" to the export GTK_RGBA_APPS line that SoftwareExplorer mentioned above.

Also, posting a video I made of rgba in action if anyone wants to see [http://www.youtube.com/watch?v=SdI7kVghCTc](http://www.youtube.com/watch?v=SdI7kVghCTc)

and dual monitor version too [http://www.youtube.com/watch?v=P1JysVrvI0g](http://www.youtube.com/watch?v=P1JysVrvI0g)

(dunno which one is better, so meh, uploaded both)

---

### Post by SoftwareExplorer on 2010-02-22
The gray square in nautilus is the background for the animated loading throbber, which isn't transparent (and I'm not sure how to fix that).

---

### Post by 3rdalbum on 2010-02-24
You should add gnome-mplayer to the "allbut" list too. It runs, but videos won't play correctly with Xv or VDPAU.

EDIT: Prism won't work - you'll probably need to add xulrunner-1.9 and xulrunner-1.9.1 and maybe prism to the list.

---

### Post by themusicalduck on 2010-02-24
Also, chrome and chromium don't work properly if they are set to use GTK+ theme. It's fine on classic theme though. prognames google-chrome and chromium-browser.

---

### Post by snkiz on 2010-02-24
Is there a reason that the gtk2-modules-rgba package depends on gnome color chooser and murrine-themes? I already have rgba enabled murrine themes and have no desire to use gnome color chooser to configure my theme, my gtkrc handles that.

---

### Post by snkiz on 2010-02-24
what about chrome isn't working for you? It works as expected with my theme.

---

### Post by snkiz on 2010-02-24
well this is how my theme looks with rgba enabled:

---

### Post by SoftwareExplorer on 2010-02-25
> **snkiz said:**
> Is there a reason that the gtk2-modules-rgba package depends on gnome color chooser and murrine-themes? I already have rgba enabled murrine themes and have no desire to use gnome color chooser to configure my theme, my gtkrc handles that.

I updated the package package to exclude more programs, and to not depend on gnome color chooser or murrine themes.

---

### Post by snkiz on 2010-02-25
Hey thanks a lot friend. I hope you left them as recommends or suggests. I can see how they would be useful to non-themers.

---

### Post by gnomeuser on 2010-02-25
Using current lucid plus the xorg-edgers ppa, this along with compiz now runs on Nouveau on this meager nvidia ION based Acer Aspire Revo r3610.

100% Open Source, it's a thing of blingy pointless beauty.

Not extremely fast though.

---

### Post by SoftwareExplorer on 2010-02-26
> **snkiz said:**
> Hey thanks a lot friend. I hope you left them as recommends or suggests. I can see how they would be useful to non-themers.

You're welcome. I might put them as recommends or suggests next time I decide to update the package.

---

### Post by plun on 2010-02-27
> **gnomeuser said:**
> 
100% Open Source, it's a thing of blingy pointless beauty.



Yup... with my laptop running some ATI crap and everything open source.

Its a beauty..:D   pure "Bling"...:D

[[img]http://ubuntu-pics.de/thumb/44396/snapshot64_1vmz5H.png[/img]](http://ubuntu-pics.de/bild/44396/snapshot64_1vmz5H.png)

;)

---

### Post by MacJack on 2010-02-27
How does one set the opacity levels?

tia

---

### Post by VCoolio on 2010-02-27
> **MacJack said:**
> How does one set the opacity levels?

tia

See [this]("http://ubuntuforums.org/showpost.php?p=8858391&postcount=9")

---

### Post by gnomeuser on 2010-02-27
I have removed everything according to the instructions on the wiki, however something keeps trying to load librgba.so

I see this message when launching any gtk app in a terminal
Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory

I cannot for my life figure out what is doing this, naturally it will fail since the file isn't there anymore but somehow something is still expecting it to be. Additionally while my user sessions gtk apps aren't transparent gksu is, which it is certainly not supposed to be.

---

### Post by snkiz on 2010-02-27
check to make sure rgba.sh has been removed from /etc/profile.d/
it should have been removed but maybe not.

---

### Post by gnomeuser on 2010-02-27
> **snkiz said:**
> check to make sure rgba.sh has been removed from /etc/profile.d/
it should have been removed but maybe not.

and we appear to have a winner:
/etc/profile.d/gtkrgba.sh

---

### Post by snkiz on 2010-02-27
any time :)

---

### Post by SoftwareExplorer on 2010-02-27
> **MacJack said:**
> How does one set the opacity levels?

tia

You have to re build from source the murrine engine. Something like this would be close to what you would have to do, (I might make it more specific later)

Enable source repositories.
sudo apt-get install checkinstall
sudo apt-get build-dep gtk2-engines-murrine
mkdir tempbuild
cd tempbuild
apt-get source gtk2-murrine-engines
ls
(cd into the only folder that exists)
nano src/support.h
(near the top it has a section "/*Opacity Settings*/. Edit the number to whatever you want. 1.00 is fully opaque and 0.00 would be fully transparent)
Ctrl x , y(es) , <enter>
./configure --prefix=/usr/ 
make
sudo checkinstall

I think that will do it.

---

### Post by snkiz on 2010-02-27
How hard would that be to make adjustable from the gtkrc??? I know jack about compiled languages.

---

### Post by SoftwareExplorer on 2010-02-28
> **snkiz said:**
> How hard would that be to make adjustable from the gtkrc??? I know jack about compiled languages.

Well, it has been discussed here [http://www.cimitan.com/murrine/node/204](http://www.cimitan.com/murrine/node/204) , but I don't think anyone has written code that lets you do that. (And doing that is probably beyond what I know how to do). You don't have to know a lot about programming to modify support.h.

---

### Post by SoftwareExplorer on 2010-03-01
> **gnomeuser said:**
> I have removed everything according to the instructions on the wiki, however something keeps trying to load librgba.so

I see this message when launching any gtk app in a terminal
Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory

I cannot for my life figure out what is doing this, naturally it will fail since the file isn't there anymore but somehow something is still expecting it to be. Additionally while my user sessions gtk apps aren't transparent gksu is, which it is certainly not supposed to be.

I think I figured out why that happend: I started installing it like you should a normal file, and because it is in /etc it is assumed a configuration file unless you specify otherwise, which isn't removed unless you purge the configuration files. 

So, do people prefer I leave it as a configuration file or change it to a normal file?
If I leave it as a configuration file, it won't be removed by a normal removal, and people will get the error that gnomeuser got. (But I think if a program was crashing, it won't anymore because it can't load what was crashing it). If they change the file, they will be asked what version of the file they want to use.

If set gtkrgba.sh as a non-configuration file, it will be removed with a normal package removal and people won't get the error gnomeuser got. However, if they edit the package and then the package has an update, their configuration will be overwritten without a warning.

---

### Post by snkiz on 2010-03-01
> **SoftwareExplorer said:**
> I think I figured out why that happend: <snip>

I vote you change it. When I updated the file it was overwritten anyhow since the update was from the same package source, namely you. Along that same idea, when I tried to recompile murrine and reinstall it. I had an error that my package wanted to overwrite another packages configuration file. (murrine something xml) I had to force install my package to overwrite the file.

oh btw
Chromium works with rgba but you have to disable rgba for gtkentry in your theme rc. And you need to add pidgin to the list, it no start with rgba. Or is that just me?

---

### Post by SoftwareExplorer on 2010-03-02
> **snkiz said:**
> I vote you change it. 
Thanks for the input. I'll probably see what a few other people think before I do anything.
> **snkiz said:**
> oh btw
Chromium works with rgba but you have to disable rgba for gtkentry in your theme rc.
I think it will leave it the way it is, but you can put something on the wiki page about it if you want.
> **snkiz said:**
> 
And you need to add pidgin to the list, it no start with rgba. Or is that just me?

I have pidgin 2.6.2-1ubuntu7.2 installed on karmic and it works fine for me. What version are you running?

---

### Post by snkiz on 2010-03-02
My pidgin is up2date maybe its a plugin I have. I have the Facebook plugin from svn or whatever Google code uses. Also the plugins pack from the repos. I have no idea what is causing it, but it definitely gives me the rgba error when I try to run it without the blacklist.

---

### Post by SoftwareExplorer on 2010-03-02
> **snkiz said:**
> My pidgin is up2date maybe its a plugin I have. I have the Facebook plugin from svn or whatever Google code uses. Also the plugins pack from the repos. I have no idea what is causing it, but it definitely gives me the rgba error when I try to run it without the blacklist.

I have also have the pidgin plugin pack installed in karmic, version 2.6.0-0ubuntu1. Maybe that will help narrow it down.

---

### Post by gnomeuser on 2010-03-02
> **SoftwareExplorer said:**
> I think I figured out why that happend: I started installing it like you should a normal file, and because it is in /etc it is assumed a configuration file unless you specify otherwise, which isn't removed unless you purge the configuration files. 

So, do people prefer I leave it as a configuration file or change it to a normal file?
If I leave it as a configuration file, it won't be removed by a normal removal, and people will get the error that gnomeuser got. (But I think if a program was crashing, it won't anymore because it can't load what was crashing it). If they change the file, they will be asked what version of the file they want to use.

If set gtkrgba.sh as a non-configuration file, it will be removed with a normal package removal and people won't get the error gnomeuser got. However, if they edit the package and then the package has an update, their configuration will be overwritten without a warning.

You should remove it on uninstall, otherwise you may cause unwarranted bug reports filed against Ubuntu packages leading to a misallocation of ressources.

---

### Post by ethana2 on 2010-03-28
I installed this from the PPA on Lucid, and while blur works great in the dock and window title bars, it won't do anything for the windows themselves.

Is there some kind of conflict with Gnome GlobalMenu?
[http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

I'd really like to have both, but given a conflict I've got to opt for functionality..

---

### Post by ethana2 on 2010-03-28
There's an option in the global menu applet to enable support for RGBa, I have it checked, and the menu drop downs are properly translucent... but gedit, and all my other gnome apps look normal.

Totem doesn't crash and plays video fine, if that's any kind of clue.  Does this project have an irc channel somewhere?

---

### Post by 3rdalbum on 2010-03-29
> **ethana2 said:**
> There's an option in the global menu applet to enable support for RGBa, I have it checked, and the menu drop downs are properly translucent... but gedit, and all my other gnome apps look normal.

Totem doesn't crash and plays video fine, if that's any kind of clue.  Does this project have an irc channel somewhere?

You need to modify the ~/.profile file and add the following:

```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:openoffice:rhythmbox
```

Add any applications that don't work with RGBA.

Reboot, and assuming you're using a Murrine theme and have Murrine selected as the main engine in Gnome Color Chooser and have RGBA enabled in Gnome Color Chooser you'll get transparency.

---

### Post by SoftwareExplorer on 2010-04-01
> **ethana2 said:**
> There's an option in the global menu applet to enable support for RGBa, I have it checked, and the menu drop downs are properly translucent... but gedit, and all my other gnome apps look normal.

Totem doesn't crash and plays video fine, if that's any kind of clue.  Does this project have an irc channel somewhere?

Did you get it to work?

---

### Post by machinegunkelly on 2010-05-12
Hi I've got  promblems for some applets in the gnome-panel: the tray and the windowapplet. Here's a screenshot

[[IMG]http://upload.centerzone.it/images/70994035536282479015_thumb.jpg[/img]](http://upload.centerzone.it/viewer.php?file=70994035536282479015.png)

Is there a way to fix them?

---

### Post by warrenis1234 on 2010-05-13
> **3rdalbum said:**
> You need to modify the ~/.profile file and add the following:

```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:openoffice:rhythmbox
```

Add any applications that don't work with RGBA.

Reboot, and assuming you're using a Murrine theme and have Murrine selected as the main engine in Gnome Color Chooser and have RGBA enabled in Gnome Color Chooser you'll get transparency.


could adding the panel to this list fix the inconsistent transparency in it?

---

### Post by 3rdalbum on 2010-05-13
> **warrenis1234 said:**
> could adding the panel to this list fix the inconsistent transparency in it?

That would make the whole panel opaque. If that's the kind of fix you're after, then go ahead :-)

---

### Post by xand on 2010-05-17
I had this:
> I can't set a background ! I can see for a short period when I login or logout that my chosen background is there but not when session is active

But after another logout/login (and maybe an extra step which I don't know) it started working :)

---

### Post by frankob on 2010-07-11
> **3rdalbum said:**
> That would make the whole panel opaque. If that's the kind of fix you're after, then go ahead :-)

No, it doesn't... I tried it, as I was having my panel transparent via Compiz, anyway. So I added gnome-panel to the list, the panel was less transparent (I have it set to 90% in Compiz), but the part around the notification area, Tomboy applet and the clock was still darker than the rest of the panel.

I guess it is something with the colors, not with rgba. But why in that specific areas? I don't know...

---

### Post by SoftwareExplorer on 2010-07-11
What I do to make my panels transparent:
I leave RGBA on for panels, and then under Panel Properties on the Background tab, I choose solid color and then adjust the slider until the transparency is right to blend in.

---

### Post by frankob on 2010-07-12
Thank you! That's one solution.

Here is another one I found out:
As I said, I have my panel's trasparency handled by Compiz, but having the panel blacklisted in gktrgba.sh didn't work for me. Instead, in Gnome Color Chooser, under Engines tab I put the panel's engine to be Clearlooks, because I am using a Clearlooks-based theme at the moment. The panel's gtk-rgba support dropped, and Compiz took over. It looks consistent now. :-)

---

### Post by snkiz on 2010-07-12
The problem with the panels is some gtk themes just arn't designed with changing the panel in mind. Some work well others... not so much

---

### Post by frankob on 2010-07-13
> **3rdalbum said:**
> It's a bug in Compiz; it won't draw shadows for RGBA windows. This also explains why there's no shadow behind the Google Chrome window when you don't have native titlebars. (because the round corners of the Google Chrome window are drawn using RGBA)

If you want a composited desktop with shadows behind RGBA windows, you can use gconf-editor to enable compositing in Metacity.

Actually, it is possible under Compiz, too. But you will have to secify what exactly you want to shadow. "any" will not do the trick anymore.

I found out a soulution this evening and posted on this thread: [http://art.ubuntuforums.org/showthread.php?p=9534678](http://art.ubuntuforums.org/showthread.php?p=9534678)

---

### Post by jcullen86 on 2010-07-23
Azureus/Vuse doesn't work with RGBA but i haven't been able to disable it. Added ":Vuze:vuze:azureus:Azureus" to /etc/profile.d/gtkrgba.sh but doesn't work.

It displays this when running from terminal

progname=<unknown>; RGBA=on

Along with alot of window drawing errors
Can post full output if wanted

thanks

---

### Post by snkiz on 2010-07-23
does azureus show up in top or settings manager display? sounds like its not setting a pid properly. Makes it kinda hard to blacklist

---

### Post by jcullen86 on 2010-07-23
With RGBA enabled it just crashes straight away. 
When i disable RGBA it runs fine and shows up in Top and System Monitor as 2 processes, java and azureus.
Both of which I've blacklisted with no luck

---

### Post by jcullen86 on 2010-07-23
Heres the terminal output

---

### Post by snkiz on 2010-07-24
Well I tried it. On my system it just shows up as java, and blacklisting java clearly doesn't work. You could try Java or jvm or JVM, but I don't think that will work either.
```
progname=<unknown>; RGBA=on
```
Is clearly the problem. The system can not identify vuze. Again most likely because it isn't setting a proper pid, witch is a bug that should be filed.

On a side note Vuze is really bloated for what its doing. 110 megs just to fire it up on my system, firefox uses less. You may be better served by another bittorrent program, ie: transmission or deluge. even utorrent through wine would behave better. But if Vuze is what you want it appears you have a decision to make. either way file a bug about the pid. That makes Vuze hard to deal with for many reasons, not just RGBA.

---

### Post by SoftwareExplorer on 2010-07-24
> **snkiz said:**
> 
```
progname=<unknown>; RGBA=on
```
Is clearly the problem. 

Yes, that's the problem. Unfortunately, I don't know if there is a way to block unknown programs. However, you can turn it of for one command like this
```
GTK_RGBA_APPS=gedit <command>
```
This makes it so that for this one command, it goes off a whitelist instead of a blacklist, so anything you might run with this command is automatically blacklisted (except for gedit).
> **snkiz said:**
> On a side note Vuze is really bloated for what its doing. 110 megs just to fire it up on my system, firefox uses less. You may be better served by another bittorrent program, ie: transmission or deluge. even utorrent through wine would behave better. But if Vuze is what you want it appears you have a decision to make. either way file a bug about the pid. That makes Vuze hard to deal with for many reasons, not just RGBA.
I like deluge. :)

---

### Post by jcullen86 on 2010-07-25
Yeah i thought about whitelisting and that looks like the way im gonna have to do it for now 

I haven't been able to find a torrent prog that has the same built in search function that Vuse does

Thanks for the help

---

### Post by .salo on 2010-08-16
About nested error in console after uninstall. 

Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory

I removed the rgba packages (according to wiki) and i don't have the   gkrgba.sh file in profile.d directory. Do you know why can I have this  message?

---

### Post by Frogs Hair on 2010-08-16
PPA Purge:

sudo add-apt-repository ppa:THE_PPA

sudo ppa-purge ppa:<repository-name>/<subdirectory>

---

### Post by SoftwareExplorer on 2010-08-16
> **.salo said:**
> About nested error in console after uninstall. 

Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory

I removed the rgba packages (according to wiki) and i don't have the   gkrgba.sh file in profile.d directory. Do you know why can I have this  message?

It would probably still give you that message until you log out and then back in again, because then the profile.d folder scripts would run again. Also, you could have something in ~/.profile if you modified that manually, but the package doesn't modify that file.

---

### Post by .salo on 2010-08-18
The problem was in ~./profile. I modified it manually (thanks SoftwareExplorer). I deleted the EXPORT lines and problem goes away)

---

### Post by stanca on 2010-08-21
I prefered to compile the gtk2 murrine engine pack from sources,edited the support.h file from extracted murrine folder > src for more transparency and voila': ;) 
 [http://forums.debian.net/viewtopic.php?f=6&t=51651](http://forums.debian.net/viewtopic.php?f=6&t=51651)

---

### Post by snkiz on 2010-08-23
How did you get the transparency in file area of nautilus? Is that a change from git?

---

### Post by stanca on 2010-08-28
No,I use nautilus with background too,added in edit>new backgrounds and emblems>new pattern.:)
Here's a new useful link: 
 [https://launchpad.net/~murrine-daily/+archive/ppa](https://launchpad.net/~murrine-daily/+archive/ppa)

---

### Post by snkiz on 2010-08-28
I have that, broke a few themes on me, namely the new Mavrick theme. Some one told me its actually ahead of Mavrick now. If thats the case I'm surprised Cimi depreciated options he is using in Ubuntu's not yet released themes. Or it could just be a regression.

---

### Post by gsedej on 2010-09-07
Hello!

I have (kind of) important **information**.
I had issue with **adobe flash plugin**. I managed to block it by adding **:exe** in .profile file.
my config:
```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:openoffice:rhythmbox:MonoDevelop:openshot:chromium-browser:exe
```
It works ok in Chromium browser.

Firefox is still problem, because I don't get progname
```
gasper@sirah:~$ firefox 
progname=<unknown>; RGBA=on
NOTE: child process received `Goodbye', closing down
```
Any idea?

I would like to warn others. It is said but to repeat again:
[LIST]
[*]CapitalLetters are important 
[*]you need to logout after changing .profile file
[*]some programs have subproceses like browsers's flash player
[/LIST]



I have question. I think buttons and other controls has problems. Exmaple is ccsm - in main window, background is not transparent but when you mousehover it bocomes transparent, which is not really logical. But when you click on plugin everything becomes transparent and buttons becomes less visible.
Can be this fixes?

---

### Post by Windows Nerd on 2010-09-07
Okay, I got the PPA installed but I cannot find the Gnome Colour Chooser anywhere on my Prefrences menu. Why is this?
Edit: I had to install it. You should mention that you have to do that from a Vanilla Lucid Install in your Wiki. The only thing now is that there is no murrine theme on the controls tab when I select appearance>custimize

Scott

---

### Post by snkiz on 2010-09-07
Or you could try a theme that alreay has rgba enabled, like [mine]("http://gnome-look.org/content/show.php?content=128102&vote=good&tan=69192939")

---

