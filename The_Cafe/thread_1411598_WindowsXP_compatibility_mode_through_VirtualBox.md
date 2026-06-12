---
title: "WindowsXP compatibility mode through VirtualBox"
date: 2010-02-20
forum: The Cafe
---

### Post by dixon on 2010-02-20
Hi,
recently I've read some articles on Windows XP compatibility mode in Windows 7. I was just wondering if the same thing cannot be possible in ubuntu through virtualbox. I'm linux only since dapper drake, but from time to time I need to use some windows utility like blackberry desktop app etc. Is it possible to strip down the WindowsXP (so it can startup as fast as possible) and then in ubuntu associate exe files with the virtual box machine and it will start the virtual machine in the background, run the application in seamless mode and then after the application is closed, will shutdown the virtual machine? Also I'd like to see the installed apps on windows XP integrated to the application menu in ubuntu.
So the question is: Is the integration of WindowsXP apps in ubuntu possible?

---

### Post by marin123 on 2010-02-20
Thats not possible because you have to operate inside virtualbox, so if you could get virtualbox to load at startup and boot xp, you would have to open that window and work inside it...
does that app work in wine? thats the closest you can get to integration of windows app in linux...

---

### Post by Dr. C on 2010-02-20
This can be done. [https://help.ubuntu.com/community/SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization")

Same principle as the XP compatibility mode in Windows 7. An application running in a virtual machine made to appear to run on the desktop.

---

### Post by dixon on 2010-02-20
Thank you very much. I'm going to try it.

---

### Post by squilookle on 2010-02-20
I have seen what you're asking for done on a Mac - I believe it was VMWare Fusion or something of the sort. 

The seamless virtualisation thing in the Ubuntu documentation looks interesting.

---

### Post by Nerd King on 2010-02-20
Seamless is pretty cool. Some caveats though.

1. You have to load the VM, then it has to load the OS then you get to open the app.
2. It doesn't have direct access to the linux filesystem (a good thing)
  - Make a shared folder then map it to a network drive in windows if you want to share files back and forth

---

