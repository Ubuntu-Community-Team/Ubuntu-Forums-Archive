---
title: "Wine not getting upgraded"
date: 2009-02-15
forum: Wine
---

### Post by sandy8925 on 2009-02-15
I installed a special wine version for CNC3(the one shown in the wine appdb cnc3 page).

I wanted to remove it and install the later versions. However, after running sudo apt-get upgrade and installing the latest version, when I run:

wine --version

I still get only 1.1.6 and not 1.1.14.

I decided to manually install the latest version and so I found the .deb in the /var/cache/apt/archives folder and installed it again but I still get the same result. Can someone please help me ?

---

### Post by hikaricore on 2009-02-15
If you compiled WINE from source it may not install in the same location as the packaged version.

You will need to goto the source folder you compiled it from and run:

> sudo make uninstall

I suggest you then remove the package you installed and reinstall it once again.
This should clear up your mess.

---

### Post by Dizzle7677 on 2009-02-16
> **sandy8925 said:**
> 
I still get only 1.1.6 and not 1.1.14.

  You could purge the .deb you installed , grab the wine v1.1.15 source and just repeat the instructions on the CNC3 page like you did before. If you did the install per instructions from the CNC3 page you probably did this - "Delete the Wine source with 'cd ..; rm -rf wine-1.1.0'." And hence can't uninstall it. Make sure to leave the directory if you want to uninstall the wine binaries,etc in the future.

  As far as odd versioning reports ,the system is looking for wine where you pointed it look for the wine binary.

---

### Post by Kareeser on 2009-02-17
To download the latest beta release, simply follow the instructions here:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by sandy8925 on 2009-02-17
I didn't compile it from source. There was a .deb readily available so I downloaded that and installed it. Afterwards I uninstalled it and then when I ran:

sudo apt-get install wine

it started installing the latest version i.e 1.1.14 . 
However after that it still says 1.1.6 .

I think it's possible that the latest version is installed and the version is shown wrong by mistake.

---

### Post by sandy8925 on 2009-02-18
I finally found the solution by opening Synaptic Package manager. The wine .deb provided on the Wine AppDB CNC3 page actually installs a hacked version of wine.

I searched for wine in synaptic found a hacks package and removed it. Problem solved!

By the way it was listed as a separate package from wine so when I uninstalled it the original wine was still there but it was the newest version (1.1.14).

Thanks a lot!

---

