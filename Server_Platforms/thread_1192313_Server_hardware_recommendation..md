---
title: "Server hardware recommendation."
date: 2009-06-19
forum: Server Platforms
---

### Post by izap on 2009-06-19
Hi guys,
    I am new in this community. We are actually looking to install our own in house web server. Where we planned to install 5 web applications and one of them will have video conversion features using ffmpeg. Consider 1000 user on video conversion application.

So i am really confused about the hardware i should go with. I want to ensemble my server.
So is there any body who can let me know the configurations of the hardware i should go with.

Motherboard,
CPU,
How much Ram?
etc.

Thanks in advance
-----------------
Regards,
Tarun

---

### Post by ian dobson on 2009-06-20
Hi,

"Consider 1000 user on video conversion application." this sentence is confusing me abit, are you talking about 1000 users converting videos at the same time? If so forget it or have a look at installing a very large number of servers.

Video conversion/transcoding can require alot of processing power so get the quickest CPU can afford, then look for a good quality server motherboard and then fill it with as much ram/hard disks (Video requires alot of disk space). 

My backend video server has almost 9Tb of disk space (40% full at the moment), a Quad Core CPU and 8Gb ram. The harddisks are setup in a RAID5 array so that if one HD dies I don't lose any data (Just swap it out and rebuild).

Don't forget if this server is important make sure anything that could break (Harddisks, Powersupply etc) should be setup so that you always have a spair online (2 powersupplies, N + 1 harddisks).

Regards
Ian Dobson

---

### Post by izap on 2009-06-24
@Ian Dobson,
   Thanks for your recommendation. It will help me.
-----------
Regards
Tarun

---

