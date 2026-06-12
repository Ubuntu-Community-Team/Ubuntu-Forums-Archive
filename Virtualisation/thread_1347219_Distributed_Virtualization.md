---
title: "Distributed Virtualization?"
date: 2009-12-05
forum: Virtualisation
---

### Post by yesindeed on 2009-12-05
So I'm not sure if this idea is even physically possible, but if it is and someone knows how to do it, or can point me in at least the right direction, I would be very appreciative!

So me and a couple of my buddies all have home server boxes running Ubuntu out of our houses. For the most part, they are all for personal-type things, and are online a majority of the time, but occasionally will go off, either due to power outages, while moving between apartments, manually turning off while going on a long trip, etc. The question I have is: Is it possible to virtualize a server over all of these machines, so that if one machine is down, it will stay up, as long as at least one of our host servers is up. The purpose of this being a reliable, always-on server that we can all share. The problem is that we are physically distributed all over the country. I know (at least I think I do), that it would be possible to form a cluster like this and virtualize a linux server over a high-speed LAN, but is it possible to do it over the Internet?

---

### Post by bingoUV on 2009-12-06
Like you said, it is possible on a high speed LAN. The same can be done on internet too, only at a cost of performance.

Now, exactly what kind of performance are we talking about? To see this, let us discuss how this "distributed" virtualization works. To the best of my knowledge, (based on working with Xen, about a year ago) such systems work on a common distributed filesystem (NFS etc.). So 2 VMs - VM1 and VM2, on 2 different servers - Server1 and Server2, can fail-over if they are configured to do so; and also if they are on the same distributed storage. When Server1 goes down, taking down VM1 with it, Server2 detects it through time-outs and then it boots up VM2.  This VM2 behaves identically as VM1 because they share the same storage. That is why fail-over takes some time i.e. the time required to boot VM2 from its storage.

In your case, this distributed storage will be on the internet. Let us say, you subscribe to Amazon's S3 as well as EC2 service for storage. Make one EC2 server as NFS server and all your friends mount this storage as the image of the VMs you are running. Check the performance of VMs thus configured. If this performance is acceptable, you have your "distributed virtualization". If not, wait for lower latency and higher bandwidth internet :).

So, long story short, your question is not about distributed virtualization. It is about distributed filesystems. If, other than NFS, some other distributed file system can give better performance over slower links, you can use that instead.

---

### Post by julianb on 2009-12-09
>  The purpose of this being a reliable, always-on server that we can all share. The problem is that we are physically distributed all over the country. I know (at least I think I do), that it would be possible to form a cluster like this and virtualize a linux server over a high-speed LAN, but is it possible to do it over the Internet?

Would it serve your needs to instead take a "mirror and synchronize" style approach - all files to be kept on 2 or 3 machines, and all necessary apps also running on each mirror?

---

