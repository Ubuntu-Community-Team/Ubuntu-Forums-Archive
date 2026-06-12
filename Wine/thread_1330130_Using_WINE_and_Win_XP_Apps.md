---
title: "Using WINE and Win XP Apps"
date: 2009-11-18
forum: Wine
---

### Post by Ineed2know on 2009-11-18
I am so new to Ubuntu that I have not "gotten out of the hospital diapers" yet. I having Win XP Home installed on my C-Drive with several apps I would like to "attempt" to use on Ubuntu. I installed Ubuntu 9.10 as "dual boot". Using Ubuntu's Software Center under OFFICE, I see "Wine Microsoft Windows Compatibility Layer". When I open it, it refers to version "1.0.1-0ubuntu8 (wine)". So, how do I use WINE? I did have WINE installed but the GUI was **_[COLOR=Red]not[/COLOR]_** finding anything installed under c:\program files\....  where have the majority of the apps installed. So how do I use WINE and get it configured properly? I am not much for the "command line" approach if at all possible. But, I will tackle it if necessary.  Many thanks.

---

### Post by realzippy on 2009-11-18
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by anaconda on 2009-11-18
You need to run the 
winecfg
command before you start using wine.

It will create the .wine folder and the wirtual C: dirve to your home-directory.

---

### Post by Alatar1 on 2009-11-18
The C/program files directory in your windows is NOT the same directory as your /.wine/dosdrives/c_drive/program files, if your looking for these programs you installed via windows in the wine directories they wont be there, it may also help to install them via wine, or browse with wine to the windows partition to run the program.

---

### Post by David_UK on 2009-11-21
Yeah.  I'm new to wine also so I can understand some of your confusion.
As has already been said, wine does not 'know' about any windows software already installed on your windows boot-up (partition).  Software will only appear in this 'virtual' C drive if you use wine to install windows software on your linux boot-up (partition).
However, if you have found out how to access your windows files from within Linux (actually, I think 9.10 will just do that automatically...?) you can navigate to your windows software and try right-clicking on the .exe file - it may well work as normal.  (examples for me were - my organiser, my photo editor and my backup utility.)

Good luck and welcome to Ubuntu!

---

