---
title: "Near catastrophe with hard drive"
date: 2005-08-22
forum: The Cafe
---

### Post by matthew on 2005-08-22
Charles Dickens described my day quite well. "It was the best of times, it was the worst of times..."

My ***hard drive failed*** today in my laptop. Fortunately, I did a ***full backup today*** using the method described on these two pages so I will find out soon how well the restore works.

[https://wiki.ubuntu.com/BackupYourSystem](https://wiki.ubuntu.com/BackupYourSystem)
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

Within an hour after finishing the backup I left my home office to eat dinner with my family. I came back and wiggled the mouse to stop the screensaver. As I did I noticed a strange high-pitched sound. I clicked on Evolution to read my email and--nothing happened. I tried again and the high-pitched sound got louder and louder, turned into a low rumble, and then faded into a dull hum. Bummer. The system worked fine, but no response form the hard drive. So...CompUSA had a 80Gb Samsung drive on sale for $129 (after rebate) so I bought it and installed it. I am now in the process of restoring my backup...I'll post a followup once it's done to let you know how it went. I'm using the family computer right now, so I have a backup plan as well as a backup to the world.

I was dual booting on it with Windows on my machine, but I haven't used Windows in over a month so I am going to just install Ubuntu.

---

### Post by skoal on 2005-08-22
That's good to hear.  I recently lost a replacement Maxtor drive only a few months ago with some business data on it (which I didn't have on CDs at the time).  Unfortunately, even the BIOS wouldn't recognize the drive.

Thankfully, my trusty Kenmore refrigerator was able to salvage it for me.  I put my 30 gig'er in a ziploc freezer bag, stuffed it in an empty ice tray, took it out a week later, and attached it to my IDE ribbon cable.  I let it set at room temperature for a bit, wiped off the sweat with a paper towel, and the BIOS finally recognized it.  I was able to use if for 30 minutes and move all my data to another drive in the process.  That drive is currently in my backyard with an engraved stone above it's dirt mound, which simply reads: "R.I.P - here lies Maxtor"...that's lies, not lays...

Who says cryogenics are just for bringing people back to life...

Glad you saved some grief and burial rituals unlike myself...

\\//_

---

### Post by matthew on 2005-08-22
Great news!! I am up an running again and all seems to be working perfectly. That has got to be the easiest hard drive death recovery in my life. I did make sure once the process was complete to drop to a console ad use nano to edit my /boot/grub/menu.lst as well as my /etc/fstab to show the new partitioning scheme without windows. Otherwise it restored everything to a state IDENTICAL to before the failure. Wow. Very cool.

I'm off to make a new backup. :D

---

### Post by jonrkc on 2006-05-24
[QUOTE=skoal]
Thankfully, my trusty Kenmore refrigerator was able to salvage it for me. 
[...] Who says cryogenics are just for bringing people back to life...
[/QUOTE]This is the first time I've heard of freezing a failed hard drive to get it to work (even if briefly) after a failure.  It makes excellent sense.

I hope I can remember to try this next time a hard drive fails.  Thanks for the suggestion!  (And I'm glad it worked for you.)

---

### Post by bigken on 2006-05-24
I have heard of the freezer trick before just never had the balls to try it next time I get a dead drive ill give it a go ;)

---

