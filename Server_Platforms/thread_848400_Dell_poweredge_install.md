---
title: "Dell poweredge install"
date: 2008-07-03
forum: Server Platforms
---

### Post by RFXCasey on 2008-07-03
Hi there, I have just acquired a Dell Poweredge 2400 from a friend at work. I am pretty much an ubuntu noob and especially when it comes to servers. I am trying to install the latest version of Ubuntu server but my raid configuration is not being recognized. I have read post in a forum [http://rbtech.blogspot.com/2007/03/installing-ubuntu-server-610-on-dell.html](http://rbtech.blogspot.com/2007/03/installing-ubuntu-server-610-on-dell.html) that would seem to be the solution I might be looking for but I don't know anything about megaraid drivers. Are they contained in the kernal or what. The post says to press control M at when it loads but I don't know how to identify when it loads. Is this in the bios or do I have to have the OS installed first the get there? If there is no hope could someone please tell me the best free linux OS to run on this server that would communicate with my other Ubuntu machines on my network. I am in a real bind here and really don't want to have to install windows to get the server working.:confused:

---

### Post by unixbills on 2008-07-03
The CTRL-M is a megaraid command from bios.  After basic machine bios runs you would typically see this message to enter the bios on the megaraid card.  On fast machines this can go so quick you don't see it.  Just start hitting ctrl-m on power up until you get in.

Is your card a megaraid?  Do you see this message?  

Sorry I can't help you with your dell 2400/raid configuration in Ubuntu.  I have just worked with the megaraid card before and remember this bios question.

---

### Post by ixus_123 on 2008-07-03
ctrl M is to access the megaraid bios.

You'll need to enter this during boot and create a logical drive. Once you have done that, you can install the operating system.

You don't say how many disks you have but if you have only 1, you can set this up as a RAID 0.
2 disks go for a RAID 1 etc.

All the controls for the megaraid BIOS are along the bottom of the screen but from memory you'll probably have do something like this:

1. At boot, hold CTRL + M when prompted to enter RAID BIOS

2. RAID BIOS is a blue on blue screen that can be navigated with arrow keys. SPACE ususally selects menu items, ENTER / RETURN will end a selection (when selecting multiple things) and F10 usually confirms an important action.

3. Assuming the data on your disks is fine to be wiped, go to step 4.

4. from the object menu, you can view the state of your raid card, if the alarm is enabled, battery state etc. You can alse enable audio alarm and set the rebuild rate (default = 30%)

You can also view logical and physical disks. F2, will give you more details on the physical disks such as capacity, firmware revision, vendor and any predictive failures or errors.

5. go back to the main menu and from the configure menu, we can create a new arrray, or clear an old one (if the data is okay to be lost.

6. BIOS will search for drives for a few seconds before the next menu comes up. 
- select the disks you want for array with arrows and SPACE bar.  When you have selected all you need, hit enter to end the array.

7. F10 to configure, then (Ithink) SPACE again to select the span.

8. from here you can set up RAID level - eg RAID one.  To get the most from the card performance wise, set read mode to adaptive, and IO to cached IO, write level to writeback,

If you want to tweak to your needs to can google what each of these are (basically how your system uses the card's RAM to save writes on the disk when the disk is busy / less busy.

9.  Once that's set up, ESC, accept the config, select yes to confirm

10.  initialise - this will clear all data on the disks!

Next time you boot, Ubuntu should have something to install to - it will see the span as one disk.

Sorry if you knew all this, I wasn't sure your level of understanding of RAID, so I tried to break down the steps as best I can remember so that anyone could hopefully get it.

Megaraid is really awesome. Be sure to download the megaraid utility from their website (I'm sure they must have an Ubuntu package).  This utility lets you access the raid bios from the command line. It's almost exactly the same as the real RAID BIOS but with out the prompt bar at the bottom of the screen telling what keys do what.

I have no experience with Dell 2400s but have used megaraid on tonnes of Dell 2850s

---

### Post by ixus_123 on 2008-07-03
Oh, I just re-read your post....

You should see the prompt for the RAID card soon after boot.  It will be the first thing checked after the memory tests.

The screen should say something like, 2 physical drives detected, one logical drive, hold CTRL M (or CTRL R) to enter raid bios.

As I said above, I'm not familiar with the 2400, it could be you don't have a RAID card.  If you are not sure, open the server and look to see how your disks connect up inside.   Megarad will be a dedicated card, perhaps with a battery on it.

---

### Post by RFXCasey on 2008-09-25
ixus_123 you totally rock man. Your information was extremely insightful and welcome. As I am pretty new at all this Linuxing any detailed and understandably arranged knowledge is likened to sitting near a warm fire on a cold winters day. I wish everyone knew how to present their thoughts is such a clear and concise way. If I wasn't such a lame *** I would post you a thanks but my feeble mind hasn't figured it out yet.

---

### Post by RFXCasey on 2008-09-26
Just one more thing. I decided to go with Debian instead and it went over without a hitch. Worked flawlessly out of the box except for some OS updates after the install. I installed LAMP and Proftpd and now have an awesome little web host/backup server stationed out in my garage of course because the noise that thing puts out makes it sound like a jet taking off.:guitar:

---

