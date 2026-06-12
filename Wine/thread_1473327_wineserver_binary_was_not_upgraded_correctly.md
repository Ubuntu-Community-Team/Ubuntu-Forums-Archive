---
title: "wineserver binary was not upgraded correctly"
date: 2010-05-05
forum: Wine
---

### Post by ninja senses on 2010-05-05
So I have been messing with wine trying to get it to run a game and also upgraded to lynx recently...somewhere along the way I messed up wine to the point of it not working, here is the error I get:

$ winecfg
wine client error:0: version mismatch 0/398.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

I can get the wine cfg to work if I goto the synaptic package manager and get get wine 1.0, but when i try and get the later versions i am not successful...any help?

---

### Post by hikaricore on 2010-05-05
Did you at any point try to install wine from source?
This could cause issues if you later installed it from a package without first removing the source install.

---

### Post by Bachstelze on 2010-05-05
Also make sure you have closed all your WINE programs. If a WINE program is still running, you will still have the old wineserver running, hence the error message.

---

### Post by YokoZar on 2010-05-06
> **Bachstelze said:**
> Also make sure you have closed all your WINE programs. If a WINE program is still running, you will still have the old wineserver running, hence the error message.

This is correct.  You need to close all running Wine programs every time you update Wine.

You can do this forcefully by typing wineserver -k on the console.

---

### Post by ninja senses on 2010-05-07
> **hikaricore said:**
> Did you at any point try to install wine from source?
This could cause issues if you later installed it from a package without first removing the source install.

yes I did...how can i completley remove it and reinstall to get it working again?

---

### Post by cogadh on 2010-05-07
Usually you just have to go into your source directory and run "make uninstall":
[http://www.winehq.org/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE](http://www.winehq.org/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE)

---

### Post by ninja senses on 2010-05-12
> **cogadh said:**
> Usually you just have to go into your source directory and run "make uninstall":
[http://www.winehq.org/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE](http://www.winehq.org/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE)

I was trying to follow this write up [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)

but I dont know what the source directory is...can anyone help?

---

### Post by hikaricore on 2010-05-12
If you deleted the source or can't find it, just download it again then run:

make uninstall

Then remove any currently installed wine packages and reinstall them.

---

### Post by dino99 on 2010-05-12
> **ninja senses said:**
> I was trying to follow this write up [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)

but I dont know what the source directory is...can anyone help?

goto your /home/.wine, save what you want to, then remove .wine

update your synaptic repo with: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

update and install wine1.2 and winetricks

then open wine menu and run winecfg

maybe your app need you make some install with winetricks (see [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true))

---

### Post by cogadh on 2010-05-12
> **ninja senses said:**
> I was trying to follow this write up [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)

but I dont know what the source directory is...can anyone help?
The source directory is whatever directory you had Wine's source code in when you built it. It where you did all your compiling work.


> **dino99 said:**
> goto your /home/.wine, save what you want to, then remove .wine

update your synaptic repo with: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

update and install wine1.2 and winetricks

then open wine menu and run winecfg

maybe your app need you make some install with winetricks (see [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true))
That's not going to fix his problem. He's trying to remove a self-compiled version of Wine he had already installed.

---

### Post by ninja senses on 2010-07-31
i have tried all th above steps to no luck..any other suggestions?

---

