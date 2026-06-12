---
title: "Gutsy, system hangs every few minutes, Gazelle V4"
date: 2008-11-16
forum: System76 Support
---

### Post by DesiArnez6 on 2008-11-16
**Background**

I upgraded from Feisty to Gutsy using the Update Manager, and I noticed a change

(When I had feisty, the computer would lock up after a few hours of use where the mouse would barely move, except every three seconds or so, and I would have to Alt-F1 or something to get to a terminal and type "sudo killall hald-addon-stor" at which my system would be saved and back to normal, often the system would hang so badly that I'd have to restart. I was told this had something to do with my DVD drive, not sure)

Anyways, when I upgraded to Gutsy, (and modified that file, that workaround listed here so that It could boot without crashing when using the latest default kernel for Gutsy)

And after upgrading to Gutsy, that whole "hald-addon-stor" problem miraculously was fixed.

**The Problem**

So, now every five minutes or so, sometimes less or more, I can be typing like I am now in Firefox, and the letters stop showing up. The system sort of freezes, but the mouse arrow works fine. In fact the arrow moves smoothly wherever I want, but when I click on the webpage nothing happens, when I click on "Applications" or "Places" nothing happens, and when I minimize firefox, it kind of minimizes but leaves black box outlines of the window closing diagonally, OR the desktop is shown but blank , without any folders , and the bottom bar becomes blank too....

THEN, after a few seconds, The Hard drive green LED light flashes quickly like 10 quick flashes, and all the actions I clicked on happen at once in the correct order, I see the "Applications" Menu, then the "Places" Menu, or Firefox tabs that I clicked on all show quickly in the order I clicked, or all the words I typed finally begin to type themselves, as if the system were playing "catch up". And everything returns to normal.

Then a few minutes later, same thing. But the mouse ALWAYS works, and I can usually minimize the windows that are open. But the desktop always looks blank, or those shadow black box lines, until the Green LED blinks, and all the actions I did when it "froze" happen at once.

Rarely it will completely lock up (mouse included) and require reboot, but not very often

Why does this happen? How do I fix it, as its REALLY Annoying. I feel like I'm on 33.6k dialup, or an old 386. This happens WAY too often, fast (Normal) than freeze/ slow, green light blinks then fast normal, etc..

PLease help :)

Notes: System Name: Gazelle Value
System Model: gazv4
Processor: Intel Celeron M CPU 440 @ 1.86G
Memory:1027248 kB
Hard Drive: 97 GB

Note: This "freeze" happened at least 5 or six times while typing this. The "freeze lasts about 30 seconds

Thanks ;)

---

### Post by thomasaaron on 2008-11-17
That is a known bug for the **_older Gazelle Values *GazV3/4*_** and the **older, white Darters *DarU1***.

The problem is actually an incompatibility issue with the firmware in your dvd drive.

To flash the CD/DVD drive firmware in your (white)DarU1 or GazV4, follow
the instructions on this bug report...
[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)
...beginning with the post that has this header...
Thomas Aaron  wrote on 2007-08-13:  (permalink)

Let me know if you have any questions.

**NOTE TO OTHER READERS: IF YOU ARE NOT A GAZV4 OR DARU1 OWNER, DO NOT DO THIS. WHATEVER THE PROBLEM IS WITH YOUR COMPUTER, IT IS NOT THIS ONE.**

---

### Post by tipiglen on 2008-11-18
You might try looking here
[http://ubuntuforums.org/showthread.php?t=978842](http://ubuntuforums.org/showthread.php?t=978842)
or here
[http://ubuntuforums.org/showthread.php?t=975414](http://ubuntuforums.org/showthread.php?t=975414)

Good luck

Ed

---

### Post by DesiArnez6 on 2008-11-22
I read both responses. Since I don't currently have 2 pendrives, I decided to check what tpiglin said. The links were to posts that seemed similar to my problem. After typing "top" I noticed that my swap is 0k (not sure if this is a problem) Noticed all my memory was pretty much used up most of the time. However.....

Before messing with firefox, I decided to try running Epiphany instead. I still had the same problem. Assuming that maybe it was a mozilla thing. I decided to try Opera, same thing. Well, so now I wasn't quite sure if tpiglen's solution was my problem, And as luck would have it, my system froze, BUT I was able to hit CTRL-ALt-F5 to get a terminal And....

I noticed this:
[280878.388000] ata1.01: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[280878.388000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in

which would repeat several times with little change.

So after a google search, I ended up at a bugreport which then linked to thomasaaron's post. So, I'm now convinced that Tom has the solution for this specicic problem, right on target. So....

****

I cannot obtain another pen drive for probably a month or two. I do have 1 pen drive. Is there a way to do this solution with 1 pen drive and 1 external disk drive and disk 1.44? 

(I can't get any blank CDs or DVD's, but I do have alot of 1.44 disks laying around, and my 1 pen drive)

---

### Post by thomasaaron on 2008-11-22
Can you borrow a pen drive from a friend? You wouldn't want to put the image on it. But you can use it for the data file. That way it won't erase your friends data.

This is *definitely* the fix.

---

### Post by MorphWVUtuba on 2008-11-23
> **thomasaaron said:**
> This is *definitely* the fix.

I can vouch for that.  I had similar problems with my gazv2 & this fixed it.

---

### Post by DesiArnez6 on 2008-11-30
OK, I will try to find another pen drive and post my results here as soon as I try the fix. Thank you so much for your help.

---

### Post by DesiArnez6 on 2009-01-12
I Finally got my pen drive so I will now try the fix and post my results.

---

### Post by DesiArnez6 on 2009-01-12
Finished the process sucessfully. The only hiccup I had was I had to open up a second terminal window for step or Step 6, and i didnt see the part about leaving pendrive #1 in the USB port until after I'd already taken it out, so I had to put it back in, no problem there.

Overall process went smooth, and I'm currently listening to my Sergio Vargas CD with no problems ;)

So, I'll see how it goes this week, and try to put in one final post if this fix was permanent. I have a feeling it was, since so far its been running smoothly.

---

### Post by DesiArnez6 on 2009-01-18
OK, It totally worked :) One last question, after completing this process, how do I restore my USB Flash Drive? It was previously 8 GB, now it only says that I have 1.4 MB free space

---

### Post by thomasaaron on 2009-01-18
Download gparted...

sudo apt-get install gparted

...insert your USB drive and then go to System > Admin > Partition Editor. From there, you can delete existing partitions on your drive and reformat it... probably as fat32.

---

