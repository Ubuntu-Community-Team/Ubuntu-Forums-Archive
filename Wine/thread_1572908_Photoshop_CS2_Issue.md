---
title: "Photoshop CS2 Issue"
date: 2010-09-11
forum: Wine
---

### Post by Autokrat on 2010-09-11
I just upgraded from 10.04 to the 10.10 beta and everything is more or less running fine except one of my Wine programs.
 

 I was running Adobe Photoshop CS2 in Wine 1.2 with Winetricks installed and Windows True Type fonts and it ran fine with no problems. When I upgraded to 10.10, I received this error:
 

 > “An error has been detected with a required application library and the product cannot continue. Please reinstall the application.” Photoshop installed fine and I can start it up, but every time I do, a few seconds later that error message comes up.
 

 I tried simply removing Wine and reinstalling everything, but got the same error message as before. Then I installed the Wine 1.3 beta and tried that and got the same message.
 

 Am I missing something here? Right now I'm stuck and have hit a dead end.
  

The problem didn't happen until I upgraded to 10.10, which in retrospect was a poor choice on my part since I probably should have waited for the stable version.
 

 I'm not sure if this is important or not, but I'm running on a 64bit architecture (Intel 2 core.)

---

### Post by dino99 on 2010-09-12
its one of the numerous issue provided by 64 bits, and its why i use i386 with pae-kernel to fully use the ram.

i suppose you have enabled the wine team ppa to install the latest wine & winetricks. You should hunt errors logged into .wine/cs2/log or so.

---

### Post by tacitdynamite on 2010-09-21
For what it's worth, **I have the exact same scenario in 32-bit** ubuntu 10.10: 

> **Autokrat said:**
> When I upgraded to 10.10, I received this error:
> “An error has been detected with a required application library and the product cannot continue. Please reinstall the application.” 
  Photoshop installed fine and I can start it up, but every time I do, a few seconds later that error message comes up.

I'm running wine wine-1.3.3 from the PPA and the Sept 17, 2010 version of winetricks. 

There is no /cs2 or /cs2/log directory in ~/.wine. How do you look at the error log for wine?

---

### Post by TaliaT on 2010-09-21
Have exactly the same issue on 32bit 10.10.

Additionally, when I try to reinstall the authentication window doesn't show either.

Wasn't sure if it was due to some tinkering I was doing with my presets. 

I've checked my install on a 10.04 vm and that works fine. Installs, authenticates and runs. Copying the .wine directory from the vm to my computer also gets the same issue.

Seems to be an accumulation of two issues. One the authenticate on the install fails and second something isn't working with an authenticated version of photoshop once it's installed.

---

### Post by MartinEve on 2010-09-26
The respective version change between Lucid and Maverick is from 1.1.42 to 1.2, which would seem to be the cause of this problem.

The problem is also present in Wine 1.3.

However, I think it's more complex as, on Maverick, the problem is still present after these steps, which will install 1.1.42:


**Steps I tried:**
sudo apt-get update
sudo apt-get remove wine

sudo nano /etc/apt/sources.list
Comment out all Maverick "universe" lines
Add:
```

deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe

```
sudo apt-get update
sudo apt-get install wine

Uninstall photoshop
Reinstall photoshop
Activate photoshop

Put /etc/apt/sources.list file back to how it was (uncomment the Maverick "universe" lines and remove the lucid lines)

:(

---

### Post by MartinEve on 2010-09-26
As a temporary workaround:

run it from command prompt:

wine ~/.wine/path_to_photoshop/Photoshop.exe

when the error dialog appears, press CTRL+C in the terminal window.

Another error will popup in photoshop.

Press ok on that error. Press ok on the original error. You will then be inside Photoshop.

---

### Post by psytrox on 2010-10-09
Thank you MartinEve.  That is the only way it works for me.  I tried with multiple versions of wine through PlayOnLinux, too; same problem.

---

### Post by c0balt on 2010-10-10
I'm having this exact same issue on the 32 bit version of Ubuntu 10.10. The issue only presented itself after I upgraded from 10.04. 

I have tried to use the workaround, and that's one way to get Photoshop to run, but none of the shortcut keys work. Not even most common keystrokes like using DELETE to clear something or the arrow keys to finely position objects and layers. This means anytime I need to do something, I have to go to the edit menu, for example, just to perform a copy or paste. It's frustrating when you need to do anything quickly.

---

### Post by bradtem on 2011-01-01
> **MartinEve said:**
> As a temporary workaround:

run it from command prompt:

wine ~/.wine/path_to_photoshop/Photoshop.exe

when the error dialog appears, press CTRL+C in the terminal window.

Another error will popup in photoshop.

Press ok on that error. Press ok on the original error. You will then be inside Photoshop.

This works, but in the resulting Photoshop all the keyboard shortcuts are non operative.   Makes it hard to use.

---

### Post by edib on 2012-05-24
> **MartinEve said:**
> As a temporary workaround:

run it from command prompt:

wine ~/.wine/path_to_photoshop/Photoshop.exe

when the error dialog appears, press CTRL+C in the terminal window.

Another error will popup in photoshop.

Press ok on that error. Press ok on the original error. You will then be inside Photoshop.

i did first command but no error message appeared. works fine.

---

