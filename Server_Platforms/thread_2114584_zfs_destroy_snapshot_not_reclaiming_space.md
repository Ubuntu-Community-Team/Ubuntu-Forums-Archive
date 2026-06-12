---
title: "zfs destroy snapshot not reclaiming space?"
date: 2013-02-10
forum: Server Platforms
---

### Post by automaticgiant on 2013-02-10
I have finally divorced myself from zfs-auto-snapshot, which I have learned, by experience, requires careful forethought about the data sets you apply it to. I just finally destroyed my last two snapshots, but I still have 2.57T REFER on my fs. Right after destroy, I think the FREE on my pool was like 1T or 1.1T, and now it's 1.22T, so maybe its working it out, but it seems as if there is still space tied up in the snapshots even though they are destroyed. I started a scrub to see if it would hurry it along, though that may have been a mistake - I've been experiencing major packet loss to the internet and have been having trouble researching. Without doing a du on my fs to see how much I actually have in files, can I trust that the REFER 2.57T means that there is space in snapshots (what I previously understood it to mean)? I'm kindof confused, and my horrible internet isn't helping much.

---

