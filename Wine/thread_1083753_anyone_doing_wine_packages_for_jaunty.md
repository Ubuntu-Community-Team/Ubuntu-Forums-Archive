---
title: "anyone doing wine packages for jaunty?"
date: 2009-03-01
forum: Wine
---

### Post by Yeeha on 2009-03-01
Title says it all.

---

### Post by kvarley on 2009-03-01
Wine packages? You mean can you install wine in jaunty?

If that's what you mean yeah.

---

### Post by Yeeha on 2009-03-01
i mean if someone has made packages of latest wine 1.1.16 for ubuntu jaunty, wine in jaunty repositoryes is still 1.0 and compiling from sources is bit tedious with wine. Although i could use debs at winehq that are meant of 8.10 but i fear it might be problematic as there is new Xserver and so on.

---

### Post by Meow27 on 2009-03-01
ok you are going to have to do this

open up a terminal and type ```
sudo apt-get build-dep wine
```

while you are downloading these dependencies, you will need to download the source code for wine [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=664595](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=664595)

after you are done with installing the dependencies in the terminal, open up a new one (you should extract the wine source in as the folder in your home folder)

in the terminal type ```
cd wine1.1.6
``` or whatever the folder is

then type /.configure

this will take ~3 minutes

after that you will need to do ```
make
```
which can take 1-3 hours, depending on you cpu

after that is completed, do ```
sudo make install
```


just make sure you uninstalled your older version of wine just in case

---

### Post by DigitaLink on 2009-03-01
Yeah, I have jaunty installed, and it's running great, but I'm not compiling the latest wine on my old Sempron.  That's just torture.  Unfortunately the old 1.0.1 version won't run Photoshop CS2 for me like 1.1.17 does on Intrepid.  It's a deal breaker for me.  As much as there are good RAW photo editing apps that are linux-native, none of them seem to work as quickly and easily as PS.

Soooooooooooooooooo I'll just have to leave jaunty alone for now.  I've installed some half-dozen distros this weekend, seeing what will be next for my machine, from jaunty to fedora 10/11 to PCLOS Gnome to SimplyMepis 8 to elive-testing.  (Cool, but I've built a good workflow with Gnome.)  

None of them have outshone Intrepid so far, even though I think my old install that's been upgraded since Dapper has a lot of cruft in it.  Xorg regularly needs re-starting because it starts chewing CPU cycles (60-70%) for no apparent reason.  So while I've been looking for a distro that outshines it and will make me switch/update ... not yet, even though Jaunty is looking really good so far.

---

### Post by Yeeha on 2009-03-02
Heh last time when i tryed to compile it i seeked out dependencies by running configure and installing dependencies 1 by 1 :D. sudo apt-get build-dep wine makes it much much easyer thx for the tip.

---

### Post by Gabbegubben on 2009-03-10
If anyone is interested, I have wine-1.1.16 packages for Jaunty in my PPA.

[https://launchpad.net/~gabriel-thornblad/+archive/ppa](https://launchpad.net/~gabriel-thornblad/+archive/ppa)

---

### Post by altonbr on 2009-03-15
Here's the [WineHQ archive for Ubuntu ]("http://wine.budgetdedicated.com/archive/index.html"). The Intrepid 8.10 binaries seem to work for me fine on Jaunty.

---

### Post by oliwally on 2009-05-03
> **Meow27 said:**
> ok you are going to have to do this

open up a terminal and type ```
sudo apt-get build-dep wine
```

while you are downloading these dependencies, you will need to download the source code for wine [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=664595](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=664595)

after you are done with installing the dependencies in the terminal, open up a new one (you should extract the wine source in as the folder in your home folder)

in the terminal type ```
cd wine1.1.6
``` or whatever the folder is

then type /.configure

this will take ~3 minutes

after that you will need to do ```
make
```
which can take 1-3 hours, depending on you cpu

after that is completed, do ```
sudo make install
```


just make sure you uninstalled your older version of wine just in case

Sorry, but I'm not that clued up with the various commands in Linux. What is this difference between this and installing wine with synaptic or similar?

---

### Post by cogadh on 2009-05-03
> **oliwally said:**
> Sorry, but I'm not that clued up with the various commands in Linux. What is this difference between this and installing wine with synaptic or similar?
Those commands allow you to download the latest Wine source code and compile it into binary (executable) form yourself, then install it. With Synaptic, you are installing a pre-compiled binary package, which is generally much easier for the average user. TBH, most people should never have a need to compile Wine themselves.

If you want to get the latest Wine instead of the version that is in the default Ubuntu repositories without having to compile it yourself, follow the instructions here:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by oliwally on 2009-05-03
Great  - thanks cogadh! Makes good sense.

If I wanted to uninstall once wine had been compiled the way described above, what would be the commands for that?

Is there any disadvantage to using synaptic to install wine (other than not getting the latest version)?

---

### Post by cogadh on 2009-05-04
For uninstalling a self-compiled version, all you (should) have to do is open a terminal, change directories to where you have the Wine sources stored, then type "make uninstall".

Synaptic is just an application that is used to install pre-compiled software packages from different software repositories. It is not restricted to only giving you the older, stable version of Wine, if you add the WineHQ repository as described in that link from my last post. There are no real disadvantages to using it and there are plenty of advantages, like easy install/uninstall, automatic updates, guaranteed compatibility and dependencies, proper integration into the GUI, etc.

---

### Post by Meow27 on 2009-05-04
i made the compilation guide since there were no available packages for jaunty at the time

but if you have an option between the official packages and compiling, you should choose the packages since they have everything set up the way its needed

---

### Post by starscalling on 2009-07-03
> **altonbr said:**
> Here's the [WineHQ archive for Ubuntu ]("http://wine.budgetdedicated.com/archive/index.html"). The Intrepid 8.10 binaries seem to work for me fine on Jaunty.

+rep :guitar:

---

