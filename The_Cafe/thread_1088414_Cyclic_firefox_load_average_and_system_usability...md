---
title: "Cyclic firefox load average and system usability..."
date: 2009-03-06
forum: The Cafe
---

### Post by kline on 2009-03-06
Awhile ago I posted a query asking what was going on with firefox[3]: why, e.g., it was soaking up 98% of the processor and making work difficult or impossible.  A few hours ago [[ well, maybe 5 hours ago ]] I ran a sh script and uptime while firefox was sitting idling.  It was open only to marketplace.org.

FWIW:: the load average was up to 98.4% for the past 20 minutes and rendered even this app worthless.  Zero response from the keyboard.

I gathered a lot of data from the couple hours of running and caputing uptime data.   Part of it is commented.   I've begun to see if my running ff3 and miro simultaneously contribute to this bizarre behavior.  I'll let you guys know.  But if you want my help with this bug--whatever it is--please send me email offline.  _Also_, since this is a non-tech forum, please tell me which is the best directory/forum...

tia, guys


gdk

---

### Post by swoll1980 on 2009-03-06
> **kline said:**
> Awhile ago I posted a query asking what was going on with firefox[3]: why, e.g., it was soaking up 98% of the processor and making work difficult or impossible.  A few hours ago [[ well, maybe 5 hours ago ]] I ran a sh script and uptime while firefox was sitting idling.  It was open only to marketplace.org.

FWIW:: the load average was up to 98.4% for the past 20 minutes and rendered even this app worthless.  Zero response from the keyboard.

I gathered a lot of data from the couple hours of running and caputing uptime data.   Part of it is commented.   I've begun to see if my running ff3 and miro simultaneously contribute to this bizarre behavior.  I'll let you guys know.  But if you want my help with this bug--whatever it is--please send me email offline.  _Also_, since this is a non-tech forum, please tell me which is the best directory/forum...

tia, guys


gdk
 While running firefox my processor hovers around 2%, and my load is 0.10 What kind of processor do you have.

---

### Post by jdong on 2009-03-06
Sometimes a nasty sqlite database can lead to that too. Although it's a pretty hackish workaround, I've found that clearing the history periodically helps, or at least trimming it down to the past couple days when you notice extreme slowness.

Not the ideal solution but this problem has only cropped up for me twice in all the time I've been using Firefox 3 since early alphas.

---

### Post by kline on 2009-03-06
> **swoll1980 said:**
> While running firefox my processor hovers around 2%, and my load is 0.10 What kind of processor do you have.

10, 12 minutes ago my firefox3 screen was black--[[i was KVM'd elsewhere]]. top was eunning on the konsole; the load for ff was around 97% (cpu).  i managed to do a ksnapshot that i will send/post/glue in tomorrow.  Also will post my file of load averages.  The only thing that's running is the browser and one instantiation of konsole.       two or three times per hour the load goes from or near 0.00 to over 1.00.

i'm stumped.

the box is an AMD 2.8GHz.  1G of DDR, close to 200G of disk drive.  

Note that I just installed 8.04 on my Thinkpad [3GHz, 120G disk, 2Gigs of memory]  i'm still stress-testing the old / used laptop, but so far, no problems.

more later; time to get something called *sleep**.  Bizarre.  the cpu hit 98% for around 15 minutes and just suddentky dropped to 0.7%.

better post this before things hang up again.

---

### Post by MaxIBoy on 2009-03-06
I know you're probably not using the live CD, but if you are, the system could easily be prone to major slowness.

Also, do you have any add-ons/plug-ins on Firefox?


Until you get your problems with Firefox ironed out, try using a different browser. You can go to the "add-remove programs" app, and search for "web browser." There are several options. I'd recommend trying either Opera or Epiphany. (Note that the Gecko version of Epiphany uses a lot of the same under-the-hood code as Firefox, so if Firefox doesn't work for you, you should try the non-gecko version of Epiphany.) Both browsers run a little more lightweight.

---

### Post by ssam on 2009-03-06
you could turn down the time history is stored for. i think firefox 3 increased it from 30 to 90 days.

it could also be caused by animations and flash. if you set gif to only play once, that helps. and either remove flash or install the flashblock plugin.if you want to go further try the noscript plugin.

---

### Post by kline on 2009-03-06
> **MaxIBoy said:**
> I know you're probably not using the live CD, but if you are, the system could easily be prone to major slowness.

Also, do you have any add-ons/plug-ins on Firefox?


Until you get your problems with Firefox ironed out, try using a different browser. You can go to the "add-remove programs" app, and search for "web browser." There are several options. I'd recommend trying either Opera or Epiphany. (Note that the Gecko version of Epiphany uses a lot of the same under-the-hood code as Firefox, so if Firefox doesn't work for you, you should try the non-gecko version of Epiphany.) Both browsers run a little more lightweight.

