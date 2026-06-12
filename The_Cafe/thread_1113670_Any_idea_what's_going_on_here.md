---
title: "Any idea what's going on here?"
date: 2009-04-01
forum: The Cafe
---

### Post by Mateo on 2009-04-01
I work for a small company of about 30 employees.  Most of our file storage is done on an older windows server (I think probably windows 2000 era).  We have a problem where the servers often go slow or "crash" (as coworkers often say) from time to time.  Probably a couple of times a day.  You will be working with an open file and your application will go slow for a minute or so.  Sometimes you will lose changes that you have made since the last save, sometimes not.

I don't work for IT so I don't care about finding a "solution", I'm just curious as to what is likely happening here.  Purely a curiosity question.  And if we can refrain from "it's windows" answers, that would be great.  With that being said, if you know what the reason is for this problem, how would a switch to linux remedy it (keep in mind that i have no say in this matter and am not going to suggest it, i'm simply curious to learn).

One thing to note is that I know we are very close to being full as far as hard drive space is concerned.

---

### Post by cheapie on 2009-04-01
Sounds like there isn't enough space for the swap file.

---

### Post by swoll1980 on 2009-04-01
Could be a bunch of different things, really to many to list.

---

### Post by lykwydchykyn on 2009-04-01
Could be the AV scanning; not even the server necessarily, but on workstations. Could be someone transferring large files, a backup job runninng, high network traffic volumes, scheduled task running.  Who knows?

---

### Post by Mateo on 2009-04-01
> **lykwydchykyn said:**
> Could be the AV scanning; not even the server necessarily, but on workstations. Could be someone transferring large files, a backup job runninng, high network traffic volumes, scheduled task running.  Who knows?

I know it's not the AV, because that was believed to be the problem in the past and it was fixed (or turned off, i'm not sure which).  I think AV is done in the firewall now.

Of all of the ideas you listed, would they cause you to actually lose connection to the server from your workstation?  Because I'm pretty sure we are losing connection temporarily, long enough to lose changes made to files.

---

### Post by swoll1980 on 2009-04-01
> **Mateo said:**
> I know it's not the AV, because that was believed to be the problem in the past and it was fixed (or turned off, i'm not sure which).  I think AV is done in the firewall now.

Of all of the ideas you listed, would they cause you to actually lose connection to the server from your workstation?  Because I'm pretty sure we are losing connection temporarily, long enough to lose changes made to files.

High traffic could absolutely cause slowdown, and a disconnect.

---

### Post by Mateo on 2009-04-01
Oh, ok.  Do you know why that is, on a more technical level?  Does it only allow a certain number of file connections and if the number is exceed it disconnects everyone temporarily or something like that?

---

### Post by swoll1980 on 2009-04-01
> **Mateo said:**
> Oh, ok.  Do you know why that is, on a more technical level?  Does it only allow a certain number of file connections and if the number is exceed it disconnects everyone temporarily or something like that?

Every connection to the server uses resources. When the server runs out of resources it will slowdown, and drop connections.

---

### Post by 3rdalbum on 2009-04-01
At the university I used to go to, all the video editing workstations were set to use the network share as scratch space, rather than the local hard disks. If too many people tried rendering out their projects simultaneously, the network would get flaky and sometimes even go down; this always used to bring down some of the Macintosh clients as well.

If you are running any programs on your computers that require scratch space (basically, temporary space), check that they are set to use the local hard disk rather than a network share.

---

### Post by kernelhaxor on 2009-04-01
There's a very high chance that its the disk space.
What could be happening is that it whenever its absolutely out of disk space, it usually halts most of the processes and cleans up space wherever it can .. and then once it has enough space everything runs normal again .. slowly that space again keeps getting used by the OS and it again hits the point where it absolutely has no disk space .. and repeat

One of the guys that manages the servers at my company told me the above .. the OS used to pause the virtual machines until it cleaned up a little space and it did this periodically

---

### Post by lykwydchykyn on 2009-04-01
Most network services have something called a timeout, which means I send a packet to the server, and if I don't get the expected response in a certain period of time, I consider myself disconnected and give up.  Timeout is different for various services, and in some its tweakable.  It's possible the network traffic is just so high, or the server so overburdened, that connections are timing out and dropping.

Really, all this is speculation.  I'd assume your IT folks know what's going on.

---

### Post by Mateo on 2009-04-01
> **lykwydchykyn said:**
> Most network services have something called a timeout, which means I send a packet to the server, and if I don't get the expected response in a certain period of time, I consider myself disconnected and give up.  Timeout is different for various services, and in some its tweakable.  It's possible the network traffic is just so high, or the server so overburdened, that connections are timing out and dropping.

Really, all this is speculation.  I'd assume your IT folks know what's going on.

I don't think they do, since it's been happening since the summer and the general feel is that we just have to live with it, save stuff to our local drives while working.

thanks every one.  so it sounds like this isn't a windows problem so much, and that it would happen even if we used a linux server for file storage?

---

### Post by Dr. C on 2009-04-01
My guess is that it is a Windows NT4 server possibly 2000 or NT3.xx that is desperately short of disk space. It could be a very small partition for C:\ and there may even be lots of unused space in other partitions.

The fix may be as simple as booting an Ubuntu live CD on the server, resizing the partitions, and giving Windows (whatever version) a chance to breathe. Have fixed a Windows server by resizing partitions with an Ubuntu live CD and solving the too small C:\ partition problem. 

It is not the first time I have seen a Windows admin create a far too small partition for C:\.

---

### Post by Sinkingships7 on 2009-04-01
> **Mateo said:**
> I work for a small company of about 30 employees.  Most of our file storage is done on an older windows server (I think probably windows 2000 era).  We have a problem where the servers often go slow or "crash" (as coworkers often say) from time to time.  Probably a couple of times a day.  You will be working with an open file and your application will go slow for a minute or so.  Sometimes you will lose changes that you have made since the last save, sometimes not.

I don't work for IT so I don't care about finding a "solution", I'm just curious as to what is likely happening here.  Purely a curiosity question.  And if we can refrain from "it's windows" answers, that would be great.  With that being said, if you know what the reason is for this problem, how would a switch to linux remedy it (keep in mind that i have no say in this matter and am not going to suggest it, i'm simply curious to learn).

One thing to note is that I know we are very close to being full as far as hard drive space is concerned.

Well, obviously the culprit is Conficker.

.... seriously, though. It could be one of a million reasons. Probably poor maitenence. Could probably use a good registry cleaning and defrag. A full hard drive is certain to lead to bad fragmenting.

---

### Post by dmizer on 2009-04-02
My guess would be an equipment problem of some kind. Switch, router, cabling, network card, bad connection, bad crimp on the cat cable ...

But as others have noted, it's completly speculation unless we either have more specific information, or you have hands on troubleshooting access.

---

