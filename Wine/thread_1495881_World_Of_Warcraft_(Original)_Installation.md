---
title: "World Of Warcraft (Original) Installation"
date: 2010-05-28
forum: Wine
---

### Post by HenrySkitsas05 on 2010-05-28
I've got the cd, and I've followed the online guide for installing wow on Ubuntu but when I type into Terminal 

"cd //home/henry/Desktop/wow_install/ wine Installer.exe" 

This appears. 

"//home/henry/Desktop/wow_install$" 

What am I supposed to do at this point?

---

### Post by cburner on 2010-05-28
Did you copy the contents of the CD to the folder ```
/home/henry/Desktop/wow_install
```

There is more on the CD than installer.exe

---

### Post by HenrySkitsas05 on 2010-05-29
I had one CD with World Of Warcraft on it. And I copied ALL the files to the folder 

/home/henry/Desktop/wow_install

---

### Post by cburner on 2010-05-29
Type this into a terminal: ```
cd /home/henry/Desktop/wow_install
```
then type into the terminal ```
dir
``` and post the output here.

---

### Post by HenrySkitsas05 on 2010-05-29
Installer\ Tome\ 2.mpq    Installer\ Tome\ 6.mpq
Installer\ Tome\ 3.mpq    Installer\ Tome.mpq
Installer\ Tome\ 4.mpq    World\ of\ Warcraft\ (OS\ X).app
Installer\ Tome\ 5.mpq

---

### Post by HenrySkitsas05 on 2010-05-29
Problem Solved. I was being stupid. I didn't unmount and remount so I couldn't see some hiddenn files..

---

### Post by HenrySkitsas05 on 2010-05-29
Ok, maybe not solved. I just tried the same process again and got the reply 

henry@henbox:~/Desktop/wow_install$

I then entered dir, and it replied 

Autorun.inf    Installer.ico           Installer\ Tome\ 6.mpq
Desktop\ DB    Installer\ Tome\ 2.mpq  Installer\ Tome.mpq
Desktop\ DF    Installer\ Tome\ 3.mpq  World\ of\ Warcraft\ (OS\ X).app
DirectX        Installer\ Tome\ 4.mpq
Installer.exe  Installer\ Tome\ 5.mpq

Why isn't it running the installer?

---

### Post by cmileto on 2010-05-29
Is that the MAC install cd and nopt the x86 install cd?

---

### Post by HenrySkitsas05 on 2010-05-29
I'm not sure If I'm honest. I played wow on Windows XP before I changed to Linux on this computer and I used the exact same CD.

---

### Post by cburner on 2010-05-29
In the same terminal, type:```
wine Installer.exe
```or via the gui navigate to that folder and right click Installer.exe and click open with Wine...

As far as I know, the Mac and Windows versions are on the same CD/DVD so that should not be an issue.

---

