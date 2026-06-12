---
title: "Can only boot into recovery mode after hibernating :/"
date: 2015-01-19
forum: Ubuntu/Debian BASED
---

### Post by konrad6 on 2015-01-19
Hi all,

So I installed elementary Os 32-bit which is based on Ubuntu 12.04 onto my ageing laptop about a month ago and it's been running fairly well. Earlier today I ran "sudo apt-get install hibernate," as I want to keep all my tabs and stuff with the power off. So then I ran "sudo hibernate," and what that did was put me into a screen with some text on it (I forget what it said), which was frozen for ages so I decided to simply power off the entire system.

When I came home to turn it back on, Grub loads up fine, but when I try to boot it normally it just stays at the loading screen forever. It does boot into recovery mode which is where I am now but of course the graphics are distorted, and my CPU usage is a remarkable 50-80% with just Firefox and system monitor open (normally <10%).

I ran "sudo apt-get purge hibernate" in the recovery mode but that didn't make any difference upon trying to reboot. Does anybody know how to fix this issue so everything goes back to normal? I'd rather not have to do a wipe and reload...

Thanks

---

### Post by howefield on 2015-03-16
Thread moved to the "Ubuntu/Debian BASED" forum.

---

### Post by s.fox on 2015-03-16
Perhaps a little late but I think it'd be useful to see the list of processes running.

Can you post the output of running this in terminal:

```
ps aux | less
```

Thank you :)

---

