---
title: "Wine for Linux"
date: 2010-01-25
forum: Wine
---

### Post by chikiwighi on 2010-01-25
I currently have Linux with a dual boot with Windows Vista.

I am trying to use programs via the WINE program on Linux so I can use Windows programs within Linux.

I have no idea how to set the WINE program up so I can use windows programs with it. Ive looked all over the Internet trying to find a help guide but have no look. Am help in using the WINE program would be greatly appreciated.

Thanks in advance

---

### Post by ajgreeny on 2010-01-25
First install wine either from the repositories or get the most up to date version from [winehq]("http://www.winehq.org/download") direct.  Then in terminal enter ```
wine /path/to/windows/install/exe
``` for the program you want to install.  A menu entry should be added for the program you have now installed, and all the files for the prog will be in a hidden folder in your home ~/.wine.

There are some programs which work very well and many which will not run at all, so don't be disappointed if the ones you want will not run.  Also don't forget there may well be a linux alternative to whatever it is you want to use from windows.

---

### Post by dino99 on 2010-01-25
Seriously, if you search "wine ubuntu" with google or else, you will find a lot of doc and howto.

just look here :

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

add this repo to your sources.list and update, that's all, now you can install the latest release with synaptic.

the next step is to "click" on the ".exe" file and wine come to start.

... as easy as  ... :P

---

### Post by SuperSonic4 on 2010-01-25
Wine can be annoying to get working what with deps and all. I'd recommend you look or post for which programs you'd like to have in wine.

For example 
[list]
[*]You've no hope in hell of getting iTunes or WLM to work
[*]utorrent works well but deluge and transmission are better native programs
[*]dvdshrink and EAC work well in wine
[/list]

---

