---
title: "Server crash logs?"
date: 2009-05-16
forum: Server Platforms
---

### Post by batman01 on 2009-05-16
Hi Chaps,

My ubuntu server has been crashing of late. It chucks out a whole load of what looks like debug info when it does it, pages of the stuff. When I reboot it however I can't seem to find anything similar in any of the logs. 

How do I capture the terminal output when the crash occurs so I can start trying to work out whats causing  it to keel over?

i.e. can I dump it to disk, or fire it off to a syslog server or something?

Thanks

Pete

---

### Post by batman01 on 2009-05-18
Wow, I didn't realise it was such a difficut question. Its the first time I've stumped you guys completely.

---

### Post by gombadi on 2009-05-18
> 
How do I capture the terminal output when the crash occurs so I can start trying to work out whats causing it to keel over?

i.e. can I dump it to disk, or fire it off to a syslog server or something?


Sounds like your server did a kernel panic. Depending on the type of crash it may or may not log details to the log files. In your case I guess not. If it is that bad then system will be dead. i.e it will not be able to write to filesystems or remote hosts via the network.

The best idea is to have a pencil and paper handy or use a digital camera to capture the details on the screen, reboot and then search the net for similar crash reports.

---

