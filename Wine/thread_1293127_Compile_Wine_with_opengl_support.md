---
title: "Compile Wine with opengl support"
date: 2009-10-16
forum: Wine
---

### Post by Jaraxle on 2009-10-16
Hi all,

I am trying to get Half Life and some other games to work and am following the instructions given here:

[http://lhl.linuxgames.com/howto/half-life-HOWTO-0.5.html](http://lhl.linuxgames.com/howto/half-life-HOWTO-0.5.html)

I was able to download the latest src for Wine, extract it, and run ./configure. However, the instructions specify using the following command:

```
./configure --enable-opengl

```

Whenever I try this I receive the following error message:

```
configure: WARNING: unrecognized options: --enable-opengl

```

Can anyone confirm that this is a valid command? I've searched on Google and none of the sites were clear about this. It seems that it should be a valid option to use as the author of the HOWTO simply stated to download and extract the Wine source, then use that option with the configure file.

Just in case it helps, I will place the rest of the terminal output below. Thanks in advance for any help you can give. This forum is a wealth of information! 

Output from ./configure --enable-opengl:

```
configure: WARNING: unrecognized options: --enable-opengl
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for cpp... cpp
checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

```

---

### Post by Jaraxle on 2009-10-16
I just noticed that I was missing many things so I ran apt-get install build-essential but the command still does not work.

Thanks again for any help you can give.

---

### Post by hikaricore on 2009-10-16
Uhh.... WINE already has opengl support by default.
You're using a 7 year old guide to compile modern WINE?

> [B][COLOR="DarkRed"]HOWTO run Half-Life using WINE

_Version 0.5, September 23rd 2002_[/COLOR][/B]

Me thinks you need to just goto the AppDB and look for more recent instuctions.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8)

---

### Post by Jaraxle on 2009-10-16
Doh! I never even thought of that. I knew the guide was a bit outdated but thought it would help me get opengl support for games. Like I said, I never even thought modern Wine would already have support!

Thanks for helping me again, hikaricore.

---

