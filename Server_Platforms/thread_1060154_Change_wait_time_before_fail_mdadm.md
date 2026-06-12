---
title: "Change wait time before fail mdadm"
date: 2009-02-04
forum: Server Platforms
---

### Post by electrofreak on 2009-02-04
I've been having various issues with my Samsung hard drives in a raid-5. After several days of research, I finally came up with what I really think the problem is.

I was reading this white paper: [http://www.samsung.com/global/business/hdd/learningresource/whitepapers/LearningResource_CCTL.html](http://www.samsung.com/global/business/hdd/learningresource/whitepapers/LearningResource_CCTL.html)

Down where it talks about using desktop drives in a raid... what it basically says is that the drive tries to recover when it can... and it can take too long to do that which causes the raid controller (mdadm) to assume it failed and drops it from the array. Typically this is 8 seconds, which I assume is also the default for mdadm.

So... then I read the man pages for mdadm and I can't find any way to change the wait time before mdadm assumes the drive has failed.

My thinking is that if I simply increase this wait time, then the drive should recover from whatever its problem is and it wont drop out of the array.

In case it's relevant... I'm working with a raid-5 of three 750GB Samsung HD753LJ.

Also... if some one knows how to change this wait time... would you have any good recommendations of what time would be appropriate? I was thinking 15-30 seconds.

---

### Post by fjgaude on 2009-02-05
Interesting... from all the literature I've read I've not seen anything that would lengthen the delay time. Neil Brown is the author of **mdadm** but I don't know if he is active in bug issues and the like.

The best links I have regarding mdadm are:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

[http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing](http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing)

[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

This link might work for access to Neil Brown:

[http://www.cse.unsw.edu.au/~neilb/patches/linux-stable/](http://www.cse.unsw.edu.au/~neilb/patches/linux-stable/)

Sorry I can't be of more help, but do let us know if you find anything useful.

---

### Post by electrofreak on 2009-02-05
Thanks for the reply.

I will look into the pages you linked to.

For those curious... Essentially, 2 of the 3 drives ended up having bad sectors...which don't fair well when in a RAID. Apparently, zeroing over the problem drives actually fixed them (I've done extensive testing and they seem to be fine now...for now anyway).

Yes, I lost data, but I keep back-ups of the critically important stuff, so all is fine there.

But I fear the future at this point because it is very possible for it to happen again :(

Next time I will buy RAID-specific drives, tho.

In the process, I learned a LOT about RAID, tho... and I feel more confident that before that second drive dropped out of the array (during the recovery attempt I made when I assumed the first drive was fine)... I was actually able to recover data.

RAIDs are very reliable and robust... but faulty drives can be a problem.

---

