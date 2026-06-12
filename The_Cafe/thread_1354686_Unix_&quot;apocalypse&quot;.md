---
title: "Unix &quot;apocalypse&quot;"
date: 2009-12-14
forum: The Cafe
---

### Post by scottuss on 2009-12-14
No idea why they randomly chose to talk about this now, but the BBC have a quick mention on 32 bit UNIX date issues...

[http://news.bbc.co.uk/1/hi/technology/8408838.stm](http://news.bbc.co.uk/1/hi/technology/8408838.stm)

---

### Post by HappinessNow on 2009-12-14
> **scottuss said:**
> No idea why they randomly chose to talk about this now, but the BBC have a quick mention on 32 bit UNIX date issues...

[http://news.bbc.co.uk/1/hi/technology/8408838.stm](http://news.bbc.co.uk/1/hi/technology/8408838.stm)
the paper batteries were interesting. :P

---

### Post by insane_alien on 2009-12-14
hasn't this issue largely been dealt with? and really, by the time this rolls round, most systems running a 32-bit unix system will have been replaced. either due to a failure, the purpose simply doesn't exist anymore or they are no longer fit for purpose due to other upgrades.

the few that remain probably won't be too dependant on time, sure there might be a few log errors. but i doubt it would be anything requireing a reboot.

just out of interest, has anyone ever set a system to a few minutes before the cycle time and seen what happens? i think i'll go try this now.

---

### Post by Exodist on 2009-12-14
> **insane_alien said:**
> hasn't this issue largely been dealt with? and really, by the time this rolls round, most systems running a 32-bit unix system will have been replaced. either due to a failure, the purpose simply doesn't exist anymore or they are no longer fit for purpose due to other upgrades.

the few that remain probably won't be too dependant on time, sure there might be a few log errors. but i doubt it would be anything requireing a reboot.

just out of interest, has anyone ever set a system to a few minutes before the cycle time and seen what happens? i think i'll go try this now.


We will never see you again.. j/k... :D

---

### Post by HappinessNow on 2009-12-14
> **exodist said:**
> we will never see you again.. J/k... :dlol!

---

### Post by scottuss on 2009-12-14
insane_alien: you really are insane!
 
You've broken the interwebs now

---

### Post by Yes on 2009-12-14
> **insane_alien said:**
> hasn't this issue largely been dealt with? and really, by the time this rolls round, most systems running a 32-bit unix system will have been replaced. either due to a failure, the purpose simply doesn't exist anymore or they are no longer fit for purpose due to other upgrades.

the few that remain probably won't be too dependant on time, sure there might be a few log errors. but i doubt it would be anything requireing a reboot.

just out of interest, has anyone ever set a system to a few minutes before the cycle time and seen what happens? i think i'll go try this now.

Do it with a live CD, not an actual install.  Or better yet, in a VM.  IIRC someone else here tried it and it actually screwed some things up kinda bad.

---

### Post by insane_alien on 2009-12-14
i have just replaced my server, give us a bit to install a working system on the old box(i've been messing about with it, currently running win95 for nostalgia and bluescreen purposes.)

i don't care if it gets bricked(even the local library won't take it for free) so i might as well try it on real hardware.

the vm idea would be good for those wanting to do it without having spare antiquated hardware available.

---

### Post by HappinessNow on 2009-12-14
> **insane_alien said:**
> i have just replaced my server, give us a bit to install a working system on the old box(i've been messing about with it, currently running win95 for nostalgia and bluescreen purposes.)

i don't care if it gets bricked(even the local library won't take it for free) so i might as well try it on real hardware.

the vm idea would be good for those wanting to do it without having spare antiquated hardware available.
good to see your still alive! :P

---

### Post by insane_alien on 2009-12-14
still installing. ubuntu is a bit sluggish on 500MHz and 64MB of RAM

---

### Post by HappinessNow on 2009-12-14
> **insane_alien said:**
> still installing. ubuntu is a bit sluggish on 500MHz and 64MB of RAM
try puppy

---

### Post by insane_alien on 2009-12-14
its almost done. can't be bothered giving up and trying something else

---

### Post by meho_r on 2009-12-14
Hey, don't forget to unplug the cable when you finish the installation, you don't wanna bring the Internet down, do you? Or kill some innocent birds? Or get us into another ice age? Or... I go find some coffee.

---

### Post by insane_alien on 2009-12-14
well, no crashes. updates even worked.

thinks its 1901 but still, that seems to be the only problem and its not causing anything critical to system stability to malfunction.

---

### Post by benj1 on 2009-12-14
> **insane_alien said:**
> well, no crashes. updates even worked.

thinks its 1901 but still, that seems to be the only problem and its not causing anything critical to system stability to malfunction.

wouldn't it think it was 1/1/1970 ?

---

### Post by insane_alien on 2009-12-14
nope. its a singed integer.  0 is in 1970 but it went backwards as well down to friday the 13th of december at ~8:50pm [http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)

---

### Post by scottuss on 2009-12-14
Maybe *cough* someone *cough* is just starting to get a foot into the media to start the FUD campaign about how you shouldn't use UNIX or UNIX like Operating Systems because in the year 2038 ALL YOUR DATA WILL BE GONE!!! OMG!!!

---

### Post by benj1 on 2009-12-14
> **insane_alien said:**
> nope. its a singed integer.  0 is in 1970 but it went backwards as well down to friday the 13th of december at ~8:50pm 

i did think about that but then i thought it would be a bit silly for a signed number to wrap around and flip the signed bit, although having just played it seems this is standard, well you learn something new every day:)

---

### Post by fromthehill on 2009-12-14
everything is fine on december 13 1901 21:05 :D

---

### Post by insane_alien on 2009-12-14
okay, i'm actually astounded  by the stability of this. i haven't found a single problem(except for the clock displaying a time over a century in the past). then again, i'm just doing normal user stuff(browsing, word processing, listening to some tunes etc.). 

i imagine there are some date dependant applications, but it would seem to me that these aren't likely to be embedded systems that stand a chance of still being in service in 2038. the big problems would probably be in enterprise servers whichwill have been turned over several times by then. plenty of opportunity to transfer to 64-bit if they haven't already due to the limitations of 32-bit(even with PAE) 4GB/64GB with PAE RAM isn't so much in that environment.

---

### Post by fromthehill on 2009-12-14
> **insane_alien said:**
> okay, i'm actually astounded  by the stability of this. i haven't found a single problem(except for the clock displaying a time over a century in the past). then again, i'm just doing normal user stuff(browsing, word processing, listening to some tunes etc.). 

i imagine there are some date dependant applications, but it would seem to me that these aren't likely to be embedded systems that stand a chance of still being in service in 2038. the big problems would probably be in enterprise servers whichwill have been turned over several times by then. plenty of opportunity to transfer to 64-bit if they haven't already due to the limitations of 32-bit(even with PAE) 4GB/64GB with PAE RAM isn't so much in that environment.

when I tried maxing out the time windows I had some problems:
on some forums or blogs posts posted in the future didn't show up.
when grouping files in a folder on date created/modified everything would be in "in the very far future" group.
virusscanner(with one year subscribtion) breaks immediately. can't be restored.
30 day timer to activation drops to 0. can only get to the desktop by opening explorer.exe in IE.
for once no updates :D

---

### Post by scottuss on 2009-12-14
I guess it was just a slow tech news day.

---

