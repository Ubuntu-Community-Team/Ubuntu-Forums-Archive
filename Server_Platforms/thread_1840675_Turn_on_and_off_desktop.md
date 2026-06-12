---
title: "Turn on and off desktop"
date: 2011-09-08
forum: Server Platforms
---

### Post by RefinersFire on 2011-09-08
I have a Ubuntu 10.10 server install with LXDE as my desktop. I enjoy the ease of use for the desktop, however it is lowering my server's performance capabilities. I am launching a new site and need the capabilities. I am not fluent enough with Linux to go solely by commands.

My question is likely simple, and probably rhetorical. Can I somehow "turn on and off" the desktop on demand without rebooting?

---

### Post by arrrghhh on 2011-09-08
Well, on GNOME you just kill GDM.  ```
sudo service gdm stop
```What does LXDE use?  There must be some service like this that you can stop.

IMHO you should focus on working on the console, especially if you need the performance.  Not using a DE will help you learn the inner workings better, and you'll not only have a better understanding of how it works, but you'll be a leg up on troubleshooting issues down the road.

So while you're using the DE as a crutch now, I would highly encourage you to focus on ridding yourself of that crutch.  Ask questions, Google around... there's a ton of information out there.

---

