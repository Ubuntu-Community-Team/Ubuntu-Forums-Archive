---
title: "Problem running anything in Wine."
date: 2009-06-21
forum: Wine
---

### Post by koubanator on 2009-06-21
So, I am new to Ubuntu, but not Linux itself as we use it at work (Gentoo). I'm trying to get WoW, Fallout 3, COD:MW, etc.... to install, but i get the following error. 
 
The program Installer.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience. 
 
This can be caused by a problem in the program or a deficiency in Wine.  You may want t check [http://appdb.winehq.org]("http://appdb.winehq.org/") for tips about running this application. 
 
If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org.]("http://bugs.winehq.org./")   
 
I've checked all the forums, and such, but can't find anything. I have reinstalled Wine three times now. Yes, I have the latest 1.1.24. I've tried running it in Vista, XP, and 2000. I also tried in Win98 and downloading dcom98 from Winetricks. Really confused on this one. Also, on WoW, I am using the Download Client, as I know that works a lot better. 
 
Any insight would be nice, as I'm about ready to kick myself.

---

### Post by DOS4dinner on 2009-06-21
As of late, I've been having this problem, and there's another guy on the WineHQ forums that reported this too. I think it's a regression in 23/24, but I'm not sure. What's your graphics card?

---

### Post by koubanator on 2009-06-22
nVidia 9800GT

---

### Post by koubanator on 2009-06-22
problem resolved.  after running the CD to install, and looking in Terminal, found 3 bad .exe files.  deleted, and it worked.

---

