---
title: "Trouble with WIne"
date: 2010-07-18
forum: Wine
---

### Post by Nick_Jinn on 2010-07-18
[http://www.youtube.com/watch?v=wGxA6-dGOmc](http://www.youtube.com/watch?v=wGxA6-dGOmc)


So I am having trouble with WINE. Its not working right. I cant get Oblivion or Fallout 3 to work right, and I had them both working on my older and slower computer on a previous version of Ubuntu.

I am using Mint by the way. I hope there are no downstream issues. 

The games crash sometimes talking about dll something that I missed and didnt copy, or says there may be a deficiency in wine.


> sudo apt-get install wine1.2
[sudo] password for djinn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit  status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on tetex-bin | texlive-base-bin | latex; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not  configured yet.
  Package latex is not installed.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a  followup error from a previous failure.
               No apport report written because the error message  indicates its a followup error from a previous failure.
                              Errors were encountered while processing:
 tex-common
 texlive-binaries
 winefish
E: Sub-process /usr/bin/dpkg returned an error code (1) 			 		

Anyone know how to do the scrolling quote thing?

---

### Post by asdfoo on 2010-07-18
I replied in the other thread you posted the exact same message in.

The command you've posted says wine is already installed, all those errors are problems with tex related programs - unrelated to Wine.

Perhaps you could start by explaining how you start the program and what happens when you do.

---

### Post by Nick_Jinn on 2010-07-18
Whenever I go to install a game on playonlinux I get to where it loads the game option and I click on it....without fail it will freeze. I stop it with the app killer, and as soon as I kill the app another windows successfully pops up and starts the installation process. It finishes ok usually.

Then I go to Wine, Programs, Bethesda then Fallout or Oblivion then their launchers.

For a minute I was able to load Oblivion without sound....now nothing this time.

Fallout 3 without fail crashes at startup. I get past the fist screen when I hit play then it says there is a serious problem and has to close and it may be due to a deficiency in wine (or wine related tools).

---

