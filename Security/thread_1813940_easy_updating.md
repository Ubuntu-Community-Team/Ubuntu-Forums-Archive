---
title: "easy updating"
date: 2011-07-28
forum: Security
---

### Post by sks24 on 2011-07-28
I would like to set up my father's 11.04 installation so that it updates with minimal actions needed on his part.  It looks like I can set it to "Install security updates without confirmation."  

I set it this way once, and I seem to recall that I still had to actually click on the Update Manager and then the "Check" button and then "Install Updates" and only then would the prompt for the password pop up.  

He won't go through all that.  If I select "Install security updates without confirmation," will the machine download all updates and then simply present him with a prompt for his password to authenticate?  If not, is there a way to do that?  If not, how would I set up his machine so that he would have to do the least discrete number of actions to keep his installation properly updated? 

Thanks in advance,
Scott

---

### Post by bodhi.zazen on 2011-07-28
I would do security updates only.

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by sks24 on 2011-07-28
Thanks bodhi.zazen,

If I selected "Download all updates in the background," would the Update Manager pop up when the downloads were done?

---

### Post by bodhi.zazen on 2011-07-29
> **sks24 said:**
> Thanks bodhi.zazen,

If I selected "Download all updates in the background," would the Update Manager pop up when the downloads were done?

I am not sure , sorry

---

### Post by sks24 on 2011-07-29
Sorry to pester you with all this.  I'll set my machine to one then the other and come back and describe what the interface does here.  It's just that he had stopped by with his machine.  But I'll take care of him remotely when I figure all this out.  Forgot I could do that.  
Thanks for your help,
Scott

---

### Post by sks24 on 2011-07-29
"Download all updates in the background" results in:

1) a "Update Manager" notification (I guess?) in the taskbar.  The user must click on that and then
2) the Update Manager pops up and the user must click "Install Updates" and 
3) the user must authenticate with his password.  

I'm afraid many people won't pay heed to the Update Manager in the taskbar.  

What would work - I think - is one action - entering one's user password in a box which would pop-up on the desktop - to enable the downloading and installation of OS updates.  (Or the installation of updates downloaded in the background.)  

Bet there's a browser pop-up exploit possible with that one, tho.

Anyway, I'll see what "Install security updates w/o permission" with only the "Important Security updates only" box (the top one in that list of four on that same tab) checked.  

If that's not what I'm looking for, I'll try w[hat you suggest]("https://help.ubuntu.com/community/AutomaticSecurityUpdates"), and see how that does.

---

### Post by bodhi.zazen on 2011-07-29
Again, I would configure security only automatic updates.

If you need more then that, write a cron script or ssh in.

---

### Post by CharlesA on 2011-07-29
> **bodhi.zazen said:**
> Again, I would configure security only automatic updates.

If you need more then that, write a cron script or ssh in.

I'd also do that. I do the same thing for my server box - allow automatic security updates but ssh in to do normal updates.

---

### Post by sks24 on 2011-08-05
Thank you all very much.  He has a Verizon mifi for Internet, so I'll have to do this next time I'm out there.  But I'll come back and mark "Solved" or check back in if I need a bit of hand-holding.  Maybe I'll do it on my machine.  

Of course, that means I'll actually have to do it.  Why can't I just THINK it and have it happpen?  Life is just not fair.

---

