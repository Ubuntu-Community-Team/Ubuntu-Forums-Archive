---
title: "Should I be concerned?"
date: 2008-01-10
forum: Server Platforms
---

### Post by borahshadow on 2008-01-10
Hello
I have a basic home file server running samba that also runs a LAMP setup just for my home computers.  This computer is isolated from the internet via my router.

Ok now that that introduction is over. Today I came home and noticed my server was down. w\When I asked somebody about it they said they were looking at the pictures stored on it and then the next minute nothing worked.  Due to the recent death of my laptop I really had no linux computer to access the server from. I downloaded PuTTY real quick but it couldn't connect so I tried pinging it but that didn't find the server ether. After checking all the physical network connections I was forced to hard reboot the server after which everything is back to normal.

So what could have caused this when the only activity should have been some samba file browsing.  Should I be concerned that my server decided to randomly crash?

---

### Post by James79 on 2008-01-10
Which version of Ubuntu is it? Have you applied all updates?

Is this an old/repurposed machine? Perhaps consider running a ramtest on it (one is available off the Ubuntu live cd, at the boot up menu).

Just some ideas off the top of my head...

---

### Post by tgalati4 on 2008-01-11
More likely explanation:  Browsing myspace and flash crashed, leaving the computer unresponsive.

---

### Post by borahshadow on 2008-01-12
It is ubuntu 6.06. It is an older machine but it has ran stable for several hundred days recently. I believe it is up to date. It couldn't be flash or anything it is a headless machine and the only thing that was going on or should have been was somebody accessing the shared RAID array through samba.

Again it looked like it just disappeared off the network nothing could see it including the router but after a reboot it worked fine

---

### Post by tgalati4 on 2008-01-13
I assume your server is on an UPS.  If not, it should be.  Otherwise, it could be a wonky power supply.  They do fail or develop intermittent behavior.  For instance, if a disk drive was asleep, and someone requested some files and the drive spun up (making a current surge) and the power supply burped, that would cause a hang.

Check your log files in /var/log.

---

### Post by borahshadow on 2008-01-14
Yes I am on a UPS but it does not have the auto shutdown feature due to no linux support for that model (unless it has changed since the last time I checked NUT). The power supply sounds like a possible cause it is not an expensive one I believe it is just one that came with the case (I know I should probably buy a good one but this was a simple budget server) However what was reported to me was that they were using the server got off for at most 5 minutes and then tried to come back and use it at which it would not let them access it so I doubt that the drive spun down in 5min but I could be wrong. I didn't see anything out of the ordinary in my logs it all looked like messaged that would have appeared during boot time but then again I'm not an expert system admin (if I was a good system admin I wouldn't be asking here :))

---

### Post by tgalati4 on 2008-01-15
When you get a spontaneous shutdown without any droppings in /var/log that is usually a good indicator of a hardware problem.

On my Dapper server, I cleaned out the case (a lot of dust accumulates after a year of 24/7 operation) and I found that the power lead to the hard drive was loose from vibration.  It was easy to push on and pull off--it looked like metal fatigue inside the connector.  I swapped it with another lead.  

After cleaning, reseating the RAM is a good idea.  Of course it could have been a cosmic ray that   sliced through the data bus.  No decent prevention for that except a tinfoil hat and several hundred meters of earth underground.  That takes care of the cooling problem as well.

---

### Post by borahshadow on 2008-01-15
ok well I'll check my case for dust and stuff but it sounds like unless it started happening again I'm fine.


Thanks

---

