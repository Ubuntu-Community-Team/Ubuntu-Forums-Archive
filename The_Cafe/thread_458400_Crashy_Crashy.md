---
title: "Crashy Crashy"
date: 2007-05-29
forum: The Cafe
---

### Post by verevi on 2007-05-29
I've been having frequent lock-ups until one day my PC would power up but do nothing.  I took out the memory and put it back in, and it still starts up but crashes a lot.

Everything crashes this thing including knoppix, ubuntu studio, etc... It also started doing a small "chirp" sound before the normal startup beep.  Clearly I have a problem.  I assume my Mother Board is dying.  Is there a way to tell what the problem is?  Is it the CPU?  MB?  (I did a memtest, and everything seems fine there).  Vid Card?  

I know this is not Ubuntu related, but I haven't had HW problems in YEARS.... So, I don't know where else to ask.  Plus, I like Linux-friendly answers as I don't care to run Windows tools to investigate this problem.

Thanks for any tips, pointers, or suggestions.

---

### Post by meng on 2007-05-29
Try running the memtest from a LiveCD, then you should know if you have bad RAM.

---

### Post by verevi on 2007-05-29
> **meng said:**
> Try running the memtest from a LiveCD, then you should know if you have bad RAM.

I did the memtest from a liveCD thing...  There were no mem problems.  I was kind of surprised.

---

### Post by meng on 2007-05-29
> **verevi said:**
> I did the memtest from a liveCD thing...  There were no mem problems.  I was kind of surprised.
Crud, I didn't read your initial post properly. Shame on me!

---

### Post by smoker on 2007-05-29
hi, have you checked your power supply, if you have another handy, you could maybe swap them to try,

best of luck

---

### Post by stmiller on 2007-05-29
> **verevi said:**
>  It also started doing a small "chirp" sound before the normal startup beep.  

Power supply. They chirp when they are about to go, funny enough. :)

---

### Post by verevi on 2007-05-30
Although the power supply might be going out, I did find something that stopped the crashing.  If I remove the second memory stick (which seems to get very hot), the thing never crashes.  (I can use either stick, but only in the first slot).  

I think the memory slot is weird even though the memtest checked out.  I think it gets too hot or something.  Which has never been a problem in the past...  Oh well, this week another PC of mine crashed (the old ASUS MOBO just gave up the ghost.)  

I haven't had this many hw failures in years!  I wonder if my new house has more moisture and heat?  

Anyway, thanks again for all who gave suggestions. They are very much appreciated.

---

### Post by maniacmusician on 2007-05-31
> **verevi said:**
> Although the power supply might be going out, I did find something that stopped the crashing.  If I remove the second memory stick (which seems to get very hot), the thing never crashes.  (I can use either stick, but only in the first slot).  

I think the memory slot is weird even though the memtest checked out.  I think it gets too hot or something.  Which has never been a problem in the past...  Oh well, this week another PC of mine crashed (the old ASUS MOBO just gave up the ghost.)  

I haven't had this many hw failures in years!  I wonder if my new house has more moisture and heat?  

Anyway, thanks again for all who gave suggestions. They are very much appreciated.
how long did you run the memtest for?

a 24 hour memtest is probably a reasonable amount of time to run the test, and a 3 day memtest would be an extremely thorough test.

---

### Post by FuturePilot on 2007-05-31
> **maniacmusician said:**
> how long did you run the memtest for?

a 24 hour memtest is probably a reasonable amoun tof time to run the test, and a 3 day memtest would be an extremely thorough test.

You mean you're supposed to run Memtest for 24 hours:o I never knew that. What do you do in the meantime?

It sounds like either you have a bad stick of RAM or there's something wrong with the slot.

---

### Post by maniacmusician on 2007-05-31
> **FuturePilot said:**
> You mean you're supposed to run Memtest for 24 hours:o I never knew that. What do you do in the meantime?

It sounds like either you have a bad stick of RAM or there's something wrong with the slot.
I have the luxury of owning various computers, so I just use a different one. If I only had the one, I would just go to sleep.

---

### Post by verevi on 2007-05-31
I ran memtest for 11 hours and I thought that was WAY more than needed.  I didn't realize that it needed to be run longer than that.  I just thought it was doing the same thing over and over.  I'll try running it for longer to see if anything pops up.

---

### Post by Bigbluecat on 2007-05-31
I would suggest that you also check the hardrive although the memory does sound suspicious. You should be able to download the manufacturers diagnostic tools from their web site.


I had a hard drive failure on my windows drive. Started with crashes that gradually got worse then failed completely.

---

