---
title: "BIOS Update?"
date: 2006-09-29
forum: System76 Support
---

### Post by kevinlyfellow on 2006-09-29
I found a post back on the forums at your website about a possible bios update for the gazelle performance which would enable suspend to work.  I was hoping for some word on if there is an update and if it does solve the suspend problem

---

### Post by crichell on 2006-09-29
I'm not sure yet - the BIOS version that's running on our working machines is the same as the non-working machines making it an interesting problem.  We have a couple of leads we're working on so I should no more within a few days.

---

### Post by eg-maverick on 2006-10-06
I have a Pangolin that I purchased in August. The suspend does not work. It is interesting that this is one of the features that is explicitly listed on your website yet it doesn't work. I hope this has a very high priority for resolution.
Thanks,
Craig

---

### Post by crichell on 2006-10-06
Hi Craig - Suspend does work on the Pangolin model we are selling now.  The original pangolin sold in August is a different model.  We didn't start supporting suspend until the Dapper release.  Are you running Dapper now?  I'd be happy to help you out with suspend.  I must admit though power management is a week area in my expertise.

---

### Post by crichell on 2006-10-06
Actually I'm thinking last year August (the year has flown by).  Nonetheless, I'm sure you're on Dapper - we haven't had any trouble with suspend.  What's happens when you attempt to resume?

---

### Post by eg-maverick on 2006-10-06
> **crichell said:**
> Actually I'm thinking last year August (the year has flown by).  Nonetheless, I'm sure you're on Dapper - we haven't had any trouble with suspend.  What's happens when you attempt to resume?

Yes we bought it this Aug. It had Dapper preconfigured. When recovering from suspend, the select for the touchpad does not work. I cannot select any menu or do anything. Most of the time the cursor will move be that's it. 
I'm not sure what else doesn't work cause without select (left mouse button or touch-tap), can't do much.
Thanks.
Craig

---

### Post by crichell on 2006-10-07
It sounds like you're machine is resuming from suspend but there is a problem with re-loading the synaptics module.  Do you have a USB mouse you can plug in - suspend - resume and then try using the external mouse?  If this works we can look at what's going on with the touchpad.

---

### Post by eg-maverick on 2006-10-09
Carl,
Last night I tried suspend (selecting suspend on lid close in the power settings). When I closed the lid, the screen went blank but the machine did not suspend. When I opened the lid, I couldn't get the screen to come back on. I had to hard powerdown (push and hold the power button). I figured that was enough for the evening. This morning, I've tried the same thing three times and suspend works fine! I have changed nothing. I'll see if I can get it to break again and send any info I can. Thanks for your interest.
Craig

---

### Post by crichell on 2006-10-09
Thanks for helping out Craig - please do let us know if it breaks - perhaps it's related to a particular app or module that's running.

---

