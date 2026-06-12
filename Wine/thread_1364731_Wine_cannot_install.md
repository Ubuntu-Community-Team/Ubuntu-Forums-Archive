---
title: "Wine cannot install"
date: 2009-12-26
forum: Wine
---

### Post by tahuhali on 2009-12-26
[SIZE=2]I am running a fresh install of Ubuntu 9.10. I wish to install wine but my situation seems odd:

When trying to install using the Ubuntu Software Center, i can find and open the wine page, however there is no response when i click on the "Install" button.

When i attempt an manual download and install from Wine HQ and run the "wineinstall" file i get this in the terminal:[/SIZE]

[SIZE=1]Wine Installer v1.0

Running configure...

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
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

Configure failed, aborting install.[/SIZE]

[SIZE=2]This is the same response when trying to install either Wine 1.0.1 or 1.1.35[/SIZE]
Can anyone help with this?

---

### Post by Babuloseo on 2009-12-26
have you tried installing the beta? I dont have that much knowledge but this should help hopefully....[http://www.winehq.org/download/deb:confused:]("http://www.winehq.org/download/deb")

---

### Post by beastrace91 on 2009-12-26
In terminal run ```
sudo apt-get install wine1.2
``` this will install the latest beta from the default repositories (1.1.35 as of today)

~Jeff

---

### Post by tahuhali on 2009-12-27
Thank you both for responding.

Babuloseo, if you have read more carefully you may noted that i have already tried installing the beta.

beastrace91, that command did in fact work. However it installed 1.1.31 not 1.1.35. do you have any idea why?

---

### Post by beastrace91 on 2009-12-27
> **tahuhali said:**
> However it installed 1.1.31 not 1.1.35. do you have any idea why?

Ah, the beta packages in the Ubuntu repos must still be a few versions behind (not uncommon, personally I compiled all my Wine packages from source so I can install multiple versions - sorry I should have checked what was in the repos)

Running the following commands in terminal *should* remove 1.1.31, add the Wine repositories and then install the latest version for you: ```
sudo apt-get remove wine1.2
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2
```

Have any other questions feel free to ask.

Cheers,
~Jeff

---

### Post by Rosco316 on 2009-12-29
I had the same issue. Worked for me! Thanks soo much!

---

