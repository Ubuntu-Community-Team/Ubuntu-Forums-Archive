---
title: "New Wine runs Photoshop up to CS2"
date: 2008-01-26
forum: The Cafe
---

### Post by jrusso2 on 2008-01-26
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

Running Adobe Photoshop on Wine

Photoshop 5 through CS2 install and works pretty well on wine! Here are some tips you'll need to run it successfully:

    * You shouldn't have to copy Photoshop from Windows; just install it under Wine by running its Setup.exe. (To run a .exe under wine, you have to doubleclick it, right click and choose "Run with Wine", or run it from the commandline using the 'wine' command, depending on how your Linux distribution integrates Wine.)
    * Never use a cracked version of Photoshop.
    * Never run Wine as root.
    * Use a recent version of Wine (latest is 0.9.53).
    *

      Before installing Photoshop, install the Times32 font by downloading and running [http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
    * The Clone tool uses the ALT key in a way that conflicts with many window managers. Here's how to fix that:
          o Ubuntu: System / Windows / Movement Key, and pick "Super" instead of "Alt".
          o Kubuntu: K / System Settings / Look and Feel / Windows / Movement Key, and pick "Super" instead of "Alt"
          o Suse with Gnome: Computer / Control Center / Look and Feel / Windows / Movement Key, and pick "Super" instead of "Alt"
          o

            Suse with KDE: Gecko / Favorites / Configure Desktop / Desktop / Window behavior / Window Actions / "Inner Window, Titlebar & Frame" , and pick "Meta" instead of "Alt"


Known Issues

    * wine-0.9.54 or later is needed to use Photoshop CS2 or pressure-sensitive tablets properly.
    * If installing Photoshop from CD-ROM fails quickly, you might need to install mfc42 by running 'wget kegel.com/wine/winetricks; sh winetricks vcrun6'
    * If you don't have Times32 installed when you first run Photoshop CS2, it will refuse to run ever again, claiming there's a hardware error.
    *

      ImageReady CS/CS2 don't work yet.
    * Bridge CS2 (and therefore File/Browse in Photoshop CS2) doesn't work yet.
    * Photoshop CS3 doesn't even install yet.
    *

      Photoshop Elements 4 and 5 won't work unless you install Microsoft's ODBC (e.g. using winetricks mdac28). One user recommends doing 'wget [http://kegel.com/wine/winetricks;](http://kegel.com/wine/winetricks;) sh winetricks fakeie6 mdac28 jet40' before installing.
    * Photoshop Elements 6 currently doesn't work because the installer doesn't create manifests for MSVCRT assemblies.

---

### Post by mech7 on 2008-01-26
Does it run without any issues.. and what about CS 3 ?

---

### Post by Darkhack on 2008-01-26
> **mech7 said:**
> Does it run without any issues.. and what about CS 3 ?

No and No.

I have nothing against the Wine project but I always sink a little in my seat when I hear people proclaim they are removing their Windows install because application xyz works in Wine.  It's very unstable, feature incomplete, and buggy.  Although I admire their work, I wouldn't suggest that anyone rely on Wine, especially for complex software such as Photoshop or Office.  Applications built for Windows 98 and older are probably the only ones I would have any confidence in, but I still wouldn't rely on them for serious work.

---

### Post by SunnyRabbiera on 2008-01-26
Yeh but wine has already gotten better over the course of one year then they have in three, wine is going to get there sooner or later... sooner by the looks of it as wine is getting to be pretty close to greatness

---

### Post by ACGarib on 2008-01-26
I can't get CS2 to install with the new wine. I mounted the cd and ran setup.exe with wine but I get the following errors: .\AutoPlay\main.ini, MAIN_FILE_VERSION, PRODUCT_REGISTRY_PARENT, and PROJECT_REGISTRY_KEY.

Going to my windows partition and running photoshop.exe with wine will run photoshop, but as soon as it loads, it tells me its not registered and immediately shuts itself off.

It would be cool if I could get photoshop to work in ubuntu because the only reason I boot into vista is because of photoshop.

Any ideas?

All of the other tutorials I see online talk about copying the adobe folder and some registry keys, but according to first post, it seems like that is not necessary.

---

### Post by Acglaphotis on 2008-01-26
That's a shame having to change my precious alt-click just for photoshop, but W00T PHOTOSHOP!

---

### Post by klange on 2008-01-26
I've been using 7 for a while now, which has always worked. Used to be buggy, but they seem to have fixed things over the past few updates that have filtered down into Ubuntu's repos. ImageReady 7 also works, but the toolboxes have not been fixed like in Photoshop (they appear on all workspaces and the fonts are screwy)

I heard CS3 worked, but that it took some time and extra configuration to get it to run properly (and that it doesn't install natively), but that was a while ago so I can't be to sure.

---

### Post by rosegarden78 on 2008-01-26
WINE will run Fireworks 4, Premiere 6 (no Quicktime), Photoshop 6 (full), Flash MX (no Sorenson video input) and Director 8.5 (full) as long as you make a symlink to your Common Files in your .wine directory.  That way you don't have to copy the files twice.

AfterEffects, Illustrator, Maya and higher versions than above will fail, as will Explorer 6 SP1, but if you install Firefox for Windows with WINE you can download streaming HD from ABC.com even though they actively engage in operating system sniffing and blocking.

I assume you can access any Window-only website this way.

---

### Post by mech7 on 2008-01-28
> **ACGarib said:**
> I can't get CS2 to install with the new wine. I mounted the cd and ran setup.exe with wine but I get the following errors: .\AutoPlay\main.ini, MAIN_FILE_VERSION, PRODUCT_REGISTRY_PARENT, and PROJECT_REGISTRY_KEY..

I had the same thing.. what you need to do is go to the photoshop directory, in there is antoerh setup.exe and run that then it works...

Seems to run pretty ok :) Brdige has a few issues though and i some small defects witch compiz.. but then again compiz does not run very great on my ati card.

---

### Post by LightB on 2008-01-28
Ah, no, not good enough. It is still a nuisance and it probably always will be. No, I'm not demanding anything, just saying.

Wine. Such a tragic prince :)

