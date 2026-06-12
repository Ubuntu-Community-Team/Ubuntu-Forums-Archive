---
title: "OSI Layer of bit torrent"
date: 2011-02-23
forum: The Cafe
---

### Post by kevin11951 on 2011-02-23
I am teaching networking at a local high school, and a kid asked me what layer of the OSI model bit torrent is on.  

I didn't have an answer, any ideas?

---

### Post by MaxIBoy on 2011-02-23
Some googling turns up the Bittorrent net protocol spec:
[http://www.scribd.com/doc/528983/Bittorrent-Protocol-Specification-v10](http://www.scribd.com/doc/528983/Bittorrent-Protocol-Specification-v10)
Just from skimming, it looks like the tracker uses HTTP, and peer-to-peer communication uses TCP. Don't know if that helps.

---

### Post by uRock on 2011-02-23
> **kevin11951 said:**
> I am teaching networking at a local high school, and a kid asked me what layer of the OSI model bit torrent is on.  

I didn't have an answer, any ideas?
Application layer, because the application is setting up multiple sessions to handle the job.

---

### Post by doas777 on 2011-02-23
well, bittorrent is an application so it resides at layer 7.

the better question is what protocols does bittorrent use at each layer to perform it's functions. think of each layer as a task that needs be accomplished, and ask what tool are the application developers using to accomplish each task. 

the layers above 4 (Transport) are largely up to the operating system or the bt client itself, and will rely on localization like language (presentation) and multiuser session control (session). as I mentioned it relies on tcp/udp/ip (internetwork and transport) and what ever datalink/physical protocols are appropriate for their local network, and each network that the transportation passes through.

---

