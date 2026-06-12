---
title: "Help!  KDE freezes"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bill-lancaster on 2012-03-09
Ubuntu 12.04

I have reinstalled Ubunto on a new hd and installed my old HD as drive 'D'.

I can recover file from D: but can't write to it because now I'm not the owner!  I don't want to re-format it at this time so how can I become the owner (again)?

---

### Post by pavi_elex on 2012-03-09
ubuntu 12.04 ???

---

### Post by bill-lancaster on 2012-03-15
Ubuntu 12.10.
Installed KDE a few days ago.  It has now frozen.
At the moment I am operationg from an Ubuntu boot CD.
I have a backup of my files on a second (internal) HD using dejavu Backup.
I can't access the backup hd because I don't have the neccesary permissions.
I'm prepared to re-install Ubuntu but fear I won't be able to access my backup file.

Any help would be most appreciated.

Bill Lancaster

---

### Post by bill-lancaster on 2012-03-15
Yes, Ubuntu 12.04 LTS

Can you help?

---

### Post by TBABill on 2012-03-15
I think you'll need to post more info. What do you mean by frozen? Will it restore to unfrozen after a restart? Do you get to the same point in the boot process and then it stops? Did you install a proprietary driver for video and then it became unusable? Etc...need a lot more clarity into what you installed, what you have done and when it may have stopped working (such as after an update or driver install).
 
I'm assuming you meant 11.10 is what you just installed since 12.10 won't be out until October? Or did you mean you installed 12.04 beta 2?
 
From a Live CD you should be able to access data from your other partitions.

---

### Post by bill-lancaster on 2012-03-15
After more googling I found a reference to Ctrl+ESC,  loaded my faulty KDE and it ran the System Activity programme.  Under All Processes, only krunner (system activity) and xorg showed CPU activity 1 or 2 % each so there doesn't seem to be anything using up the CPU.

I also tried CTRL+F8 which produced a terminal type screen with a repeated series of messages refering to @dropping frames due to full tx queue0

You can see from the above that I don't really know what I'm doing but I hope this might stimulate a response.

---

### Post by oldos2er on 2012-03-15
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by oldos2er on 2012-03-15
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by bill-lancaster on 2012-03-15
Thanks for the interest TbaBill,
I'm pretty sure I screwed the system by trying to run a script at startup.
I received some advice to put a file in the .kde4 folder (?? not sure noe since I can't access the system).  Any way I mistakenly put a text file in home/.kde (from memory).  I then rebooted to see if the script would run.
That is exactly where my problem started.

Whe I boot the PC I don't get any option re user, password or anything.  I just go straight to the KDE stratup screen, then the KDE desktop.  The WLAN connect quickly to my wifi.  The mouse continues to respond in all circumstances but when I click on any icon (say, my Dolphin icon in the tool tray), a short delay (while the mouse pointer shows busy) the programme goes immediately to the minimised state.  This applies to the Close or Log-Out functions as well.

As you can see from my previous posting, CTRL+ESC produces a healthy System Activity application.

Sorry, I meant Ubuntu 12.04 LTS

Bill

---

### Post by bill-lancaster on 2012-03-15
For some reason this thread has been moved to Ubuntu+1.

How can I access my KDE partition from an Ubuntu CD boot?

Bill

---

### Post by cariboo on 2012-03-15
Your two threads were moved to U+1, as they are problems with a testing release. This is the place to get answers to your question. 

Please don't start multiple threads on the same subject, I have merged your two threads.

---

