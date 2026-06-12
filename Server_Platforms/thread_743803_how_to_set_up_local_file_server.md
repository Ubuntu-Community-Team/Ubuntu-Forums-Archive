---
title: "how to set up local file server?"
date: 2008-04-03
forum: Server Platforms
---

### Post by oysterpog on 2008-04-03
Gday!!

i'm fairly new to linux (experienced mac user) so advance apologies if these questions are ridiculously simple...

I live in a share house with many people downloading/streaming/watching movies from both the web and our own network. I want to setup a very basic file server which would allow for ALL our drives to be mounted on one machine and shared over our wired and wireless network. I also want this machine to be running some sort of WebUI capable torrent client (probably deluge, it seems the best for what i need) which would then handle the torrents for the entire house

I want to know what sort of hardware i would require (pc only, i have good routers). I dont want to spend lots of money, but i do need a machine which is capable of streaming up to 2 or 3 movies simultaneously over the network, and able to have AT LEAST 6 drives (SATA and IDE) mounted on it. However this computer will never be used for any other purpose.

what sort of processing speed, RAM, motherboard etc etc would i require for this sort of application?

many many thanks for any help :)

jonas

---

### Post by ryazkhan on 2008-04-03
If you are new to linux start with ubuntu desktop and configure samba in it for files sharing and also there are lot of feature you can do in ubuntu to stream your media in your network. I dont this on windows but not in Linux sorry not much detail. But was reading some articals to do that and I am sure you can do that. Ubuntu dont need and really really heavy server it will work with a standerd server or even PC. But as suggestion and looking at your structure you should look at duel core intel 2.4 or above. Xeon will be best option. Mem  1GB or higher etc.

---

### Post by hyper_ch on 2008-04-03
I'd go for a NSLU2, install debian on it and run rtorrent (there are also WUIs for it...)
[http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)

---

### Post by oysterpog on 2008-04-03
that nslu2 looks pretty cool, but only 2 usb ports? i really want to be able to share at least 5 drives. I think a pc would be the best option, hopefully i can find a motherboard which supports 5-6 drives without any hassle.

is debian difficult to set up for this sort of application (samba server and WUI enabled torrent client)? i have absolutely no experience with debian, but i've been told before that this would be the simplest way to set it up. whats the consensus?

---

### Post by kevdog on 2008-04-04
FreeNAS as an alternative to Ubuntu?

---

### Post by hyper_ch on 2008-04-04
Debian and Ubuntu are pretty much the same... main differences, Debian doesn't use sudo and packages on debian stable are typically older than on ubuntu but debian has a good record of reliability...

As for setting up a server on debian and ubuntu it's more or less identical.

---

### Post by hyper_ch on 2008-04-04
2x 1 TB drives are not enough?

---

### Post by oysterpog on 2008-04-06
yeah... i don't have 2 1tb drives, my housemates and I have about 3tb made up of about 5-6 assorted 250,500,750 gig IDE and SATA drives.

I think the best idea would be to build a very basic computer with a big f*** off motherboard so that i can mount 10+ drives off it. should be able to build it for less than $600 (AU). if anyone has any better ideas pls speak!

many thanks guys

---

