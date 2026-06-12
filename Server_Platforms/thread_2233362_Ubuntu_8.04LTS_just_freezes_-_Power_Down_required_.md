---
title: "Ubuntu 8.04LTS just freezes - Power Down required to get it back"
date: 2014-07-08
forum: Server Platforms
---

### Post by chrislynch8 on 2014-07-08
This has happened twice in the past two weeks on one of my Ubuntu 8.04 File Servers. The Server is a Dell PowerEdge 1900 and it has no hardware issues, I've run Dell Diagnostics and it found no issues.

What is happening is that the users come on and there is not server access. The File Server is running, but there is nothing on the screen, the Keyboard does not work either. Pressing CAPS LCK etc. lights do not turn on. The only way to get it back is to hold in the power button on the File Server and have it turn off. Then when it powers up it works away. The last time this happened it froze at 19:38 on the 4th of July and it stayed frozen until the following Monday morning. I checked the log files on the File Server and they just stopped at this time, with no indication of errors etc.

I would like to get to the bottom of this before we upgrade to 14.04 as this server is due an upgrade.

Any suggestions on where to even start looking?

Rgds
Chris

---

### Post by TheFu on 2014-07-08
8.04 Server hasn't been supported in over a year.  Most people migrated to 12.04, if they skipped 10.04.  We upgraded our last 8.04 server here in 2012.  Be certain that management knows this stuff, though sometimes business needs overrule upgrades. We've all been there. Heck, I worked on 30 yr old software at my first real job.

So .... what do the log files on both the client and server show? What was the last message? Anything in dmesg?  Might need to boot off alternate media to see the old messages.

What do you mean by "file server" - is that NFS, CIFS, WebDAV ... something else?
Can you ssh in?  You imply the system is locked up, but just because the keyboard doesn't work, doesn't mean that ssh doesn't.  Please clarify.

Also - is there a GUI loaded or not?  GUIs can lock up _just because_ over time.

Without any more facts and data, we are just guessing at the problem.  Could be pixie dust ... .or a momentary short caused by metal fibers creating a short or any other issue that doesn't log. No way to tell from here. Sorry.

BTW, I hope this is a hardware upgrade.  Newer servers are much less power hungry, produce less heat, less noise, and come with larger disks that are under warranty.  Plus a small server can easily be virtualized to run 5-20 VMs.  Some older hardware will not boot Ubuntu 14.04 ... I know that was an issue for some HP models. Don't know about Dell, sorry.

---

### Post by Gyokuro on 2014-07-08
Hi

There should be something logged - either in syslog or screen and I would hook up a serial console or net terminal for further monitoring purpose. In case it freezes again it is the right time to clean it from dust, check all cables, RAM and another thing I would test is the PSU with a voltage tester. Could be a problem with an overheating CPU, bad RAM, dying disk or motherboard problem but without any logs we can only speculate. I think you know which services are running so maybe you can find out what was the last dying one. 

- HTH

---

