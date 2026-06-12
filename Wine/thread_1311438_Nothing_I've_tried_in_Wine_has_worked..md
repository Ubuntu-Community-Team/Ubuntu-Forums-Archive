---
title: "Nothing I've tried in Wine has worked."
date: 2009-11-02
forum: Wine
---

### Post by blur xc on 2009-11-02
So far, every program I've tried to run in Wine has not worked.  Not only that, they crash in some fashion that makes me have to reboot my computer.  Today, it was a hard reset.  I played w/ Wine last night, after noticing yesterday's update included some Wine updates, and still nothing worked.  Then, my poor wife got on the computer today after I had left work work, tried to switch to her user, had a lot of crazy junk going on, so she tried to go back to mine, and was stuck w/ a froze system- only a desktop background, no panels, nothign.  Ctrl-Alt-F2 (as well as other F key combos) had no affect- so I told her to hit the reset button.

So far I've tried-
Adobe Lightroom - yeah, didn't have high hopes for that one but gave it a go regardless
Photoshop cs4 - I hear it works now but when I first tried it, it failed.  I haven't tried it since, and I'm making an effort to come to terms with the Gimp.
Lego Digital Designer- I got all excited when I found some others using it in wine, but it's an older version of LDD.  The new ones don't work.  Maybe it'll get fixed.
Various Leapfrog software- for my kids' educational handheld gaming/reading systems.

That's pretty much it, and my only reasons for dual booting, since a few of those won't run in Vbox either.  Sad...

I'm pretty much heading down the road of totally removing wine altogether.  It just seems to cause me more grief than anything else.

BM

---

### Post by hikaricore on 2009-11-02
Your lockups are likely hardware related.
More info on your system would be helpful.

Did you read the appdb pages for any of these applications?

---

### Post by blur xc on 2009-11-02
> **hikaricore said:**
> Your lockups are likely hardware related.
More info on your system would be helpful.

Did you read the appdb pages for any of these applications?


Yeah, to some degree.  I know Lightroom is listed as a no go, but LDD had a gold rating IIRC.  But, I don't think I checked on the others.

My specs:  core 2 duo 3.0ghz, 4 gigs dd2 1066, nvidia geforce 9600gt 512mb vid ram, running 32bit Ubuntu 9.04.  Will go 64 bit when I give 9.10 a go.

BM

---

### Post by hikaricore on 2009-11-02
Your hardware should be sufficent to run nearly anything short of super complex 3d games in virtualbox.

Are you using the version in the ubuntu repos or the one from the virtualbox site?
If I recall the one in the ubuntu repos was or still is inferiour.
Try download vb from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Also with WINE remember even if an app is rated gold, it could just be a garbage review.
Some apps are managed by people who don't pay a whole lot of attention to the info they approve.
It's always good to read through the comments and various other info to be sure.

---

### Post by blur xc on 2009-11-02
> **hikaricore said:**
> Your hardware should be sufficent to run nearly anything short of super complex 3d games in virtualbox.

Are you using the version in the ubuntu repos or the one from the virtualbox site?
If I recall the one in the ubuntu repos was or still is inferiour.
Try download vb from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Also with WINE remember even if an app is rated gold, it could just be a garbage review.
Some apps are managed by people who don't pay a whole lot of attention to the info they approve.
It's always good to read through the comments and various other info to be sure.

I am running the PUEL version of Vbox.  Lego Digital Designer won't work, I'm assuming because of a 3d graphics issue.  Considering the rate of VBox development, it might get running soon.  They are doing amazing work over there.  

I can't run Lightroom because I need to have my lightroom catalog file on my external drive, along with all my photos.  For some reason only known to the folks at Adobe, Lightroom isn't happy with its catalog file on a network drive, which is how shared folders appear to the virtual machine.  I *could* get around this w/ raw disk access in VBox, but running the risk of corrupting my entire disk scares me away from trying it.

iTunes and the leapfrog software runs fine in VBox- I just have to dual boot to run Lightroom and LDD for my kids.  To solve the lightroom problem, I intend to get Bibble, since they provide a great product with a native linux port.

It's just funny thing to see the difference in people's computer software needs.  Of all the programs I read about people running in Wine, I have no use for any of them.  Yet, what I do have a use for, doens't run in wine and crashes my computer.

BM

---

### Post by beastrace91 on 2009-11-02
> **blur xc said:**
> It's just funny thing to see the difference in people's computer software needs.  Of all the programs I read about people running in Wine, I have no use for any of them.  Yet, what I do have a use for, doens't run in wine and crashes my computer.

IMO & if you look at a large portion of the appdb Wine is pretty much used for mostly gaming.

~Jeff

---

### Post by DanFoxDavies on 2009-11-13
Please read this thread below regarding what has been tried thus far to get LDD 3 working on Wine. If you have any ideas, please contribute them there. If we solve it, this thread below will be where you find out.
[http://ubuntuforums.org/showthread.php?t=1292942&highlight=lego](http://ubuntuforums.org/showthread.php?t=1292942&highlight=lego)

---

