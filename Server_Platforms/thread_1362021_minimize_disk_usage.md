---
title: "minimize disk usage"
date: 2009-12-22
forum: Server Platforms
---

### Post by p2ranger on 2009-12-22
I have Ubuntu Sever 9.04 installed on a thumb drive. The computer acts as a file server. I have two SATA drives raided for the files I use most of the time. I know that solid state has only so much read/write life. Is there things I can do to minimize the amount of reading and writing that goes on with the thumb drive?

I don't know, I'm guessing there isn't much that happens on the thumb drive except for when it gets started, as it just stays on most of the time. I don't have a lot of experience with how linux works. I know my previous windows computers made the HD light flicker even when it was sitting idle. I'm hoping this is not the case with linux and that most of the operations just happen in the 2 Gig of memory.

Also thinking of using this for a small personal web server. Would it be wise to move the DocumentRoot directory off of the thumbdirve so it doesn't get more read/write access?

Thanks for any suggestions.

Jason

---

### Post by CharlesA on 2009-12-22
Probably be a good idea to store the files on the RAID array.

---

### Post by Vegan on 2009-12-22
The SSD is best for files that do not change often. The read speed can be much faster. The main advantage is with database servers such as busy web sites.

This site would benefit a lot with tons of RAM and a large RAID of SSD disks.

---

