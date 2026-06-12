---
title: "Memory Leak?"
date: 2009-12-17
forum: Server Platforms
---

### Post by bacterozoid on 2009-12-17
I've been running an Ubuntu web server for several months now and I've noticed that things start to get bogged down after it's been up for a while.

When I SSH in and look at **top**, I'm seeing the normal processes with little to no memory/cpu usage (the server doesn't do much)

When I first log in, I get this info:

System load:  0.0
Swap usage:  0%
Users logged in: 1
Usage of /:   6.3% of 70.10GB
Temperature: 43 C
Memory usage: 13%
Processes:   83

That all seems fine. However, I can tell it's super slow. I'm currently downloading an MP3 over SFTP and I'm getting super slow transfer speeds and slow responses over SSH.

I installed phpsysinfo a while back so I could keep track of things - it's telling me I'm at 97% memory usage (uptime is 31 days). 79% of that is labeled "cached" and I'm not sure what that means.

Any ideas? Once I reboot the server everything runs better.

[COLOR="Orange"]Edit: I understand now that Ubuntu is just dropping crap into the cache when I use it, which makes sense. My trouble is that it doesn't seem to be releasing things from the cache when I need memory for other things.[/COLOR]

---

### Post by Vegan on 2009-12-17
I have not noticed any problems on my server. Check your software stack for a buggy program.

---

