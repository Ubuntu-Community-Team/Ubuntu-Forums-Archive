---
title: "random reboots and crashes"
date: 2007-01-09
forum: Server Platforms
---

### Post by drsar on 2007-01-09
I am at the end of my tether: :confused: 

I am running 
Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) 
as a server for pretty much any service that's useful in our group: sshd, apache, mysql, trac. Users run programs like IDL and ImageJ on it and store data. The server runs on a UPS (upsd via serial port).

It conks out in two ways:
(1) it suddenly becomes unresponsive which is why we ask the IT personnel to power cycle it which brings it back to life
(2) it restarts spontaneously much to the irritation of the users.
In both cases there is not the slightest trace in the logs that anything went wrong. In scenario (1) the logs continue after the system is unresponsive, cron jobs do their thing, syslogd sets its MARK's etc. - we just can't log in. In scenario (2) we see a system starting up as if there was a power cut (not a possibility with the UPS though, I think).

Any ideas what could be the matter and what I can do to investigate?
Additional pointer, / has 1GB space left

Any help much appreciated, 
Stefan.

---

### Post by cult hero on 2007-01-10
Sounds to me like a hardware problem, but I don't have enough to go on from your post. If a machine seems to be power cycling randomly even when connected to a UPS the most likely culprit is either a dying power supply or some kind of overheating issue. (A friend of mine had a heat sink that got so caked up with dust it caused the issue.) Honestly though, power supply is most likely. It'll give you hard locks and random restarts. (And if its own fan has failed, it could be overheating itself.)

Is the network adapter built onto the motherboard or is it a separate card?=

Also, I don't know how big the hard drive in the machine is, but going over around 80% capacity on a hard drive can really hurt performance. So if it's like... an 80GB drive and you've got only a gig left, it's time to upgrade! (However, it's likely unrelated to the reboots.)

---

### Post by PetePete on 2007-01-10
i had a computer a while ago which did this (not a server, but principles the same) ... was caused by overheating.

but like cult hero said, PSU is also another possibilty, although in my experiance they either work or they dont !

---

### Post by kebes on 2007-01-10
The one time I had a similar problem, it was the RAM. The ram that was installed on the motherboard required a somewhat high voltage (2V) to operate properly, but that particular motherboard wouldn't supply consistently above 1.75V. Point being, replacing the RAM with a different brand fixed the problem immediately.

I agree with the other posters that this sounds like a hardware problem. I would try using a LiveCD to do a memory test, as bad (or incompatible) RAM may be the problem. Also what is the frequency of these failures? Try leaving the computer booted into the LiveCD for awhile and see if it crashes. (If the LiveCD also crashes, then it's probably a motherboard issue... If the LiveCD doesn't crash, then maybe it is a hard disk issue?)

Good luck.

---

### Post by Modernity on 2007-01-10
I agree with kebes, but with 1 thing appended. If you run LiveCD and it hangs and still gives a problems, then try changing the RAM. Most times if this issue is not an overheating problem, then it usually turns out to be the RAM going bad. Look for overheating and make sure nothing is overheating then change the RAM.

---

### Post by bigken on 2007-01-10
I think this is either bad ram or bad video if it were heat the machine would not hang it would restart constantly the psu I doubt it try removing the video drivers
and removing the ram  using 1  stick at a time  :-k

---

### Post by drsar on 2007-01-10
Thank you guys. I have a few things to go on now. What makes this all a bit problematic is that the frequency is fairly low but sufficiently high to be a nuisance:

reboot   system boot  2.6.15-27-686    Tue Jan  9 13:37          (19:41)
[accidental] reboot   system boot  2.6.15-27-686    Tue Jan  9 13:09          (20:09)
reboot   system boot  2.6.15-27-686    Tue Jan  9 12:06          (21:11)
reboot   system boot  2.6.15-27-686    Sun Jan  7 08:23         (3+00:55)
reboot   system boot  2.6.15-27-686    Mon Nov 27 22:28         (43+10:49)
reboot   system boot  2.6.15-27-686    Wed Nov 22 15:17         (4+10:51)
reboot   system boot  2.6.15-27-686    Wed Nov  1 15:34         (25+10:35)
reboot   system boot  2.6.15-27-686    Wed Nov  1 08:21         (25+17:47)
[...]

For the investigation of the heat issue - are there sensors I could interrogate? 
:edit begin:
Yes there are: lm-sensors - very useful HOWTO at [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
:edit end:
Maybe stressing the poor thing out calculation-wise could trigger this.

I will also swap the memory and see what happens.

Thanks again and I'll get back to tell you how it all unfolded. Stefan.

---

### Post by drsar on 2007-01-26
Hi All, 
Thanks for the help - I have swapped the power supply and although it seemed better (it didn't immediately die when maxed out by a computation) it eventually crashed. I have now replaced the 1GB of memory (DDR II, I believe) and we weren't able to bring it to its knees. Still a little unsure but so far it seems all sorted. 

So in summary, memory was probably the culprit (memcheck not helpful though).

Thanks all,

Stefan.

---

### Post by drsar on 2007-06-20
the pesky crashes came back.

I found something suspicious in the log though:
localhost kernel: [17432335.604000] sky2 eth0: rx error, status 0x27382738 length 0

I have replaced sky2 with sk98lin following instructions at [http://ubuntuforums.org/showthread.php?t=191877&page=2](http://ubuntuforums.org/showthread.php?t=191877&page=2)

Hoping this did it.

Stefan.

---

