---
title: "ubuntu 14.04 file system"
date: 2013-11-21
forum: Ubuntu Development Version
---

### Post by leeper69 on 2013-11-21
I just installed ubuntu 14.4 on its owne partision and using the file system that is installed by default I cant get to my root file system even if i use the sertch tool and type in only the /
I installed thunar file manager and had no problem getting to root but can only open one instance of thunar from the dock.
if I look through the software installed on my system and open thunar from there I can get a second instance of thunar to open so I can use drag and drop.
I am new to the ubuntu desktop and have been using xubuntu what am i missing? how can I open two instances of thunar from the dock. and can i move the dock to the bottem of the screen insted of the left side of the desktop?

---

### Post by Frogs Hair on 2013-11-21
***Moved to Ubuntu + 1***

---

### Post by heir4c on 2013-11-22
You can't move the dock to the bottum. Ubuntu use Unity: [https://unity.ubuntu.com/about/](https://unity.ubuntu.com/about/)
If you want to go INSIDE the /root folder than you must open a terminal and type:
```
sudo nautilus
```

Or:
```
sudo nautilus /root
```

(Normally you have to use gksudo but it is no longer installed.)

I you just want to see the folders under / than you open nautilus (filemanager) and click in the left on "computer".
In the Unity-bar (Launcher) you see this icon for nautilus:
[IMG]http://i.imgur.com/O16dwuY.png[/IMG]

If you want to use Xubuntu than you can install the Xubuntu 14.04:
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

---

### Post by coffeecat on 2013-11-22
> **leeper69 said:**
> how can I open two instances of thunar from the dock.

Middle click on the appropriate Unity Launcher application icon to open a second instance of any application.

---

### Post by philinux on 2013-11-22
Or right click to see the "quick list".

---

### Post by heir4c on 2013-11-22
> **coffeecat said:**
> Middle click on the appropriate Unity Launcher application icon to open a second instance of any application.

Every day we learn more. ThanX for the tip!

---

### Post by leeper69 on 2013-11-22
Hi  thanks for answering my post heir4c,coffeecat and philinux!!!
I will try your tips.
coffeecat the center button or in my case the scrool wheel did the trick!!! thanks agin!!!

---

### Post by zika on 2013-11-22
14.04.

---

