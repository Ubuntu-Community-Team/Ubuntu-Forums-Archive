---
title: "Could someone help me install Starcraft 2 for Ubuntu?"
date: 2011-06-13
forum: Wine
---

### Post by ilikejellolol on 2011-06-13
I'm not too good at using  Linux, could someone give me step by step instructions on how to install  Starcraft 2 with Wine? I downloaded the installer off from: 
 
[https://us.battle.net/account/management/sc2/dashboard.html](https://us.battle.net/account/management/sc2/dashboard.html) 
 
I ran the installer, and around 20% it said Wine has encountered a problem and needs to close. So I clicked OK, but the downloaded kept going, so I left it. The download took a really long time to finish, so I left it on over night and I just came back to check on it and it's stuck at 98%. The downloader says "closing..." but it's not doing anything.

---

### Post by collisionystm on 2011-06-13
> **ilikejellolol said:**
> I'm not too good at using  Linux, could someone give me step by step instructions on how to install  Starcraft 2 with Wine? I downloaded the installer off from: 
 
[https://us.battle.net/account/management/sc2/dashboard.html](https://us.battle.net/account/management/sc2/dashboard.html) 
 
I ran the installer, and around 20% it said Wine has encountered a problem and needs to close. So I clicked OK, but the downloaded kept going, so I left it. The download took a really long time to finish, so I left it on over night and I just came back to check on it and it's stuck at 98%. The downloader says "closing..." but it's not doing anything.


Have you tried installing 'Play on Linux' from the software center? It is wine but with a few extra features. I believe there is a starcraft 2 installer in it.

---

### Post by pqwoerituytrueiwoq on 2011-06-13
[http://ubuntuforums.org/showthread.php?t=1779722](http://ubuntuforums.org/showthread.php?t=1779722)
another thread same topic

---

### Post by philinux on 2011-06-13
Moved to Wine forum.

---

### Post by ilikejellolol on 2011-06-13
> **collisionystm said:**
> Have you tried installing 'Play on Linux' from the software center? It is wine but with a few extra features. I believe there is a starcraft 2 installer in it.

I installed it and when I run it it says:

One or more programs are missing. Please install them and run the script again.
Program: glxinfo, package: mesa-utils

---

### Post by ilikejellolol on 2011-06-13
> **pqwoerituytrueiwoq said:**
> [http://ubuntuforums.org/showthread.php?t=1779722](http://ubuntuforums.org/showthread.php?t=1779722)
another thread same topic

It says the article is not available for viewing in my country.

______________

So now I got the installer to download, but when I run it, I get this error:

Microsoft Visual C++ Runtime Library

Runtime Error!

Program: C:\users\Vincent...

This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.

---

### Post by desktorp on 2011-06-13
I think this installs the needed runtime.
Winetricks > Install App > vc2005express

---

### Post by ilikejellolol on 2011-06-13
> **desktorp said:**
> I think this installs the needed runtime.
Winetricks > Install App > vc2005express

The installer went through the whole thing and an error came up once it finished:

Note: command '7z x /home/vincent/.cache/winetricks/vc2005express/VC.iso' returned status 127. Aborting.

I have no idea if the installation was successful or not.

---

### Post by desktorp on 2011-06-13
[FONT=monospace]127 is "command not found" so I *think* that means you need 7zip (not 100% sure) .. either check synaptic or do
sudo apt-get install p7zip
[/FONT]

---

### Post by ilikejellolol on 2011-06-13
> **desktorp said:**
> [FONT=monospace]127 is "command not found" so I *think* that means you need 7zip (not 100% sure) .. either check synaptic or do
sudo apt-get install p7zip
[/FONT]

Should I run the installer for vc2005express again after doing this? When I go to Winetricks and scroll back down to it, under status it says "cached".

---

### Post by desktorp on 2011-06-13
Dang bro, I'm not sure.  If I were feigning confidence, I'd say yes, try the installer again because it failed before.  It's probably saying cached, in that it will not have to download it from the resource again, because it just failed to extract it.  I have never encountered a cached entry in Winetricks.  Can you click (right click? any interaction?) the actual part that says "cached" ?.. like does it give you any dialogs regarding what can be done with it?

---

### Post by VeeDubb on 2011-06-13
I know that it's not a popular option around here, but it installs and runs beautifully using crossover gaming from codeweavers.

---

### Post by Dlambert on 2011-06-13
Oil rush is a great linux native RTS similar to Starcraft.

---

### Post by desktorp on 2011-06-13
These suggestions are really helping to get Starcraft 2 running under Wine.
#-o

---

### Post by ilikejellolol on 2011-06-13
> **desktorp said:**
> Dang bro, I'm not sure.  If I were feigning confidence, I'd say yes, try the installer again because it failed before.  It's probably saying cached, in that it will not have to download it from the resource again, because it just failed to extract it.  I have never encountered a cached entry in Winetricks.  Can you click (right click? any interaction?) the actual part that says "cached" ?.. like does it give you any dialogs regarding what can be done with it?

Nah, nothing happens when I right click it. When I try to run it again, I get the same error as before, even after running "[FONT=monospace]sudo apt-get install p7zip".

Also, the installer got to 52% this time instead of 2% before crashing, so we're making progress at least.
[/FONT]

---

### Post by desktorp on 2011-06-13
Are you still getting the 7z error or just the runtime error?  I should have said to just install **p7zip-full** through Synaptic, rather than messing with the terminal.  You may need to dump that cached download and try downloading it again.

---

### Post by ilikejellolol on 2011-06-13
> **desktorp said:**
> Are you still getting the 7z error or just the runtime error?  I should have said to just install **p7zip-full** through Synaptic, rather than messing with the terminal.  If know p7zip is there and are now back to the runtime problem alone, you may need to dump that cached download and try downloading it again.

The 7z error is for when I try to run vc2005express, the runtime error is for when I try to run the SC installer. How do I install p7zip-full through Synaptic?

---

### Post by desktorp on 2011-06-13
You should be able to go to Synaptic and in the search bar, type 7z.  p7zip-full should be in the results.  If it's not there, go to Settings > Repositories .. Other Software tab .. then in this list, make sure Canonical Partners and Independent are checked.  Reload.  Then search again.  I think it should be there, though.

---

### Post by ilikejellolol on 2011-06-13
> **desktorp said:**
> You should be able to go to Synaptic and in the search bar, type 7z.  p7zip-full should be in the results.  If it's not there, go to Settings > Repositories .. Other Software tab .. then in this list, make sure Canonical Partners and Independent are checked.  Reload.  Then search again.  I think it should be there, though.

There we go, finally installed! It's download all of the patches right now, I'll post if I have any problems in game. Thanks for the help.

---

