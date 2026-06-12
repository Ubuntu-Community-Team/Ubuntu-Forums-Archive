---
title: "Install issues"
date: 2008-12-19
forum: Testimonials &amp; Experiences
---

### Post by tinytim174 on 2008-12-19
Hi,

First off i'll say that when I installed 8.10 3 days ago, it was fantastic.  I was a complete noob, and followed the tutorials and was command line updating and feeling like i was smarter than i actually am.

However, I feel that I hit such a roadblock, that I'v begrudgingly gone back to XP (I can at least install it).

Here's a quick snapshot of what happened - with the aim that someone can resolve it for future (maybe me one day) users.
\pentium 4\3Gh\1G ram\ 775Twin MB \ATI DVBT777(a16ar) tunercard

3 days ago:
-installed 8.10 fine
-updated as per noob forums
-had all sorts of troubles with the ati card, couldn't get /dev/dvb
-irc #linuxtv, ran a cmd > pastebin > was told linux couldnt see tv tuner, probably broken hardware > only way to test run in XP


day 2:
-so i reinstalled xp > dvb-t 777 worked
-reinstalled 8.10
-/dev/dvb appeared
-started getting black screens after reboots
-searched forums, couldn't find anything appropriate
-reinstalled, but from live cd desktop launcher, as straight from cd was giving black screen


today:
-started getting HAL errors after live cd desktop install, at first login
-tried various hal fixes, like ensuring HAL sequence was correct, ensuring autologin not on


Also, I tried getting help on the irc ubuntu channel, but its mayhem there.  I 'waited' as instructed, but ppl would get on, ask a minor technical point(whats a torrent, how do i configure my screen), and get an answer.  I spent 3 sessions over day 2 and today without getting a single response. I got a limited response today after i kept asking Q's.  I know those ppl are volunteering, and good on them.  Just that irc process was absolutely useless for me/my issue.

The bootup problem just doesnt make sense, as it worked fine once, and I'v fresh installed it about 8 times now, but thats just not working.

I'll end by saying I reckon I've got the ability to 'truck on' w/issues, but I hit The Wall.  The level of programming skills was simply well beyond my skills.

I reckon I'v discovered a bug, its just I couldn't get to the GUI to be able to both run a terminal and get to pastebin.

hope this helps

---

### Post by stalkingwolf on 2008-12-19
I would suggest a couple of things.
First check all your hardware connections.  I have one pen drive
that will only work when plugged directly into my USB port and then
only certain ones.  My others work through my hub.

Second dual boot. Run Ubuntu along side or inside windows(wubi install).

Third try using 8.04LTS or 8.04.1 LTS  I have had several occasions
when the previous version worked better.

I have never used the IRQ.  Posting on this forum however you can get almost realtime answers.

I have found that many "hardware issues" can be solved by simply cleaning
and reseating.

---

### Post by Tamlynmac on 2008-12-19
Where did you get the Live CD?
I've had numerous problems when purchasing CD's in bulk. Was an integrity check performed after burning? I also noticed that a slow burn 8 or 16x seems to improve quality.

I agree with stalkingwolf regarding 8.04.
If your video hardware works in XP, then I'd investigate drivers. Have you tried installing 8.04? You could use Envy to add the appropriate ATI driver after install in 8.04. That was the last LTS release and I am still using that version.

---

### Post by tinytim174 on 2008-12-19
> **stalkingwolf said:**
> I would suggest a couple of things. First check all your hardware connections.  
I have found that many "hardware issues" can be solved by simply cleaning and reseating.

thanks, thats a good suggestion. probably good maintenance. don't think  this is my issue as xp doesnt show hardware conflicts.

>  Run Ubuntu along side or inside windows(wubi install).

hmm, i'll see if it installs alongside xp. if it does, maybe it indicates some type of filesystem corruption?

> Third try using 8.04LTS or 8.04.1 LTS  I have had several occasions when the previous version worked better.

I asked that Q (more stable version)on the irc chat, and was told 8.10 was it - but maybe in a few weeks i'll pluck up the courage to give that a full try if the above works.

> I have never used the IRQ.  Posting on this forum however you can get almost realtime answers.

I certainly found a tonne of info on the forums - they are very good.  I hadnt had an answer for 10 hrs (which i agree is a short time really), but i think then the 3 days of trying to install took its toll, and i imagined trying to resolve with 10hrs between posts, and thought no - too impatient.

> **Tamlynmac said:**
> Was an integrity check performed after burning?

yes.  it was the same cd that i had first had the successful install on, as well as testing on another older pc, which is still running 8.10 fine

Next new pc i get, i'll ensure its more linux compatible (no ati bits)

cheers

---

### Post by stalkingwolf on 2008-12-20
> and i imagined trying to resolve with 10hrs between posts, and thought no - **too impatient**.

That is the most common problem.  You see the person that has your answer
might well be on the other side of the world, literally.

To clarify 8.10 is the most current release.  8.04/8.04.1 (the .1 is the first update) is the current LTS ( long term support) version.  The difference being 8.10 will be supported (updates etc) for 18 Mo.  8.04
will be supported for 3 yrs.

Another way to look at it is 8.04 is the stable work aday version and 8.10
and subsequent versions ( released every 6 mo.) are your "bleeding edge" versions.
IMHO If you want bleeding edge you must be willing to bleed.  I currently run 8.04 and 8.10 as a dual boot, with a third partition for testing other distros.

So enjoy and " May the force be with you."):P

---

