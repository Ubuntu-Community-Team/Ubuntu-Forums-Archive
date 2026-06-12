---
title: "Upgrade to Wine 1.3 (yes, I read the FAQ)"
date: 2010-08-05
forum: Wine
---

### Post by namebrandon on 2010-08-05
Long story short.. I have 1.2 installed. It's working, for the most part. Here's what's not working..[INDENT]
[LIST]
[*][SIZE=1]Directx9 installer crashes (I've used winetricks in the meantime, but still, I think the installer should complete, and not crash on me).[/SIZE]
[*][SIZE=1]I cannot run dxdiag. When I run it, nothing happens.[/SIZE]
[/LIST]

[LIST]
[*][SIZE=1]Counter Strike: Source is running veeery slowly under DX9. I've got an NVIDIA 280M GTX, and under the same settings in windows I get ~180fps on the internal benchmark. I get ~ 10 (ten) fps under wine.[/SIZE]
[/LIST]
[/INDENT]ergo, I would like to upgrade to 1.3 and see if that has any effect on my issues. (I've tried troublehsooting the issues individually, and have decided to try 1.3 before digging further).

So.. I go to this web site, per FAQ.. [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

follow the instructions, and run winecfg. It then reports version 1.2.

Do I need to remove 1.2 so that 1.3 will be installed? Is there an apt command line to specify an install of 1.3?

Also, I see point #3 in the FAQ - "***Do not try and install DirectX***". Every CS:S guide tells me otherwise. Anyone have direct experience one way or the other?

_Relevant / misc info.._
[SIZE=1]Ubuntnu (studio) 10.04 x64
NVIDIA 256 drivers
I've used winetricks (I've followed a number of specific guides for Counter Strike)
Core i7 820QM
4GB ram
fakeraid.. (320GB x2 RAID-0 [yes, I know])
1920x1080 @ 24 bit
removed pulse audio, verified sound via alsa
Counter Strike does load, and forcing directx 8 I get ~40-50fps @ 1920x1080[/SIZE]

Thanks. Popcorn for reading.
:popcorn:

---

### Post by cogadh on 2010-08-05
The 1.3 package for Ubuntu is not available yet. If you don't want to wait for the package to be made available, then you can compile 1.3 yourself.

DirectX really never should be installed in Wine, it can and will break Wine's existing DirectX functionality. Every how-to I have come across that tells you to install DX is actually either woefully out of date or used the "shotgun approach" to solve a problem (a game has a problem with a particular DirectX DLL and rather than correct the problem by replacing that specific DLL, install DX and replace dozens of DLLs). Better to just skip that step in your how-to. If you do have DirectX related problems, identify the specific fault and only correct that, rather than "fixing" a bunch of stuff that isn't broken in the first place.

---

### Post by namebrandon on 2010-08-05
> **cogadh said:**
> The 1.3 package for Ubuntu is not available yet. If you don't want to wait for the package to be made available, then you can compile 1.3 yourself.

DirectX really never should be installed in Wine, it can and will break Wine's existing DirectX functionality. Every how-to I have come across that tells you to install DX is actually either woefully out of date or used the "shotgun approach" to solve a problem (a game has a problem with a particular DirectX DLL and rather than correct the problem by replacing that specific DLL, install DX and replace dozens of DLLs). Better to just skip that step in your how-to. If you do have DirectX related problems, identify the specific fault and only correct that, rather than "fixing" a bunch of stuff that isn't broken in the first place.

Thanks for the quick response! You are correct, the shotgun approach was used, and in my case, multiple times at  this point. So much so, that I have no idea what dll's were installed or where. So, being a glutton for punishment, I will remove wine 1.2 and attempt to compile 1.3. 

Can I just rename my 1.2 .wine directory, so that when I install 1.3, I can copy over my steam sub-directory to the new, 1.3 wine directory? I ask, because CS:S takes ~50 minutes to download.

Thanks!

---

### Post by cogadh on 2010-08-05
You can just re-name your .wine directory in your home directory and you will save everything you currently have installed. If you are going to try compiling yourself, make sure you uninstall your currently installed Wine packlage first, it will save you a world of headaches in the future.

---

### Post by cogadh on 2010-08-05
You might want to hold off on that compile, the 1.3 package just became available.

---

### Post by namebrandon on 2010-08-05
Thanks! Pardon the newb question, but any "gotchas" for compiling 1.3? Looks like I need to install all the dependencies (thanks to WineHQ, there's a nice little [script]("http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh") for this).. Grab the tarball.. extract it somewhere.. then 

[FONT=georgia][FONT=georgia][FONT=courier new][FONT=georgia][FONT=courier new]./configure[/FONT][/FONT][FONT=georgia]
make depend && make
sudo make install


[/FONT][/FONT][/FONT][/FONT]And that's it?

---

### Post by namebrandon on 2010-08-05
> **cogadh said:**
> You might want to hold off on that compile, the 1.3 package just became available.

Nice! Thanks for the heads up. 

Newb question time. 

So it should show up in Synatpics after an apt-get update, or do I need to do it by command line?
[I]
Edit - answer from [here ]("http://ubuntuforums.org/showpost.php?p=9681471&postcount=12")

[/I]```
sudo apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mplayer-skins
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  wine1.2
The following NEW packages will be installed
  wine1.3
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
```

---

### Post by cogadh on 2010-08-05
Honestly, its been so long since I actually compiled Wine from source, I couldn't say for certain. As I remember it, the whole process was pretty straightforward, just make sure you pay attention to the output from the configure script. It will tell you if you are missing any particular dependencies or anything (even with that dependency script, errors can happen).

Yup, it will show up in Synaptic, but you don't want the package labeled "wine-dev", you want the one labeled "wine1.3". If you want to do it via the terminal, just run "sudo apt-get install wine1.3"

---

### Post by dardack on 2010-08-05
> **cogadh said:**
> Honestly, its been so long since I actually compiled Wine from source, I couldn't say for certain. As I remember it, the whole process was pretty straightforward, just make sure you pay attention to the output from the configure script. It will tell you if you are missing any particular dependencies or anything (even with that dependency script, errors can happen).

Yup, it will show up in Synaptic, but you don't want the package labeled "wine-dev", you want the one labeled "wine1.3". If you want to do it via the terminal, just run "sudo apt-get install wine1.3"


I compile wine all the time from source (I have a couple modified files, My main one being I hate wines mouse (mimic's windows mouse pointer) so I have it use Ubuntu's mouse pointer), what you need is sudo apt-get build-dep wine, then the:
 ./configure 
make
sudo  make install

Normally, I'll go into my previous compile and do a sudo make uninstall first, or if your compiling first time make sure you do a sudo apt-get remove wine

---

