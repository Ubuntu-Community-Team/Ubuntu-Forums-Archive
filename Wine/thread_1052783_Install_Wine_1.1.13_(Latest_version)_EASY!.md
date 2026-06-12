---
title: "Install Wine 1.1.13 (Latest version) EASY!"
date: 2009-01-28
forum: Wine
---

### Post by benjio on 2009-01-28
OK, MAKE SURE you have any previous Wine installation gone before continuing. I just installed it myself, and wrote this little tutorial to make things easier on the next guy! Enjoy!
Since the latest version isn't available as an install package, you must compile it yourself (trust me, it's not hard!)



First, You will need to make sure you have all of the necessary packages to install. The easiest way is to run a shell script provided by Wine. It's Very easy!
Go Here: [http://wiki.winehq.org/Recommended_Packages]("http://wiki.winehq.org/Recommended_Packages") and find your ubuntu version. Right click on the red link to the right and select 'Save Link As...' . Save it to your desktop.
Next, open your terminal and type 'sudo sh ' then drag that file from your desktop into your terminal window. It should then read something like "sudo sh '/home/yourname/Desktop/install-wine-deps.sh'". Click back into the terminal and press enter, type your password and wait for everything to download and install. Once your terminal finishes all of the action, proceed.

Next you will need the Wine source package. You can get in here: [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449")
Download 'wine-1.1.13.tar.bz2' to your desktop.
When the download completes, right-click on it and select 'extract here'.
Then open your terminal again and type 'cd ' and drag the folder into your terminal window. It shoud read "cd '/home/ben/Desktop/wine-1.1.13'" Click back into your terminal window and press enter.
Now type './configure' (press enter) and wait for this to complete.
When it completes, type 'make depend' (press enter).
When that completes, type 'make' (press enter). This one will take a while.
Once that one finally finishes, type 'sudo make install'.

And that's pretty much it! You can enter 'winecfg' here to easily open the configure screen.

If anyone has anything to add, please post below!

PS: This has only been tested by ME using a fresh 32-bit Ubuntu install!

---

### Post by x33a on 2009-01-28
an easier way is to add this to your sources:

deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) intrepid main

[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

---

### Post by cogadh on 2009-01-28
The latest is available as a DEB package, just follow the Ubuntu instructions on the Wine website:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Those packages are maintained by the same person who maintains the official one in the Ubuntu repositories, so you can trust them to be well made. I believe he also maintains the packages on Launchpad, but AFAIK those are pre-release packages that are not ready for public consumption yet.

---

### Post by YokoZar on 2009-01-28
> **cogadh said:**
> The latest is available as a DEB package, just follow the Ubuntu instructions on the Wine website:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Those packages are maintained by the same person who maintains the official one in the Ubuntu repositories, so you can trust them to be well made. I believe he also maintains the packages on Launchpad, but AFAIK those are pre-release packages that are not ready for public consumption yet.
Yeah seriously.  I mean sometimes it takes me a day or so to get them onto the server after release, but 1.1.13 has been up there for a long time.

I really can't endorse compiling from source like above

---

### Post by Redopz on 2009-01-28
hey im trying to do this i can get this. im mainly interested in the last couple of lines. is that suppose to be whats happening?



matt@matt-desktop:~$ cd'/home/matt/Desktop/wine-1.1.8' 
bash: cd/home/matt/Desktop/wine-1.1.8: No such file or directory
matt@matt-desktop:~$ cd '/home/matt/Desktop/wine-1.1.8' 
matt@matt-desktop:~/Desktop/wine-1.1.8$ ./configure
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
matt@matt-desktop:~/Desktop/wine-1.1.8$ make depend
make: *** No rule to make target `depend'.  Stop.

---

### Post by MasterNetra on 2009-01-28
> **Redopz said:**
> hey im trying to do this i can get this. im mainly interested in the last couple of lines. is that suppose to be whats happening? ...


Just get it out of the repository like any other version. Its been released for 12 days now. I'm sure its there. If you already have wine installed then just update to it (assuming the update hasn't occured already, its mixed in with the other system updates in case you don't know.)

---

### Post by Redopz on 2009-01-28
ok now lets assume i am completely new to ubuntu. how would i go about getting it out of the repository?

---

### Post by SnakeHips on 2009-01-28
> **Redopz said:**
> ok now lets assume i am completely new to ubuntu. how would i go about getting it out of the repository?

Must you have the latest version ?

---

### Post by cogadh on 2009-01-28
> **Redopz said:**
> ok now lets assume i am completely new to ubuntu. how would i go about getting it out of the repository?
I posted a link to instructions in my earlier post above. However, if you don't need the absolute latest (unstable) version of Wine, then all you need to do is install it using Add/Remove Programs in the Applications menu.

---

### Post by Redopz on 2009-01-28
Well ive been trying to get 1.1.8, but i havent figured out how to select which version with the add/remove. I keep getting 1.1.13. Possibly because i have that in a folder somewhere?

---

### Post by albinootje on 2009-01-28
> **benjio said:**
> MAKE SURE you have any previous Wine installation gone before continuing. 

I'd like to add, for your information, that PlayOnLinux can handle various wine versions. See attached screenshot.

[http://www.playonlinux.com/](http://www.playonlinux.com/)

---

### Post by cogadh on 2009-01-28
> **Redopz said:**
> Well ive been trying to get 1.1.8, but i havent figured out how to select which version with the add/remove. I keep getting 1.1.13. Possibly because i have that in a folder somewhere?
It will always offer the most current version, not because you have it downloaded somewhere, but because that is what is on the repository server. If you use Synaptic Package Manager instead of the Add/Remove Programs, you can tell it to force a different version, as long as the version you want is available on that repository server (1.1.8 is available on the server).

Is there a particular reason you are trying to get an out-of-date version?

---

### Post by Redopz on 2009-01-28
ya 1.1.8 had been reported working with the WoW installer. Anyway, ill try the synaptic manger and see what i can do

edit: I figured out how to force 1.0.1, but thats my only other option. I actually had 1.0.1 earlier on this computer to, so again, im not sure if that has something to do with it. this one does however work with the installer, so my problems pretty much solved, but if someone wouldnt mind telling me how to force a different version, thatd be greatly appreciated

---

### Post by cogadh on 2009-01-28
Forcing the version didn't work because I'm an idiot. I forgot you have to manually install the 1.1.8 package, then tell Synaptic to force that version so that it won't prompt you to update to 1.1.13. You can download the 1.1.8 package directly from the [WineHQ DEB Archive]("http://wine.budgetdedicated.com/archive/index.html").

---

### Post by Redopz on 2009-01-28
ah perfect man. Thanks for all the help, and now your my hero.

---

### Post by Meow27 on 2009-01-29
at the dude who is trying to compile wine,
```
sudo apt-get build-dep wine
``` 
but its going to instal alot of programs.....

---

