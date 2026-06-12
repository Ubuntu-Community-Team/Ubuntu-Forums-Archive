---
title: "My new machine, some experiences"
date: 2009-08-24
forum: The Cafe
---

### Post by hwttdz on 2009-08-24
I didn't know where to put this but I've learned a lot in the past few days so I thought I'd share.

First my goals, so when I explain what I did it makes some sense.  My old machine was quite loud, and additionally it was probably a power hog, I'll be able to get some numbers on it sometime soon.  So knowing this some of the goals for the new one were to minimize power consumption and have it run nice and quiet.  Additionally my machine works as a server, and often a remote host for cpu bound computations, so it's on almost constantly, and cpu power is a big plus.

Goals:
1) low power
2) quiet
3) lots of cpu power

Conviently 1 & 2 go together quite well.  Most of the noise of a machine is from fans and the cooler running components the fewer fans are needed.  I chose an intel quad core 65w processor @ 2.83 GHz, this is the lower total power version, though after building it I read an article that stated if the equivalent 130w processor is undervolted they run very similarly.  Oh well.  I undervolted it a bit, but my bios doesn't give very fine control, so I was likely unable to undervolt it to the limit of the processor.

Going against the above I still need lots of cpu power (I kept all four cores busy for approximately 30 hours doing a set of molecular mechanics simulations almost immediately after building it).  So after undervolting a bit, I decided to overclock.  I probably could have gone further towards either a faster clock or a lower voltage processor if I did both in tandem, but I felt this was a good compromise.  I was left with a cpu running at 95% voltage and 110% speed (or thereabouts). 

In order to keep things quiet and cool I looked for fans with high airflow and low sound ratings.  In retrospect I might have chosen a different brand of fan, since those are far and away the loudest thing, but I think I can deal with two case fans.  In order to keep the processor very cool I used an aftermarket zalman cooler, which keeps it at room temp 22-24C at idle and 30C when at 100% load.  It's absolutely silent and I would definitely choose it again.

I did not go with an onboard graphics solution and I am instead running a 9400GT card made by sparkle which is fanless and therefore quiet.  Looking at nvidia-settings I could see that the card was running quite hot (around 50C, I realize this is a fine and safe temperature), and given that I don't often do graphics intensive tasks and oftentimes I'm even logged in remotely I decided to underclock said graphics card. Here's some info on how to do that
[http://ubuntuforums.org/showpost.php?p=5274719&postcount=3](http://ubuntuforums.org/showpost.php?p=5274719&postcount=3)
I was surprised how little difference a substantial underclock made on the temperature but once I get my killawatt I'll be able to figure out how much of a difference it makes on energy consumption.  

I also set up a local SGE queue, which for me is quite useful, I chose sge mostly because most of the other machines I have to work on use sge, so it's convenient.  To install that you just need to check the gridengine packages or sudo apt-get install gridengine, then if you use qmon you can graphically set up your queue.  I put 4 slots in the queue and it assigns one job to each of the 4 cpus. 

I'm quite satisfied with the new build, ubuntu certainly helped me to get the most out of it, hardinfo provided valuable information about my hardware, reclocking the video card could not have been easier, powertop helped me identify places where I could use less power, sge was extremely easy to set up and has already helped me get a lot of work done.

---

