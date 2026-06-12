---
title: "Server from left overs, what could you use this for?"
date: 2007-05-22
forum: Server Platforms
---

### Post by Raval on 2007-05-22
I'm slowly but surely updating a Dell B110: 2.53Ghz Celeron D (series 325) @ 533Mhz & 256Mb Ram @ 333Mhz. 

So Far I've added 1GB Ram @ 400Mhz and plan  to add a 3.06Ghz P4 @ 800Mhs in 2 or 3 months when the price comes down a bit more.

Once the processor is upgraded I'll have the Celeron and and 256 memory and figured I could buy the rest of parts to make a small server. 

I take a lot of photos since January01 to now I've taken over 10Gb of photos with a 5 Mega pixel camera.

I figure I could use  this little server to store photos, backups, music, local web development (drupal), and with a wireless PCI card I could also network wirelessly, once networked I could connect to the internet through it and lastly by automated process, connect to my web host and create and download backups (don't know if this is possible). 

Of course I won't be doing all of this right away or simultaneously once everything is in place. AT some point i'll add a matched pair of 512Mb and turn HT on.

Now! finally that I've gotten all of that out the way so now one has to ask about specs.

I'm looking for a RUFF IDEA (just under ball park) of what the potential of a 2.53Ghz Celeron D @ 533Mhz with HT activated and 1024Mb of matched Ram @ 333Mhz (512Mb X 2) installed?

If you have a similar specs server let me know what you use it for and how much strain (if any) are you putting on the server.

umm one last question, is it wise to use this server, being that i have no experience, to store important data on it? OS will be 80Gb HD and maybe a 500Gb partitioned in half for data.

---

### Post by Wim Sturkenboom on 2007-05-23
So you're trying to upgrade a desktop and from the remaining parts you want to build a small server? If so, here are some things to think about.

At the end of the day, you have build a complete new PC (except for the processor). Wouldn't it have been easier to just buy a new PC as a desktop machine and promote the current machine to a server (maybe just adding an additional HD).
Personally I think you're using the wrong approach. It more than likely will cost you more money at the end of the day. Further, with the 'slow' approach, there might be a risk that you can not find a motherboard for your processor or that you can't get new memory (or at a high cost) etc.

I run a server for web development and file storage on a AMD K6-III@450MHz with 128MB ram and a 2GB and 80GB HD. If you don't have thousands of users connecting to the webserver at the same time nor hundreds of users that will open files on the server at the same time, you don't need a high spec'ed server. I can't complain about the performance of my server, but there are only two users in my environment.

You mention that your going to use 50% of a 500GB disk for data; what are you planning to do with the other half?

You can store important data on the server. In that case I would not use it to connect to the internet. Further you're still responsible for backups.

---

### Post by Chayak on 2007-05-23
You don't need much for a home server.  I'm running an old celeron 400mhz with 256mb of ram and some extra hard drives as a file server for my network.  The biggest bottleneck of the whole process is the network so it would be a waste to put faster HDs in it.  I've never had any issues with it and I have cron jobs set up to rsync to it for backup.  It does it's own backups with cron jobs as well.

---

