---
title: "New Serval.. application crashes cause X reset"
date: 2010-05-01
forum: System76 Support
---

### Post by reid_rsv869 on 2010-05-01
Hello Group -

I have a new Serval which I love but I'm having trouble with several applications crashing, which then also causes X to reset. 

It first started with the Chrome browser almost immediately after I got the machine about a week ago.   Thought it might have been fixed by getting more current releases of Chrome through nightly updates, but that hasn't made any difference.  Happened three times in five minutes last night.

Then it happened with Firefox, and then this morning it happened twice with FSpot.  That was really surprising.

One way I thought I might be able to troubleshoot is by starting this applications from the terminal command-line and looking at the command-line output when it aborts, but since X crashes, too, it also crashes the terminal program.  

If you think I'm on the right track, but have an idea how to save the output, or if there's a log file I can use to diagnose, just let me know.

Thanks

Reid

---

### Post by reid_rsv869 on 2010-05-01
added info -

running version 9.10

could this actually be a display driver issue?  I have added the Sys76 drivers, just BTW.

Reid

---

### Post by thomasaaron on 2010-05-03
Hi, Reid. If it were just Chrome crashing x, I wouldn't be surprised, I guess. But Firefox and Fspot shouldn't crash anything.

Go to System > Admin > Hardware Drivers and make sure your nVidia driver is enabled.

If that doesn't fix it, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by reid_rsv869 on 2010-05-03
Tom -

The logs are attached. Most recent X-crashes were on 5-1.  As for the Hardware drivers, they've been loaded since day-1.  

Thanks

Reid

---

### Post by thomasaaron on 2010-05-03
Thanks. I don't see anything glaring, but I'm not sure what time the xorg reset occured.

There are a couple of flash segfaults on the 2nd.

Please recreate the logs when it occurs again, and let me know what time you log back in so I can try to home in on the problem.

---

### Post by reid_rsv869 on 2010-05-09
Hello Group -

After loading 10.4 I was hoping this problem would go away.  But no.  Initially this problem seemed related only to the Chrome browser but I believe now that may be a red herring (even though it can cause the symptom).

For example, this morning my daughter was playing a game called Free Tennis (Chrome wasn't even loaded in the background) and it reset.  The other day VirtualBox was running and it reset. 

Need some ideas to help me troubleshoot.  

Thanks

Reid

---

### Post by thomasaaron on 2010-05-10
Hey, Reid.

Talked to you on the horn this morning. Did you try *re-seating* your memory cards. I know you ran memtest with no errors, but it's possible that the problem is being triggered by the machine being moved around... maybe a card is loose.

I'll look at the logs you emailed. But if it's not loose mem cards, I'm thinking... hardware.

---

### Post by reid_rsv869 on 2010-05-17
Hi Tom -

Had a few X resets over the weekend.  I reseated the memory cards and saw no change.  Just had one again this morning.  So... looks like hardware to me, too.  I've been running Ubuntu for several years and linux more than 10 and have never had this kind of problem.  Has to be hardware, somewhere, somehow.

Will you please forward me the necessary shipping info?

Thanks

Reid

---

### Post by thomasaaron on 2010-05-17
Bringing this one in.

---

