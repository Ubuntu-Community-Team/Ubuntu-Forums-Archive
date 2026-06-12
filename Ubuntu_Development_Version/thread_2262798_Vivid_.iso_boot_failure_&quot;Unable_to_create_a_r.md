---
title: "Vivid .iso boot failure &quot;Unable to create a required folder&quot;"
date: 2015-01-27
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2015-01-27
For the last 2 days, daily fresh zsync of vivid 64 .iso boots to

Oops, something went wrong...
Unable to create a required folder
/home/ubuntu/config/nautilus
plus some words about required permissions...

?  

I tried both from USB restored image and also booting direct from the .iso on the hard drive.

Haven't had this problem ever on Vivid, 14.10, 14.04, ....all the way back to Dapper Drake Beta (albeit on an older pc at that level).

Cannot do ubuntu-bug since the boot juist sits there, only wallpaper and two icons, no desktop, no launcher, Ctrl-Alt-F1 nothing, Ctrl-Alt-t nothing, 

Do note I test on a /dev/sdb USB hard drive, there is a /dev/sda Win7 hard drive.

Sure hope vivid isn't trying to create /home/ubunt/config/nautilus on the /dev/sda.  It should be creating it on the USB voot image...

---

### Post by Elfy on 2015-01-27
saw the same, maybe go to one of the vt's and do the bug report from there instead

```
apport-cli -f ubiquity
```

I'd do it - but I rarely boot anything but Xubuntu

(also changed thread title - nothing to do with Alpha 2 - that's long gone now)

---

### Post by tarpman on 2015-01-28
I just filed [bug #1415586]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1415586") about this.

---

### Post by jerrylamos on 2015-01-28
> **tarpman said:**
> I just filed [bug #1415586]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1415586") about this.

Thanks.  I've gotten this failure for three days in a row with each day's zsync.

I tried doing Ctrl-Alt-F1 and creating the folder worked O.K., then couldn't figure out how to continue the "Try Ubuntu" session.

I did go on and install O.K.  Has the same bugs as my updated partition, example wallpaper hashed horizontally. settings > appearance > wallpaper doesn't change the wallpaper, etc.  I've entered bugs for these.

---

### Post by craig10x on 2015-01-31
Still can't get into the live session on the 15.04 (unity) daily build that was posted on the 30th...so bug is still there...

---

### Post by ventrical on 2015-01-31
+1

---

### Post by craig10x on 2015-02-04
What doesn't make much sense is why are the putting out defective daily build downloads?  They should fix the bug first.....what is the point of being able to download a daily build that won't even go into a live session?

---

### Post by Elfy on 2015-02-05
> **craig10x said:**
> What doesn't make much sense is why are the putting out defective daily build downloads?  They should fix the bug first.....what is the point of being able to download a daily build that won't even go into a live session?

someone is assigned to it

---

### Post by craig10x on 2015-02-06
Thanks Elfy....Thank goodness ;) :mrgreen:

---

### Post by Elfy on 2015-02-06
> **craig10x said:**
> Thanks Elfy....Thank goodness ;) :mrgreen:

Don't thank me - I don't fix things and if I did they'd be Xubuntu things :D

---

### Post by craig10x on 2015-02-09
Anyone know if this has been fixed yet?  Can you get the live session on the daily build isos?
Just curious ;)

---

### Post by jerrylamos on 2015-02-10
> **craig10x said:**
> Anyone know if this has been fixed yet?  Can you get the live session on the daily build isos?
Just curious ;)
No, it's not fixed as of 10 February vivid amd64 .iso.  
For some reason the file permissions are screwed up and Ubuntu Development has not fixed it..
No live session.

---

### Post by craig10x on 2015-02-11
Thanks...you would think that would be a super high priority and that it would have been fixed already....very strange, indeed

---

### Post by Elfy on 2015-02-11
> **craig10x said:**
> Anyone know if this has been fixed yet?  Can you get the live session on the daily build isos?
Just curious ;)

You know that rather than ask - you could go and look at the bug.

---

### Post by jerrylamos on 2015-02-14
Fixed on 14 February amd64 daily build.  Live desktop came up fine.  First time in days and days.

---

### Post by tdockery97 on 2015-02-14
Also worked fine here booting from USB stick.

---

### Post by craig10x on 2015-02-15
Hooray...at last :D
Hey tdockery97....nice to see you again over here...
Would like to check it out when they add in the 3.19 kernel on 15.04 development...(which will end up being the release kernel)...

---

### Post by tdockery97 on 2015-02-15
Good to be back craig10x.  Found this latest build to be running smooth as glass.  Using it as my daily driver.

---

### Post by craig10x on 2015-02-16
I'm running the live session of 15.04 development (from sunday's build) and also smooth as can be over here....although not installing, i like it so much that i am going to keep it on through monday night before i pop it out :D
Looking forward to the release in late April ;)

---

