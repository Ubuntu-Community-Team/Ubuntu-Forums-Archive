---
title: "Karmic Slowness..."
date: 2009-12-17
forum: Wine
---

### Post by tarbox on 2009-12-17
It seems that all things windows have become unusable / slow in Karmic.

I was using Virtualbox but that essentially broke with Karmic due to Kernel issues (they changed the clock rate).  So Virtualbox is now off the table... The Virtualbox people seem very off balance on this one and I'm kinda surprised given the wide usage of Ubuntu / Virtualbox...  This is gonna hurt both brands...

Trying to use this as an opportunity, I tried Wine.  I was able to do pretty substantial things including building all of Qt from scratch off the git repo.  

Very impressive.

However, when I tested a very simple application, no graphics, just a bunch of disk I/O, it was slow... and I mean REALLY slow... like 1/20 the speed of the test running on Virtualbox.

Dutifully, I went to the forums and looked around.  Not much sense to be made in general as all performance discussions typically refer to a particular game or app.  But I came away with the impression that most people find Wine to run pretty fast.

So, I'm thinking there may be something fundamentally broken in Wine in Karmic as well.  The performance is so amazingly bad that I must be missing something extremely fundamental or there would have been more written about this.

I also grabbed the latest Wine off the PPA, so it isn't that I'm using some old crufty version.

I'm a bit off balance and don't know what to try.  Obviously, I could try and track this down but it seems so extreme a slowdown that something major must be occurring... perhaps there's a test or log I should be looking at?

Sorry for the long post but I'm not really sure how to start here.  For a console Qt application that does almost nothing to be 1/20 the speed of a Virtualbox application seems a little over the top.

-glenn

---

### Post by HighCommander540 on 2009-12-17
> **tarbox said:**
> It seems that all things windows have become unusable / slow in Karmic.

I was using Virtualbox but that essentially broke with Karmic due to Kernel issues (they changed the clock rate).  So Virtualbox is now off the table... The Virtualbox people seem very off balance on this one and I'm kinda surprised given the wide usage of Ubuntu / Virtualbox...  This is gonna hurt both brands...

Trying to use this as an opportunity, I tried Wine.  I was able to do pretty substantial things including building all of Qt from scratch off the git repo.  

Very impressive.

However, when I tested a very simple application, no graphics, just a bunch of disk I/O, it was slow... and I mean REALLY slow... like 1/20 the speed of the test running on Virtualbox.

Dutifully, I went to the forums and looked around.  Not much sense to be made in general as all performance discussions typically refer to a particular game or app.  But I came away with the impression that most people find Wine to run pretty fast.

So, I'm thinking there may be something fundamentally broken in Wine in Karmic as well.  The performance is so amazingly bad that I must be missing something extremely fundamental or there would have been more written about this.

I also grabbed the latest Wine off the PPA, so it isn't that I'm using some old crufty version.

I'm a bit off balance and don't know what to try.  Obviously, I could try and track this down but it seems so extreme a slowdown that something major must be occurring... perhaps there's a test or log I should be looking at?

Sorry for the long post but I'm not really sure how to start here.  For a console Qt application that does almost nothing to be 1/20 the speed of a Virtualbox application seems a little over the top.

-glenn

It could just be your install. Because there are lots of people that run Karmic and Wine and have no problems whatsoever. Or your hardware could be incompatible. Or it could just be that program, have you tried any others?

---

### Post by Bwathke on 2009-12-18
I dont know that your issue is because when I started with Karmic everything is faster. Are you sure you are all updated and you have the latest version of WINE?

---

### Post by YokoZar on 2009-12-19
> **tarbox said:**
> However, when I tested a very simple application, no graphics, just a bunch of disk I/O, it was slow... and I mean REALLY slow... like 1/20 the speed of the test running on Virtualbox.
It's very possible there's a bug in Wine making this particular application slow.

Test another program other users report as running decently and then you'll be able to say whether it's Wine running that program or Wine on your system in general.

---

### Post by Capt. Blackwood on 2009-12-20
Slow...check your audio...tell me what it is

ALSA/Pulse Audio are very...VERY Slow.

You may want to give OSS a shot. That's what sped wine up for me.

---

