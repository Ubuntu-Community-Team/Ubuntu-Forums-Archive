---
title: "In need of a file server cache"
date: 2009-08-17
forum: Server Platforms
---

### Post by Alexander Lindskog on 2009-08-17
Hi all, 

I have tried googling this without much success. 

Here is a summarized description of what I'm trying to do.


Equipment;

Ubuntu 9.04 as a file server on a small/medium local network.

It has a small but fast drive (60 GiB) and a large slower drive (1 TB)


Workload:

Data is usually blocks of 100 MB and roughly 10-20 GB of total available data is requested on an average day.

Requests are however highly correlated so that several users request the same data during a day.


Goal:

Using the faster drive to cache requested files reducing the reads from the large slow drive. Preferably transparent to the file server (some sort of virtual fs / FUSE). 

Optimally a mounted folder which seems to contain all files on the large disk and which on accessing a file simultaneously copies read data to internal cache.


So, does anyone happen to know of some program or technique to achieve this "dream" of mine?

Regards,

Alex

---

### Post by ian dobson on 2009-08-17
Hi,

Maybe you could do something with the Mini_fo virtual filesystem.

Or maybe look in google for primary/secondary/tertiary file systems or "translucent filesystem" as used in sans.

I don't really think that what you want to do will make any difference even if you do get it working. Maybe try timing reading files from the "fast" and the "slow" drive over the network. I don't think you'll see much difference. The best thing to do is add as much ram as possible to server.

Regards
Ian Dobson

---

### Post by Alexander Lindskog on 2009-08-18
Thanks for taking the time to reply.

You are probably right about the speeds. We were however discussing moving the tertiary storage off-site along with our backup if this first project was successful. In this case caching would be a greater issue. 

I did check out mini_fo and it is interesting but not really what I was looking for. I also found Sluggard which was more in line with what I needed but not quite.

Would it perhaps be possible to set up Squid or some similar software to cache large files?

Regards

Alex

---

