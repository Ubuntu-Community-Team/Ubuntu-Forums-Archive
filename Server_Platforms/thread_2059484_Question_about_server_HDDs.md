---
title: "Question about server HDDs"
date: 2012-09-18
forum: Server Platforms
---

### Post by darkod on 2012-09-18
While this is not an ubuntu question, I have decided to ask for an opinion here since I'm active here.

At work I have to add new disks to a backup server (the machine doing backups). Unfortunately, I will be on a really, really tight budget and compared with the capacity I need I will not be able to go with 10k or 15k disks.

So, if we are talking about 7k2 SATA disks, how much sense does it make to go for the enterprise models compared with the "standard" ones?

I mean, I see the difference between 10k or 15k disk and 7k2, but when comparing the 7k2 enterprise models specs, the data is almost identical to standard 7k2 models. Access time, read/write time, sustained transfer rate, MTBF...

Since the enterprise models of 2TB cost double where I am, is it worth it? The only bigger difference I see is the 5 year warranty as opposed to 2 year but i wonder if it's worth it.

With similar MTBF can I really expect standard disks to fail sooner? And enterprise disks to perform much better?

If money wasn't an issue I know what I would get. But it is a big issue right now.

Thanks in advance for any feedback.

---

### Post by Grenage on 2012-09-18
Improved MTBF, so better predicted longevity; in my experience it's worth it in the right situation.  If money is tight, but your redundancy planning (outside the physical server) is good, I don't think they are worth it.  Enterprise drives can fail after a week, you can't know.

Neither the entry nor enterprise drives have failed any more than the other, but we are a relatively small subset of data.  I have never specced entry drives for a server that will be in high demand (read: 24/7 thrashed SQL server), so I'm comparing them in general low-medium use.

Bottom line: Entry drives will probably suffice - they aren't going to fail in a week.  They've got damn good build quality.

---

### Post by darkod on 2012-09-18
On top of that, this is a backup server that will do overnight backups (no 24/7 load on the disks), and most of the times differential backups.

I noticed something interesting too. For Seagate for example, the enterprise Constellation.ES2 2TB disk is rated at consumption 10.7W average, while the Barracuda 7200.14 2TB is 8W.

---

### Post by kgatan on 2012-09-18
Id suggest to use either WD black series or the budget alternative WD AV-GP series. 
AV-GP is about the same price as green drives.

Accordring to WD both are designed to run 24/7.

Though id guess that any drives are good enough if you give some considiration to what filesystem they will be using as Its all about how fast you can replace a faulted drive. 

In my humble opinion the only rock solid backup filesystem is ZFS on a solaris or bsd system.

---

### Post by darkod on 2012-09-18
> **kgatan said:**
> Id suggest to use either WD black series or the budget alternative WD AV-GP series. 
AV-GP is about the same price as green drives.

Accordring to WD both are designed to run 24/7.

Though id guess that any drives are good enough if you give some considiration to what filesystem they will be using as Its all about how fast you can replace a faulted drive. 

In my humble opinion the only rock solid backup filesystem is ZFS on a solaris or bsd system.

Unfortunately I'm in a windows only network and plus this server will be running the backup software too, so it has to have windows on it.

Isn't the AV-GP more towards video? Not sure why the data type would matter, but I remember seeing they are designed for video streaming in mind. And yes, they are designed for 24/7 but not cheap either. I guess with their price I would rather go with the WD RE4 or Seagate Constellation.ES2.

---

### Post by LedFoot74 on 2012-11-24
If you are going for non-enterprise disks then just make sure you choose a different baran/make for each one. This way you don't get MTBF (mean time before failure) issues from a batch problem.

A really good idea if you are using them for say RAID5 as you wont find all will fail around the same time....which would be bad...

---

