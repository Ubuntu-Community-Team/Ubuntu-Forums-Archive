---
title: "youre kidding me right?"
date: 2010-01-03
forum: The Cafe
---

### Post by phillychease on 2010-01-03
what is this?!
16 hrs to rip a DVD?!

---

### Post by Georgia boy on 2010-01-03
Damn! What have you got on that thing?

---

### Post by Barrucadu on 2010-01-03
Woah.

---

### Post by paparozoumis on 2010-01-03
I don't want to hijack your thread... but.. ..what is that program on the right side of your screen called? :O

---

### Post by alakazam on 2010-01-03
My goodness, that's a long porno.

---

### Post by kyuubi777 on 2010-01-03
> **paparozoumis said:**
> I don't want to hijack your thread... but.. ..what is that program on the right side of your screen called? :O
i believe it's conky with some editing done to the config.

---

### Post by Vignesh S on 2010-01-03
OMG, there's no way it could take that long. How fast is your CPU anyway? That might be why.

Yeah, I've done DVD ripping before, and it only took like 5 minutes :-O. I think that CPU was 2.0GHz Dual Core.

But still, 16 HOURS??? That's impossible. I'd only see that on my ancient IBM Thinkpad R31, and DVD ripping would probably crash it :-P

---

### Post by Barrucadu on 2010-01-03
> **Vignesh S said:**
> Yeah, I've done DVD ripping before, and it only took like 5 minutes :-O. I think that CPU was 2.0GHz Dual Core.

5 minutes on a 2GHz machine? That's impossible&#8212;unless it wasn't encoded into a different video format and just left as a series of VOB files.

---

### Post by Marlonsm on 2010-01-03
Ripping does take long, but not THAT long. Maybe there is some other process going on taking up CPU cycles. Open the system monitor and check if there is something taking up the CPU.
On my 1st gen Core 2 Duo it takes some minutes...

---

### Post by ubuntu-freak on 2010-01-03
Wouldn't suprise me if Nautilus was doing something to slow it all down.

---

### Post by inobe on 2010-01-03
wrong codecs, single core cpu, missing dependencies, many things could contribute to this.

all that will ever be needed to perform such a task quickly.

dual core cpu
2 gigs ram
medibuntu repo
restricted extras
ffmpeg
handbrake for ripping

done in about 45 minutes

---

### Post by phillychease on 2010-01-03
haha yea. i do have an old computer, maybe 7 years old. 
one cpu. :lolflag:

oh im ripping band of brothers not porno ;] hehe

---

### Post by RandomJoe on 2010-01-03
I have had rips take a very long time before.  Is/was your DVD actually running up to speed at the time?  (Or, another way I can tell, if you have activity lights is the drive being accessed as frequently as usual?)

Sometimes I've found a dirty or scratched disc to be the culprit - clean it off, and it runs quickly.  But I've also had some discs that just didn't like one of my drives.  The machine I do most rips on has two drives, if one doesn't work the other usually does just fine.  No idea why!

---

### Post by NoaHall on 2010-01-03
It will depend mainly (hardware wise) on -

Your CPU, and if the software you use to rip is optimized for multiple cores
Your RAM speed, not so much the size - 1 GB per 1 rip
Your storage read/write speed
Your motherboard
Your DVD drive speed

As for software wise, use 64 bit.

---

### Post by The Real Dave on 2010-01-03
Rips and burns take SO long in Ubuntu for me, as opposed to in Windows. Its a problem that I've been trying to fix for ages, but can't seem to find a solution. I usually just que up a pair of DVDs (I've two drives) and let them rip and encode over night :)

---

### Post by Shpongle on 2010-01-03
i remember having old computers p2's , with dvd burners i added later and to do video conversions took days , from avi to dvd lol . i cant remember how long it took to rip them tho

---

### Post by mkendall on 2010-01-03
> **phillychease said:**
> oh im ripping band of brothers not porno ;] hehe

