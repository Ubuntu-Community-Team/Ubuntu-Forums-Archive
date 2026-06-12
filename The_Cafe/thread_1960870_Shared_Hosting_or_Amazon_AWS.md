---
title: "Shared Hosting or Amazon AWS"
date: 2012-04-18
forum: The Cafe
---

### Post by minigilani on 2012-04-18
Hey

I need an opinion on this: i have about four websites, all friends and family and mostly brochureware. If you had the option, would you go for Amazon's AWS or a shared host?

Point being, i either bunch them all together on one dreamhost.com shared hosting account, or design an elaborate web hosting solution. I have no prior experience or knowledge apart from:
```
sudo tasksel install lamp-server
```

I could learn it all, (and if someone could point me to a good guide, i'd be immensely grateful) but what would you do if you were me?

---

### Post by stmiller on 2012-04-19
Shared hosting is cheaper, but they cap the upload/download speed to and from the accounts on purpose. So it can be slow uploading for lots of content.

Probably best to start out with shared hosting then you can later move to something like slicehost or linode.

---

### Post by sandyd on 2012-04-20
> **minigilani said:**
> Hey

I need an opinion on this: i have about four websites, all friends and family and mostly brochureware. If you had the option, would you go for Amazon's AWS or a shared host?

Point being, i either bunch them all together on one dreamhost.com shared hosting account, or design an elaborate web hosting solution. I have no prior experience or knowledge apart from:
```
sudo tasksel install lamp-server
```I could learn it all, (and if someone could point me to a good guide, i'd be immensely grateful) but what would you do if you were me?
Amazon AWS.
Though their EBSes (Elastic Block Volumes) have real crappy I/O latency, most have direct peering with ISPs. This means:

With Amazon AWS:
Amazon AWS Instance -> Amazon AWS Network -> ISP Network

With a standard host/server/otherwise:
Amazon AWS Instance -> Amazon AWS Network -> Tier 1/2/3 Providers -> A few more Tier 1/2/3 Providers -> ISP Network.

Other than that benifit (other than if you are hosting resource-intensive sites, or require resource scaling), theirs not much reason to spend extra for AWS. Because of the I/O latency, sites can actually run slower (Ive tried it before, it was quite nasty) if you don't select a higher plan that provides better I/O. I don't know about that, because I stopped considering it as an option after I noticed the horrible I/O.

But then again, if you are careful, you technically *could* fit in the free usage tier. There is a chance that you can go over the 2 million IOs EBS limit though, and incur a few bucks worth of charges.

In conclusion, I don't really think its worth it to host on Amazon AWS.

And as I say each time, don't host on unlimited webhosts. They attract a lot of abusers, and if you are subscribed to a box with one, there can be some serious problems.

Then again, its a long time since ive used a shared host. Switched to dedicated after experiencing the horrible I/O from cloud solutions. Now have 5 GiB/s of network connectivity.

---

