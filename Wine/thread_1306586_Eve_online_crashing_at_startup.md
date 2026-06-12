---
title: "Eve online crashing at startup"
date: 2009-10-30
forum: Wine
---

### Post by diggedy on 2009-10-30
Since I upgraded the kernel in 9.04 (cant remember which but it was the most recent) eveonline now exits during the splash screen. Ive upgraded to karmic and the fault still persists, on an old installation of ubuntu everything is fine.
I know theres a bug open for it at wine HQ but its not very active so im wondering if anyone reading these forums has encountered it and found a workaround?

---

### Post by beastrace91 on 2009-10-31
What Wine version? What graphics card? What graphics card driver version? What is the out put in terminal when the program crashes out?

Also you upgraded your system from 9.04 to 9.10 or you did a clean install?

Help us, help you,
~Jeff

---

### Post by t.rei on 2009-11-09
I encountered the same problem, and found that deleting the config (settings folder) in:
```
~/.wine/drive_c/windows/profiles/XXXXX/Lokale Einstellungen/Anwendungsdaten/CCP/EVE/c_programme_ccp_eve_tranquility/
```lets eve start up. Then again this is not really practicable.

**edit* XXXXX = your username*

One hint, I was not able to test this morning before going to work, was to jus set the "bitsCancelled=0" in the prefs.ini in the mentioned settings folder to 0 (it will be set to 1 after each time eve is run) should do th trick. I don't know yet, I hope to get it working when I go home.

Running karmic kubuntu and wine-1.1.32

---

### Post by t.rei on 2009-11-09
Editing that line in prefs.ini did **not** work for me.

What did work, was installing the latest of these: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

me is a happy (gate)camper and 'roid-murderer and collector of damsels in distress again.

karmic koala
nvidia-drivers: NVIDIA-Linux-x86-190.42-pkg1.run
```
$ uname -r
2.6.32-020632rc6-generic
$ wine --version
wine-1.1.32-402-gde00535

```

---

### Post by diggedy on 2009-11-30
> **t.rei said:**
> Editing that line in prefs.ini did **not** work for me.

What did work, was installing the latest of these: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

me is a happy (gate)camper and 'roid-murderer and collector of damsels in distress again.

karmic koala
nvidia-drivers: NVIDIA-Linux-x86-190.42-pkg1.run
```
$ uname -r
2.6.32-020632rc6-generic
$ wine --version
wine-1.1.32-402-gde00535

```

ive had success with editing the prefs file but it makes me cry having to do that each time. Gonna try the kernel upgrade and see how that works out. thanks

Jeff, my apologies for not including the details, I just assumed with it being a documented bug that I wouldnt need to include my details.

---

### Post by PariahVayne on 2009-11-30
I have to start it from Terminal, works every time then.

---

### Post by diggedy on 2009-11-30
> **PariahVayne said:**
> I have to start it from Terminal, works every time then.

Ive had no luck upgrading the kernel, its playing havoc with the graphics settings and wont let me run without being in low graphics mode. 

Forgive me for being nubish, how do I run it from terminal? Im not very good with terminal commands

---

### Post by PariahVayne on 2009-11-30
x

---

### Post by diggedy on 2009-11-30
it was the kernel upgrade which was giving me problems. no harm done though, just reverted to the original kernel.

how do you run eve from temrinal though

---

### Post by PariahVayne on 2009-11-30
x

---

### Post by diggedy on 2009-11-30
I switch between the two actually but mainly ubuntu. I run them from playonlinux

---

### Post by diggedy on 2009-12-01
Ive managed to get the kernel upgrade applied successfully and its worked. Thanks for that tip

---

### Post by airtonix on 2009-12-21
Removing the settings folder worked for me. 

since i installed my copy of eve in ~/Games/Eve (and H: is mapped to my home folder) the place my settings was located was : 
```

/home/<your-username>/.wine/drive_c/users/<your-username>/Local Settings/Application Data/CCP/EVE/h_games_eve_tranquility

```

But I'm back to the problem of missing fonts, probably an unrelated issue.

---

### Post by ericbjones on 2013-02-24
> **diggedy said:**
> it was the kernel upgrade which was giving me problems. no harm done though, just reverted to the original kernel.

how do you run eve from temrinal though

here is an example of writing a script to launch eve via terminal (launches in an emulated virtual desktop.)

cd to the directory you would like to store this script.  create a new file called eve.bash
you can do this using vi editor
```

#!/bin/bash      
WINE=wine
$WINE explorer /desktop=eveA,1920x1080 "c:\program files\ccp\eve\eve.exe"

```give the file execution rights 
```

chmod +x eve.bash

```run the file to test it 
```

./eve.bash

```

---

