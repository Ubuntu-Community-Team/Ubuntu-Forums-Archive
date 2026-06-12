---
title: "[SOLVED] Server's multitasking abilities with a VIA C7-D 1.5 GHz"
date: 2008-04-20
forum: Server Platforms
---

### Post by Palu on 2008-04-20
I bought the Everex gPC running gOS (Ubuntu with Enlightenment and a few more modifications and a ton of instability) from Walmart a while ago (oops) and on Thursday I plan on wiping it and installing Ubuntu server edition on it. I have heard a lot of bad reviews against Via in regards to multi-tasking, which seems to be kind of important for a server. Obviously I'm not concerned about a massively powerful server or I wouldn't be using the $198 gPC at all... but I was hoping someone in this forum has tried running a server on Via chips, or VIA C7-D 1.5 GHz specifically and could comment on performance versus an AMD or Intel attempt at similar hosting demands. Thanks!

---

### Post by volkswagner on 2008-04-20
> **Palu said:**
> I bought the Everex gPC running gOS (Ubuntu with Enlightenment and a few more modifications and a ton of instability) from Walmart a while ago (oops) and on Thursday I plan on wiping it and installing Ubuntu server edition on it. I have heard a lot of bad reviews against Via in regards to multi-tasking, which seems to be kind of important for a server. Obviously I'm not concerned about a massively powerful server or I wouldn't be using the $198 gPC at all... but I was hoping someone in this forum has tried running a server on Via chips, or VIA C7-D 1.5 GHz specifically and could comment on performance versus an AMD or Intel attempt at similar hosting demands. Thanks!

Many folks run mythtv on these systems for quite and low power/heat.  If you run a server install with no gui you will have ample processing power.  How much ram do you have?  Having more ram will help with multitasking.  IMHO 256meg would be a minimum starting point for a speedy server on ubuntu.  I have run Ubuntu desktop 7.10 on amd700mhz 384meg ram with very usable speeds.

I guess the big question is what are the multiple tasks you want to perform at the same time?

---

### Post by Palu on 2008-04-20
Well, it has 900-some GB RAM because it came with 512 MB and I added 1024 MB but instead of showing 1.5 GB it shows 900-some during boot. Honestly I don't care a ton at the moment because I need to tackle other things first. :)

The processor is 1.5 GHz, so it sounds faster than the one you mentioned, but I recall a comment on another forum where a user said a 700 MHz AMD was 5 times the benchmark score as a 1.5 GHz Via in areas that included multi tasking.

My server will be used for a number of things--setting up a local network to serve music and a file share for everyone in my house, running an online 2D MMORPG (more as a test of my abilities, but others I know play it frequently), and an ftp server. That could be fairly light, but at times there will be a number of things going on at once.

---

### Post by ikonia on 2008-04-20
only time will tell, as those things are not really "hard" things on the cpu but something thats light used 1000 time by users still = work.

---

### Post by Palu on 2008-04-20
I was hoping for people with specific Intel or AMD vs. Via experiences to share performance evaluations of their own, but I suppose this thread has been very helpful as is. Thank you! :popcorn:

---

### Post by ikonia on 2008-04-21
the performance of an Intel/AMD current model will be better than a via - as I've said though it depends on what your doing and in what situation how scalable your current solution will be.

My results with VIA chips against my intel machines will be different to yours, different hardware, different tasks, different loads as will the others, all people can do is explain the differences and how it effects your setup potentially, it's up to you to work out how well you think it will scale. 

Do some load tests to get an idea if your worried.

---

### Post by far_frum_h0me on 2008-04-21
I have one of the low power boards and for the life of me can't remember/find the model number. The clock speed is around 1.5. I'm running a Ubuntu 7.10 server with a software RAID5 and ssh server with no problems. I also make the most of the CPU time I'm also running HandBrake in the background. This server only has a few connections. Just to give some numbers HandBrake on a Intel Core Duo takes about 3 hours to convert home movies, were on this system takes about 8 hours. Because it just sitting there, I don't care how long it takes. It's a headless system with on DVD drive with 3 750GB drives and 2GB of RAM. I have no problems out of this system.

---

### Post by Palu on 2008-04-21
> **far_frum_h0me said:**
> I have one of the low power boards and for the life of me can't remember/find the model number. The clock speed is around 1.5. I'm running a Ubuntu 7.10 server with a software RAID5 and ssh server with no problems. I also make the most of the CPU time I'm also running HandBrake in the background. This server only has a few connections. Just to give some numbers HandBrake on a Intel Core Duo takes about 3 hours to convert home movies, were on this system takes about 8 hours. Because it just sitting there, I don't care how long it takes. It's a headless system with on DVD drive with 3 750GB drives and 2GB of RAM. I have no problems out of this system.

That's about what my system will look like too--though probably less storage. Nice storage. :) I've had no interaction with Via based servers whatsoever, so I have never figured out how "low end" it is. I think it'll work at least for my initial phases--if not further. Thanks. I'll mark this solved, I suppose.

---

