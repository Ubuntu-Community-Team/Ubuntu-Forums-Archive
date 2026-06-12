---
title: "battery may be broken dialog"
date: 2008-01-25
forum: System76 Support
---

### Post by tuebinger on 2008-01-25
I got a dialog just now that said "Battery May Be Broken - Your battery has a very low capacity (49%) and may be broken.."  I can't remember  the exact wording. This happened just after I booted up and got another message I've never seen before.  The screen displayed several lines of text after which it read:  "/dev/mappper/ubuntu-root has been mounted 25 times without being checked, check forced" then it proceeded to do some kind of test and loaded normally.  

 When I mouse over ithe battery icont it reads:  "System is running on AC Power Battery charged (0%)".  It says this even if I unplug the computer.

 I took out the battery and replaced it to see if that would do anything, but it didn't.

Do I need a new battery?

---

### Post by canthus13 on 2008-01-25
The fsck is normal..  It checks the drive every 20 boots or so.  I dunno about the battery issue, though... mine does the same thing.  My battery charged fine in windows, but won't charge under ubuntu.  It shows the same 49% message (Sometimes 44%), but if I run on battery power for more than a couple of minutes, it shuts down and won't boot 'til I plug in.  I'm wondering if the noapic and nolapic boot options are causing problems with the battery.

---

### Post by tuebinger on 2008-01-26
Thanks regarding the fsck info.  I figured that part was probably normal, just unexpected.  I know my battery is working because I'm running unplugged right now and have been for about an hour, yet the battery icon still says 0%  charged.  I'm not familiar with  noapic and nolapic boot options, so I wouldn't know if that was the problem or not.

---

### Post by tuebinger on 2008-01-26
OK, here's an update.  My laptop recognized the battery upon bootup this morning.  I waited until the battery indicator showed a full charge (100%) then unplugged and started a timer. 

At first the battery indicator showed 0% charge. Later on it showed 1 hour 7 min (3%) remaining. Then again later on it showed 56 min (30%) remaining.  I continued to allow the battery to discharge completely.  

Finally, after 2 hours and 34 minutes the laptop shut itself down.  

The erratic messages from the battery icon must mean it's some kind of Ubuntu-bug??? But the 2 hour 34 minute battery time is far short of the advertised battery runtime of 4 hours.

I wasn't doing anything that required heavy processing, like photo-editing or anything like that, just normal surfing and checking email.

---

### Post by shad0w_walker on 2008-01-26
As I understand it the battery monitor has to watch your battery for its remaining charge, see how fast it is draining and works out a rough idea of how long it has remaining based on the capacity of the battery.  The erratic messages you got were probably during this peroid. The longer it runs the more accurate its estimates will get.

---

### Post by palintheus on 2008-01-26
This is related to the power management issue, my daru2 does the same thing.

---

### Post by pavel_987 on 2008-01-28
This is a known issue in the DSDT tables of the Daru2. Please refer this thread [http://ubuntuforums.org/showthread.php?t=609722](http://ubuntuforums.org/showthread.php?t=609722) for further discussion.

---

### Post by modmadmike on 2008-05-26
Like this?
[IMG]http://lds-syndrome.net/images//batterie.jpg[/IMG]
Mine went down to 47% capacity after 9months of forgetting to condition it (the laptop was bought 9 months ago). The instant shutdown after using it for max time (mine is only 1:10) occurs with mine. It will not turn on but will show a purple power led when i try to. This is not a bug, for it happens in any OS. It's simply forgetting to unplug it when it is fully charged because the Li-on cells break down quickly when you forget to. :(

---

### Post by smurphy_it on 2008-06-11
I have a HP Compaq DV2020ca laptop.  My laptop battery is at 42%.  Problem is, I can fully charge it, shut it down, and reboot or wait a day etc, and when I boot back into Hardy I find I only have 5% or less.

My battery life lately is very, very, sad.

I am thinking about getting a new battery, but am wondering if it is a bug first before I go that route, as a few minutes on a charge isn't very much and I'm sure I should have at least an hour per charge.

Any ideas ?

---