---

### Post by rosegarden78 on 2008-01-28
Guys you should seriously download VirtualBox it runs all that! :KS
[http://ubuntuforums.org/showthread.php?t=679884](http://ubuntuforums.org/showthread.php?t=679884)

---

### Post by SyCo123 on 2008-01-28
I had the same 4 errors and going into the sup folder worked for me too. The trial version of CS2 looks just fine after install.

---

### Post by michaelzap on 2008-02-01
> **SyCo123 said:**
> I had the same 4 errors and going into the sup folder worked for me too. The trial version of CS2 looks just fine after install.

I had the same problem also, and launching setup.exe from the subfolder gave me a setup.ini not found error. Then I renamed the containing directory for the whole thing to something without any funny (foreign) characters and spaces and it installed and runs fine. I still haven't been able to activate it, however.

---

### Post by akiratheoni on 2008-02-01
Wine is great, but I prefer virtualization... I don't play games but I use Photoshop and Office which work perfectly (of course :P). With that said, I still admire the Wine project and what they're doing for us :)

---

### Post by mech7 on 2008-02-01
> **michaelzap said:**
> I had the same problem also, and launching setup.exe from the subfolder gave me a setup.ini not found error. Then I renamed the containing directory for the whole thing to something without any funny (foreign) characters and spaces and it installed and runs fine. I still haven't been able to activate it, however.

Have you tried phone activiation worked fine by me ?

---

### Post by michaelzap on 2008-02-01
When I try to activate by phone, I get an error message that there's not enough disk space to continue and the activation wizard quits (I have at least 150 GB free on that drive)...

---

### Post by mech7 on 2008-02-01
> **michaelzap said:**
> When I try to activate by phone, I get an error message that there's not enough disk space to continue and the activation wizard quits (I have at least 150 GB free on that drive)...

Umm with me it failed at making a connection over internet plrobably because of wine... then the phone came up automatically and worked fine :)

---

### Post by Victormd on 2008-02-01
> **rosegarden78 said:**
> Guys you should seriously download VirtualBox it runs all that! :KS
[http://ubuntuforums.org/showthread.php?t=679884](http://ubuntuforums.org/showthread.php?t=679884)

Though performance-wise Wine is a better alternative, I agree with rosegarden78! I struggled with Wine for a few weeks and ended up moving to VirtualBox... Because it's a virtual installation of Windows, it will run all softz with no problem! BUT, if you play games... VirtualBox is not the way to go...

---

### Post by rosegarden78 on 2008-02-18
VirtualBox has limitations (no winmodem, no fax, usb direct connect, no games) I discovered but since maxing out my RAM (1024MB + 256 MB on board) to 1.280 GB it all works better especially video. The advantages of seamless integration with mouse, Wacom and Cellwriter combined with shared folders give me no reason to dual-boot.  All it seem to run faster on one partition anyway.

---

### Post by dankegel on 2008-03-03
> **ACGarib said:**
> I can't get CS2 to install with the new wine. I mounted the cd and ran setup.exe with wine but I get the following errors: .\AutoPlay\main.ini, MAIN_FILE_VERSION, PRODUCT_REGISTRY_PARENT, and PROJECT_REGISTRY_KEY.


That means the current directory was wrong.  You have to do
something like

cd /media/cdrom
wine setup.exe

The Adobe installer is very picky, won't work if you're not in
its directory.

---

### Post by michaelzap on 2008-03-03
I had this problem when I had copied the installer into a folder with spaces and accented characters in the name, and renaming it to something simpler allowed me to install.

---

### Post by Jim_1981 on 2009-02-06
> **jrusso2 said:**
> o Kubuntu: K / System Settings / Look and Feel / Windows / Movement Key, and pick "Super" instead of "Alt"

I can confirm that the tutorial works on intrepid with KDE 4 however this step needs to be modified slightly

K menu >> System Settings >> Look and Feel >> Window Behaviour >> Window Actions >> Modifier Key change from Alt to Meta.

PS, is it possible to get Adobe Bridge to work under Linux? When I try to run it it says I need to have other Adobe apps installed to use it. Is there an issue with the wine registry or something?

---

