---
title: "X random 100% CPU usage"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-04-10
Every so often at random times, my desktop becomes unusable, cannot type anything, clicking on window close buttons does nothing etc and the laptop fan is screaming at me.

When I am finally able to do something and get htop running, it shows /usr/bin/X at around 97% - 100% CPU usage.

This normally continues for up to 5 minutes before everything goes back to normal.

I am unable to find any kind of trigger for it, it happens with just a web browser running (Chromium), just a terminal running and even at an empty desktop.
Not sure exactly when it started but it has been at least a week I would say and happens anything from once to five times in a day.

---

### Post by ayozito on 2012-04-10
This just happened to me with Disk Utility. System full load and when I was able to open the system monitor, RAM 99% and swap 75%, and after a while a message show up saying that one program had a error because of lack of memory, and it was the disk utility.

---

### Post by RJARRRPCGP on 2012-04-10
> **ayozito said:**
> This just happened to me with Disk Utility. System full load and when I was able to open the system monitor, RAM 99% and swap 75%, and after a while a message show up saying that one program had a error because of lack of memory, and it was the disk utility.

Sounds just like the bad ol' times, in the early 2000s, with anti-virus leaking RAM. With Windows XP and McAfee VirusScan 6x, 
when scanning a compressed file format, Windows XP gives a warning about the virtual memory being low. After, the McAfee real time scanner crashes.

---

### Post by jadtech on 2012-04-10
i cant say for sure what is causing this and I am sure most would say you are not giving enough info ..
 I have seen issues like this with the computer attempting to share files between each other computer in the network , you wouldn't happen to have another computer in the house  attempting to  send or share like mp3 or mp4 files,or a ubuntu one account that is loaded full and attempting to syn ..

just a though we had a computer suddenly started processor racing as it aatempted to share it whole 150gb of music files with a lap top some one brought in with shareing turned on ..

---

### Post by NHclimber on 2012-04-10
There's definitely something going on related to compiz. Others have reported similar issues [http://ubuntuforums.org/showthread.php?t=1953048](http://ubuntuforums.org/showthread.php?t=1953048) (interesting this shows chromium running too) and [http://ubuntuforums.org/showthread.php?t=1951671](http://ubuntuforums.org/showthread.php?t=1951671)

The more information you provide the more likelihood that a pattern will emerge that will narrow down the source.  Things like what display driver, are you running the latest updates, what DE, etc?  A screenshot of top would help.

@ayozito,
There's also something going on with python-based code. Massive memory usage/CPU buried at 100% in a lot a different python apps.  It's not clear if this a memory leak issue or some kind of multi-threaded race or what (doesn't help that ubu kernel is not preemptive).

---

### Post by x-shaney-x on 2012-04-10
I will wait til it happens again then get a screenshot of htop running.

Mostly Intel hardware here but not sure of specifics off-hand.
I will do some probing and update with hardware information.

---

### Post by Gregory Lee on 2012-04-10
In the past (using a previous system), Gnome and Google have given me a problem by firing up indexing programs that use lots of cpu.  Another troublesome program has been flashplayer when I'm using Firefox -- it can be invoked by an advertisement, and shows up as "plugin-container" when I use top.  I haven't noticed flashplayer eating large amounts of cpu since the last update of flashplayer, though.

---

