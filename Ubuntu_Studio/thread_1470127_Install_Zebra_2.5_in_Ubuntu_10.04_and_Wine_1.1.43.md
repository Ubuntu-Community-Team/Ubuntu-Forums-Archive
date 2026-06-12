---
title: "Install Zebra 2.5 in Ubuntu 10.04 and Wine 1.1.43"
date: 2010-05-02
forum: Ubuntu Studio
---

### Post by billstei on 2010-05-02
Shameless plug section:
I consider Zebra ( [http://www.u-he.com/zebra](http://www.u-he.com/zebra) ) to be one of the best soft synths that money can buy, and being able to run it in Linux makes it even better. =D>

Minor shame section:
I'm not sure which programs have the bugs, but since it was a bit tricky to install Zebra 2.5 I thought I would record here how I did it (in Ubuntu 10.04, and Wine 1.1.43):

1) In winecfg remove drive Z: (which points to / )
2) Put the installer file "Zebra V2.5 Winstaller.exe" in C:\windows\system32
3) Rename the installer to Zebra_V2.5_Winstaller.exe (i.e. remove spaces.  Probably don't need to do this, but otherwise use quotes around the name.)
4) Using the console in the system32 directory run: wine Zebra_V2.5_Winstaller.exe (use default options for VSTPlugins, etc.)
5) Remove installer from system32.  In winecfg put (Add) drive Z: back as /
6) Put Lucida Sans Unicode font (or a link to it) in the C:\windows\Fonts directory.  This file is named L_10646.ttf in Windows XP.  Zebra is supposed to do a proper fallback if this font is missing but it's not working at this time/version.

I use FL Studio 9.1 (also running under Wine) as a host for Zebra.  See this thread for help installing FL Studio: [http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057)

---

### Post by sgx on 2010-05-02
Hi, I have the 2.2 zebra demo, and Zebra CM, and never modified or removed anything, except to add some .dlls that were not in earlier wine releases

gdiplus
mfc42
mfc71
msvcp60
msvcp71
msvcr71
msvcr80
mscvsc60
msvcp90
msvcr90

I just run the 2.2 installer from /home/user$
I fill blank spaces in wine commandlines with a * 
Its great that you have it working, its world class!. 
I'll test the newest one tonite!

Try phasex when you get a chance, its an amazing unknown linux synth, even whats jamming on the line-in of your soundcard can be a sound source! 
Cheers

---

### Post by billstei on 2010-05-02
sgx - the 2.5 installer has some kind of data migration stuff in it that the earlier installers did not, even as late as 2.5 beta 7 did not have this, so I think that the "bug" might be there.  What it seems to be doing is trying to create a "Program Files" directory on Z:, which isn't possible when Z: points to root (and running as root is a very bad idea).  It's obviously confused, unless this is a Wine bug, which I doubt.

As far as that dll list goes, the only one I have (added) is mfc42.dll, and I don't think Zebra uses it (?) -- I have it primarily for the Wasp synth in FL Studio.

---

### Post by sgx on 2010-05-03
I tried the installer, and it asked the data-migration question, but it confirmed it would migrate the data to the location where I chose to install Zebra, which was in C: so all was smooth sailing. Maybe Urs
fiddled with the installer recently and sorted some things out. The
man just hates those bug reports :D

---

