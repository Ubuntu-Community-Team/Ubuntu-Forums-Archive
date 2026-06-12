---
title: "Ubuntu Server power management"
date: 2008-08-18
forum: Server Platforms
---

### Post by voteforpedro on 2008-08-18
I know the answer is "servers are supposed to remain on 24/7" but I don't care!!

I've built a headless server running Ubuntu Server (Hardy Heron). All works fine and I can configure it from my workplace when I'm bored, which is nice. :]

But I don't want it on 24/7. It is going to be used as a web server too but, as it is going to be my web design porfolio, I imagine it would only be accessed between 9-5 Monday Friday. It will also function as a firewall, file and print server.

So I what I want is to reduce the amount of power it consumes as much as possible. Ideally I would want it to completely shut down after a certain length of inactivity or, alternatively, shut down the hard disks.

If it shuts down I want it to be able to switch back on using Wake on LAN, when required.

Can anybody point me in the right direction?

---

### Post by Sam Lars on 2008-08-18
You might be able to get it to suspend/hibernate after inactivity, but I don't know if it would be able to automatically wake up from that.
For the hard drives, you can use
```
sudo hdparm -B 255 /dev/hda
```
The 255 is a number between 0 and 255.  255 turns hard disk power management off, zero is the max.  I can't remember what all the values in between do... but they're not exactly linear.  But use this setting with care.
If it's a firewall, wouldn't you want that on 24/7?

---

