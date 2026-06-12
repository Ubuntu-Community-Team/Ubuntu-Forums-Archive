---
title: "nvidia-glx"
date: 2004-12-08
forum: Repositories &amp; Backports
---

### Post by watchitman on 2004-12-08
I installed the NVidia drivers from the somethingorother repository and I've had nothing but problems. I followed the directions in the WIKI and everything seemed to go ok until I rebooted. The X server kept rebooting over and over. I got the following warning message:

"There already appears to be an X server running on display :0. Should I try another display number? If you answer no, I will attempt to start the server on :0 again. (You can change consoles by pressing Ctrl-Alt plus a function key such as Ctrl-Alt-F7 to go to console 7. X servers usually run on console 7 and higher. <Yes> <No>"

It didn't matter whether I clicked yes or no, it just kept rebooting X when I attempted to move my mouse. Then the message would appear again and it did all this in an endless loop. I had to do a hard reboot to get out of it.

I've had to reinstall Ubuntu three times because of my problems with this (I'm persistent). Please advise, thank you.

---

### Post by watchitman on 2004-12-08
Anyone?

---

### Post by watchitman on 2004-12-09
Is anyone out there?

---

### Post by Perfect Storm on 2004-12-09
Is it the Nvidia-glx version 1.0.6111-1ubuntu you're trying to install? There should be no problem installing them.

But I had the same problem with hoary, but not warty.

---

### Post by watchitman on 2004-12-09
[QUOTE=Artificial Intelligence]Is it the Nvidia-glx version 1.0.6111-1ubuntu you're trying to install? There should be no problem installing them.

But I had the same problem with hoary, but not warty.[/QUOTE]

Yes, that is the version I'm having trouble with. I'm not using Hoary.

---

### Post by GeneticFreek on 2004-12-14
I followed the directions in [OSNews' Preview of Ubuntu](http://www.osnews.com/story.php?news_id=8407&page=4) and have had NVidia drivers working no problem. The steps are as follows:

1) Install nvidia-glx from the universe
2) Load the driver with the command 'sudo modprobe nvidia'
3) Add 'nvidia' to /etc/modules
4) run 'sudo dpkg-reconfigure xserver-xfree86' choosing 'nvidia' to the first driver question, and enabling 'glx' and disabling 'dri' and 'GLcore' from the list near the end.
5) Reload gnome with ctrl-alt-backspace

Hope this helps  O:)

---

