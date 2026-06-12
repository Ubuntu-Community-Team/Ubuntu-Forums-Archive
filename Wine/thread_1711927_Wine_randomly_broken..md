---
title: "Wine randomly broken."
date: 2011-03-21
forum: Wine
---

### Post by Clessy on 2011-03-21
Ok so i was trying to run a file that has previously worked and now wine doesnt work at all.

Pull it up in terminal and says cant find dos driver. Wtf could of happened.

So I use the ubuntu uninstaller and uninstall and reinstall.

Still broke

So I use a sudo apt-get remove --purge wine.

Nothing. This sucks.

---

### Post by cogadh on 2011-03-22
Yep, that does suck. But we might be able to help you make it suck a little less if you just gave us a few useful details, like Wine version, the name of the app you are trying to run, the full details from Wine's error output... just for starters.

Right off the bat, however, I have to ask why you are using Wine to run what sounds like a DOS program, when DOSBox would do it so much better?

---

### Post by Clessy on 2011-03-22
> **cogadh said:**
> Yep, that does suck. But we might be able to help you make it suck a little less if you just gave us a few useful details, like Wine version, the name of the app you are trying to run, the full details from Wine's error output... just for starters.

Right off the bat, however, I have to ask why you are using Wine to run what sounds like a DOS program, when DOSBox would do it so much better?

To my knowledge its not a dos program. Its ran before. Im trying to run Sonic Fan Remix. Very simply little program.

when in terminal I only ge one line from wine and thats cant find dos driver.

I dont have wine installed right now so I cant give a version number again. I guess i need to know how to turn on hidden files so i can see the wine folder and completely remove its previous configuration files.

---

### Post by Clessy on 2011-03-22
I dont get it. I just did a complete reinstall of the OS. I could of sworn of it deleted the previous partitions so I don't know why it kept the settings.

It kept the os configuration 

clessy@clessy-901:~$  cd /media/4848-24B5/WINE
clessy@clessy-901:/media/4848-24B5/WINE$ sonic.exe
sonic.exe: command not found
clessy@clessy-901:/media/4848-24B5/WINE$ wine sonic.exe
Warning: could not find DOS drive for current working directory '/media/4848-24B5/WINE', starting in the Windows directory.
wine: cannot find L"C:\\windows\\system32\\sonic.exe"
clessy@clessy-901:/media/4848-24B5/WINE$ ^C
clessy@clessy-901:/media/4848-24B5/WINE$

---

### Post by Clessy on 2011-03-23
Figured it out just had to mount every sd card i have as a winedrive.

---

