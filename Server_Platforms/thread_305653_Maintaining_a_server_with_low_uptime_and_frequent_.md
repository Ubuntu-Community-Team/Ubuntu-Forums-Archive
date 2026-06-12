---
title: "Maintaining a server with low uptime and frequent restarts"
date: 2006-11-23
forum: Server Platforms
---

### Post by Hagbard on 2006-11-23
I have a LAMP server setup on a Xubuntu 6.10 base that I am using to learn web development and systems administration. I only keep it up for a few hours a day, and while I'm using it I frequently restart it after configuration edits. I know that servers and server software are designed for a 'constant uptime' environment.

My question is, what additional steps do I need to take to maintain a system that operates under these conditions? Do I need to examine my CRON file and execute most of its tasks manually, since my system is off most of the time? What about rotating the log files from various applications? If it makes any difference, the entire setup is also completely virtualized.

---

### Post by tturrisi on 2006-11-23
Not an answer to your question, but why the restarts?  Just stop & start the servers after making changes.

---

### Post by Hagbard on 2006-11-24
The frequent restarts have a few different causes, actually. Since it's a virtual machine on my desktop computer, I don't want to keep a 512 MB+ application constantly running in the background when I'm not working with it, since it drains a lot of processor cycles even when the VM is fairly idle. Also, since this is a test/experiment server, I will often make a backup clone of the whole VM before major changes, which requires halting it. Another consequence of the text/experiment process is that I often try to 'test to the breaking point' and get my system into some eccentric states. Throw in some tinkering with the boot process itself, and I end up restarting at least once every session working with the machine, on top of the initial startup.

---

### Post by MJN on 2006-11-24
Restarts are not a problem, however as you say this does have the potential to miss out on scheduled cron tasks. Servers are not particularly different from desktops in terms of sceduled cron requirements - after all the majority of tasks merely involve rotating log files, updating search databases etc - i.e. they're not 'server specific' tasks.
 
Thankfully, the issue has already been considered and the *anacron* project was born. Install it (nothing more to do), if it's not already (I think it's in by default), and this will ensure that any tasks scheduled to run when the machine was off will get executed appropriately.
 
[http://anacron.sourceforge.net/](http://anacron.sourceforge.net/)
 
Mathew

---

### Post by Hagbard on 2006-11-24
Thanks for the info. I guess I just need to figure out exactly what I want from my Anacron file and put it all in there. Good to know that I'm not spawning a ton of orphaned temp cache files or something like that.

---

### Post by MJN on 2006-11-25
Your 'server' is barely different than someone using Linux as a 'client' (and hence likely turning it on/off once/twice/etc a day) - and both will equally benefit from Anacron to ensure regular tasks are completed.

I'm pretty sure Anacron is installed by default - I recollect that my Breezy install had it (I removed it because my machine is on 24/7 hence it was unnecessary to keep it).

Mathew

---

