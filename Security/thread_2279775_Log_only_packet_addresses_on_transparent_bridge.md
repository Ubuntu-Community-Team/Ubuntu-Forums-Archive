---
title: "Log only packet addresses on transparent bridge"
date: 2015-05-26
forum: Security
---

### Post by john405 on 2015-05-26
I have a Linux box with Ubuntu 12.04 running as a transparent bridge (built in network interface connected to modem, network card to the router).  I can see packets going through with iftop, tcpdump, or whatever else.  What I need to do is log what users on the local network have accessed what websites (I can do the reverse DNS myself, and all users are on static IPs).  Basically, it should listen for a packet from any address to any address, and for each packet it receives, stop listening for that specific address pair, but still log different pairs (for example, if a packet goes from 192.168.1.12 to 98.139.183.24, it should log that, but never repeat the same entry, but still record if 192.168.1.11 sends a packet to 98.139.183.24).  The computer is rather slow, particularly the disk, and it's only a 32GB drive, so I can't just log everything (this will have to run for months without deleting anything).  I don't want to filter anything, just see where it went.

---

### Post by bashiergui on 2015-05-26
> The computer is rather slow, particularly the disk, and it's only a 32GB drive, so I can't just log everything (this will have to run for months without deleting anything). I don't want to filter anything, just see where it went Even if there were only a few users surfing the internet and if you only captured IPs, you would fill up that drive fast. I can't conceive a way to overcome the space limitation.

---

### Post by john405 on 2015-05-28
I fail to see how even a few people (usually 3) could fill up 30GB with just IP addresses.  That would require about 4 BILLION different website-user combinations-or each person accessing a new website every second for 50 years, day and night, with no repeats.  This is humans accessing a few new sites a day at maximum, for a few months.  So no, space is not the limitation.

---

### Post by bashiergui on 2015-05-29
Assuming you don't have access to router logs...

I don't know of anything ready made that will do that. You'd probably have to let tcpdump run eternally and write logs to smallish files. Then have a script read the log file and extract the unique IPs, then delete the log file when done. 

Let tcpdump run for a couple hours during a busy time and then do some awk uniq magic on the output to get an idea of how much data you should expect.

---

### Post by john405 on 2015-06-01
Yeah, I was hoping there'd be some premade option for that.  I was just going to use java, and have that parse the output stream directly, though.

---

