---
title: "Server keeps going down"
date: 2008-08-23
forum: Server Platforms
---

### Post by Twizzle on 2008-08-23
I have set up a home server as follows:

Athlon XP 2100 (underclocked to keep cool :) )
768MB RAM (64MB shared with on board video)
3 HDD (320, 250 and 120 GB) set up as 250GB RAID1, 70GB RAID1. 50GB non RAID (all RAID is software)

250GB is /home
70GB is /
50GB is /tmp and /swap (1Gb)

Ubuntu 8.04 server edition, Webmin, Zoneminder and Athcool.

I share the drives with both XP and Ubunut desktop so have setup SAMBA. All computers can access the shared drive fine.

The server /home is set to automount onto my Ubuntu Desktop and again this works fine.

For most of today I have been trying to copy all my media files over to /home. There are aroung 150GB in total and all computers are connected via 10/100 Ethernet through a Linksys router.

I have been dragging and dropping the files over to the server and walking away for an hour or so. Without fail, everytime I come back the server has hung and everything is frozen. I have a monitor and keyboard attached to the server at the moment but the screen stays blank. I cant get in using ssh or webmin and everytime I have to hit the reset switch.

On boot I get messages about the RAID array not being clean (or something similar) and loads of {DRDY ERR} and {ICRC ABRT} messages.

Am I overloading my RAIDed drive by copying this much data over at once?

It is driving me mad - I thought I was ready to plug it all in under the stairs and have a nice hidden server! :confused:

---

### Post by windependence on 2008-08-23
Ahhh the joys of software RAID.

Have you tried killing X and moving this stuff over via the command line? I suspect your out of resources. You got all the software RAID overhead, and then the huge copy, I suspect you are low on RAM. If it locks up again you should open an ssh session and run top to see if your CPU is saturated or your memory is gone. Pay attention to the load averages as well.

Why don't you try SCPing the files over without having the GUI running and see what happens. If it works, you pretty much know the GUI is eating up resources, and I would say probably RAM.

-Tim

---

### Post by Twizzle on 2008-08-23
Thanks for the suggestion, but I don't have X running on the server or even installed.

I just mount the drive and open it on my desktop and then drag and drop to that.

Im a bit confused too though - when it locks up I can't run anything or even ssh into it so I can't check loads etc.

I will look into SCPing and try that (I don't actually know what SCP means but will google it!)

EDIT: Hmm, something is not right. I just left the server for a couple of hours doing nothing and it has locked up again! Is there any way I can look at logs and see why after a reboot?

---

### Post by Twizzle on 2008-08-23
OK, just tried to resume my file transfer from where it last crashed and decided to run top first. As soon as I start to copy the files, my free memory drops to around 6000k from a total of 710124k! I guess you were right and memory is the problem.

I take it that software RAID has an effect on this? If so, do you know how badly this will effect my day to day usage? All i intend to normally do is run Zoneminder ,serve the odd video to a media player (XP box) and do the occasional back up.

---

### Post by windependence on 2008-08-23
Well I would not say the software RAID is responsible for the problem you are having, I just think you may be a bit light on RAM. How much swap space do you have? It should be about twice your RAM.

Sorry, when you said drag and drop files I automatically assumed......my bad. :(

You also may be able to find some info by checking your logs in /var/log. You never know, there might be a clue there.

-Tim

---

### Post by Twizzle on 2008-08-24
I have 710MB RAM and 1 GB Swap available.

I left it copying files overnight and it has managed it. I did shut down Zoneminder while it was doing so as I remembered that I had been playing around with shmall and shmmax settings (as recommended in their wiki to get cameras working).

I also left top running in an ssh termainal. Although the server is doing nothing now, it still says there is only 7872k of memory free and mysqld is using 2.6%. Other than that there is the odd 0.2% but it doesn't all add up to the 90% or so used?!?

Is is possible to increase my swap file without reinstalling?

---

### Post by chorca on 2009-03-09
Well this is a bit late in coming, but I'm having the same issue with a just-recently-installed system. Exact same problems. After large transfers over SMB, the machine hardlocks. No local video, no network, no disk writes, nothing. Complete lock up.

The machine i'm running has 2GB of memory, and I experience the same issue with top or other commands showing almost all memory used. I read about this, and it seems that linux likes to use any free memory for disk caching, i.e. it's not "used" as in it isn't available to other apps, but if there's idle ram that's not *in use* then it uses it for disk caching to speed things up. Mine goes up to almost 2GB used within a few reads/writes to the array, and stays there forever, until there are large reads/writes.

---