Man, that's one long gay porno.

---

### Post by toupeiro on 2010-01-03
If you're using SSD, make sure the burner software is not using it as a write cache area

---

### Post by Exodist on 2010-01-03
Sounds like something is not set correctly.
I had a AMD Athlon 2GHz with 2GB of RAM and it didnt take that long. Maybe 4 hours, but thats it. Try taking a look at the FSTAB file and seeing what the setting are. Doesnt sound like DMA is working correctly.

---

### Post by Marrkk on 2010-01-04
i'm guessing the disc is scratched, fingerprints or some CRC read-error,
not enough to kill the transfer, but causing re-reads and bad I/O throughput. maybe even 40 pin IDE cable when should use a 80 pin / wire (Blue DMA) cable to the drive.
are all discs as slow ?

---

### Post by pwnst*r on 2010-01-04
lol @ the 5 minute post.

---

### Post by madhi19 on 2010-01-04
Seriously I got a single core AMD 64 2.0GHz with 2 GB of Ram and it take my rig less than an hour at worse to rip a DVD. Am using DVD Shrink with Wine. Once am done with the disk it may take 2 or 3 compression (half an hour max each) to reduce the file size. Than it Avidemux or ffmpeg in terminal to convert for my ps3 and maybe a little more compression. So a good quality rip on my old rig is a 3 hours job at the worse.

---

### Post by CharlesA on 2010-01-04
Looks like they are transcoding the DVD, not just ripping it. That is why it's going to take that long.

Just a straight rip takes about 15-20 mins for me.

---

### Post by Khakilang on 2010-01-04
Wow its really a joke to take 16hrs to burn. Have you find what cause the delay? Hope you can share with us when you found the problem.

---

### Post by Gizenshya on 2010-01-04
In my experience it takes longer the smaller the resulting file is, and how high the quality of the resulting codec is.

A simple DVD9->DVD5 takes me 10-15 mins, but that's only because that's as fast as my DVD drive can read.  I haven't tried codig to different file types in a while, but it would take longer (maybe 30 mins I'm guessing?)... but not 16 hours.  I'm going to do some transcoding when I get my Cowon, though ;)

I also noticed it said 1%, so it just started.  That isn't enough time to get a valid measure of how long the entire rip will take.

---

### Post by phillychease on 2010-01-04
> **Koh Kook Loon said:**
> Wow its really a joke to take 16hrs to burn. Have you find what cause the delay? Hope you can share with us when you found the problem.

acutally i havent found out what cause the delay. maybe because i set the settings to rip at high quality? its weird
so i changed it to low. and it takes like 1 hr. but the quality is still pretty good.

---

### Post by madhi19 on 2010-01-08
> **Gizenshya said:**
> In my experience it takes longer the smaller the resulting file is, and how high the quality of the resulting codec is.

A simple DVD9->DVD5 takes me 10-15 mins, but that's only because that's as fast as my DVD drive can read.  I haven't tried codig to different file types in a while, but it would take longer (maybe 30 mins I'm guessing?)... but not 16 hours.  I'm going to do some transcoding when I get my Cowon, though ;)

I also noticed it said 1%, so it just started.  That isn't enough time to get a valid measure of how long the entire rip will take.

This is why my first pass to rip the data off the disk is almost uncompressed. You compress later from the resulting files it a lot faster to do it that way because you don't have the DVD drive speed and copy protection to slow thing down.

---

### Post by forrestcupp on 2010-01-08
Are you trying to run Ubuntu on a Commodore 64? :)

---

### Post by justsomedude on 2010-01-08
> **phillychease said:**
> acutally i havent found out what cause the delay. maybe because i set the settings to rip at high quality? its weird
so i changed it to low. and it takes like 1 hr. but the quality is still pretty good.

Just rip it to your hard drive **without** converting it. 

It'll take 10 - 20 minutes (depending on the speed of your DVD drive) and results in the best possible quality you can get.

---