I have some plugins/addons.  One checks the weather [and is broken], another is FoxVox [ tts reader (python) ].  I'll de-install these.

I do use konq because it lets me use the festival tts capability and is built-in.  I'll add both Opera and Epiphany.   Will post results.

my first thought (after a long nap + 27 cups/coffee) was Some Kind of Systems Bug.  posting now before things hang.

---

### Post by linuxisevolution on 2009-03-06
It hangs because of too many i/o to the hard drive. It's a well-known bug. I just use a fast file system and it works fine. Watch your hard drive light on your pc the next time it happens.

---

### Post by kline on 2009-03-06
Can't find the Opera browser (via Synaptic).  Have installed Epiphany.  What's the magic to install opera, by apt-get or other. 

[[ things were hung for several minutes ]]  also, i just got a note that ff3 has been updated.  maybe a fix that was backported [?]

---

### Post by kline on 2009-03-06
> **linuxisevolution said:**
> It hangs because of too many i/o to the hard drive. It's a well-known bug. I just use a fast file system and it works fine. Watch your hard drive light on your pc the next time it happens.

Are you saying that somebody has ported the Berkeley FFS to Linux?!  How to I install this?

---

### Post by happysmileman on 2009-03-06
> **kline said:**
> Can't find the Opera browser (via Synaptic).  Have installed Epiphany.  What's the magic to install opera, by apt-get or other. 

[[ things were hung for several minutes ]]  also, i just got a note that ff3 has been updated.  maybe a fix that was backported [?]

They offer Ubuntu packages at Opera.com, not sure if there's a repo

---

### Post by kline on 2009-03-06
> **happysmileman said:**
> They offer Ubuntu packages at Opera.com, not sure if there's a repo

i'll check at their site, thanks.  i'd think if they have a port or pkg, it would be available more easily.

at any rate, when i got back to my desk earlier there was a small lightbulb that said that a new fix for firefox3 had been installed; that i needed to restart firefox.

i did close and restart firefox and at the same time, i set off my tackload.sh script.  for close to an hour, the system load average never went over 0.12.  --this While firefox was running, open only to my home html hotlist.html.  does this mean that that "fix" resolved the I/O bug, the hang-bug?  i have no idea; but i'll be very happy if it is fixed.

thanks for the pointer to opera.com v9.64.2 is installed.  now i've got two ways of checking this hang bug.

:)

---

### Post by kline on 2009-03-06
okay, i have both firefox and opera going.  plus the ff bugfix in.  that may have been it.  i'll post a final question here and exit.

i'm thinking of switching to ubuntnu for all my desktops, but need to understand if there were a more appropriate place for this kind of post/question.  i couldn't decide from the ubuntuforums.org/ homepage which forum was the best... so just chose this one and hoped that nobody would be TOO ticked off.  (i would like some kind of hackers/geek/techy forums for busted apps or better filesystems or whatever... .  you know.)

thanks.

---

### Post by Mohamedzv2 on 2009-03-06
The only problem I face with Firefox 3 is it crashes for often than FF 2

---

### Post by kline on 2009-03-06
> **Mohamedzv2 said:**
> The only problem I face with Firefox 3 is it crashes for often than FF 2

You probably should start a new post with an appropriate Title/Subject line.

---

