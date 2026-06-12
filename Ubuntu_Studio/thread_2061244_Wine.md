---
title: "Wine???"
date: 2012-09-22
forum: Ubuntu Studio
---

### Post by JXR on 2012-09-22
The first program I want to install on UStudio is a program called TablEdit, a music notation program that allows one to notate in standard notation and tablature.
 
I expected it would run in UStudio but when I go to the TablEdit page regarding Linux it says: > **TablEdit on Linux, it works!** At this time there are no plans for a Linux version of TablEdit due to the fact that TablEdit runs fine under WINE emulation
 
So I go to the WineHQ forum and cannot find anything that clearly explains what WINE is (aside from some sort of emulation program that allows Linux users to run Windows programs?) the relationship of Wine to UbuntuStudio or detailed plans how to install on UStudio.
I also reviewed threads in this forum (notably How-To FL Studio 9 in Ubuntu (using Wine)) and discover immediately that > you should know that the installation method depends on your Ubuntu version
 
Are Wine and UbuntuStudio compatible?
Am I asking for trouble in trying to install Wine?
If not, where can I find detailed instructions on how to install Wine on UStudio?
 
Thanks

---

### Post by coldraven on 2012-09-22
I don't know what version you are using but you will have either a "Software Centre" or "Synaptic package Manager" or both already installed in your system.
Run one of them and search for wine. Mark it for install and click "Apply".
That's it!

---

### Post by jejeman on 2012-09-22
Try to use Linux native programs for notation. Like MuseScore or Lilypond.

---

### Post by sgx on 2012-09-22
> **JXR said:**
> 
Are Wine and UbuntuStudio compatible?
Am I asking for trouble in trying to install Wine?
If not, where can I find detailed instructions on how to install Wine on UStudio?
 
Thanks
Hi, wine works in probably any distro. You can install it from synaptic. The first time you run it, a /home/you/.wine folder
will be created, holding the windows api system, dontaing
the typical Program Files folders. C:\ is now the folder

/home/you/.wine/drive_c

Some choices can be made, use command  winecfg  to open a settings panel.

windows apps are installed by command:

wine reaper425_x64-install.exe

To launch apps, there may be an icon, or you can use the
wine command, and account for windows path and naming differences
by replacing spaces with a *   or by quoting the entire path, and
you can use symbolic links from .wine to /home/you to simplify
things. Commands

wine /home/you/.wine/drive_c/Program*Files/IK*Multimedia/AmpliTube*3/AmpliTube*3.exe  or

wine "/home/you/.wine/drive_c/Program Files/IK Multimedia/AmpliTube 3/AmpliTube 3.exe"

windows vst plugins are best handled by installing Reaper,
or a linux app called Festige.

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

there is a wine repository, with a howto to at the link, to add the wine repository to synaptic. You can also click the
'View package details' link, and download and install the needed packages manually using

sudo dpkg -i name.deb

Cheers

---

### Post by JXR on 2012-09-23
Searched for "wine" in Synaptic Package Manager and got the following:
 
gnome colors
gnome-exe-thumbnailer
gnome-wine-icon-theme
libkwindffects1abi3
playonlinux
pptview
q4wine
shiki-colors
shiki-wine-theme
tellico
tellico-data
tellico-scripts
unmass
wine
wine-geco 1.4
wine1.2
wine1.3
wine1.4
wine1.4-common
wine1.4-dbg
wine1.4-dev
wine1.4-i386
winefish
winetricks
(phew!)
 
There is a description to each of these, but it's not that helpful.
 
*My purpose in wanting to install Wine is for sound editing (notation and playback) and realtime sound production (realtime looping) applications.*
 
Which do I need to install?

---

### Post by sectio aurea on 2012-09-23
Install the "wine" package unless you find an application doesn't work in the version of Wine provided. If that happens, you can look at the Wine project PPA for a chance at a newer development version.

---

### Post by JXR on 2012-09-23
All of the above are wine packages (I think)
 
Are you suggesting I install wine 1.4 since this seems to be the latest version?
 
I assume -dev = developer  and -dbg = debug  are versions I don't want to be messing with...
 
Should I install "wine1.4" (Binary Emulator and Library) or "wine1.4-common" (transitional package)

---

### Post by jejeman on 2012-09-23
Install wine1.4, that is the main package. The rest will follow automaticly.

And good luck running win apps on linux.

---

### Post by sgx on 2012-09-24
> **JXR said:**
> All of the above are wine packages (I think)
 
Are you suggesting I install wine 1.4 since this seems to be the latest version?
 
I assume -dev = developer  and -dbg = debug  are versions I don't want to be messing with...
 
Should I install "wine1.4" (Binary Emulator and Library) or "wine1.4-common" (transitional package)
Before you go too far, you should verify your soundcard and printer
will be linux compatible, or be prepared to sell or trade them
as needed. Having an nvidia video card will also help, as their
support has had a head start compared to ati. A little google search
with name, brand, alsa, and ubuntu, should reveal all.

maudio audiophile pci alsa ubuntu    etc
Cheers

---

