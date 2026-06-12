---
title: "Seeking recommendations for small server hardware..."
date: 2009-04-14
forum: Server Platforms
---

### Post by georgikeith on 2009-04-14
I wonder if anyone out there has some experience with Ubuntu on servers (not just desktops).

I'm looking to replace a 4-year old Dell Poweredge server that I currently use as a colocated business/hobby/email/webserver.  It's currently running SuSe, but I'm sick of dealing with RPMs, and would like to set up something running ubuntu, since that's what I use everywhere else.

Ideally, I'd like something that's incredibly reliable, and requires as little energy to maintain as possible.  I like to be able to keep it updated, but--since it will be handling all of my email and web presence--I need a system that doesn't suffer from flaky hardware.  (If it's going to be down, I want that to be MY fault).  Since disks seem to be the most common failure point, I expect I'll need a RAID array... Which brings me to my question: 

What hardware vendors do people who run Ubuntu on a RAID-able server recommend?

System76 looks convenient (though not the cheapest), but I know nothing of their hardware's reliability or their customer service.  I know IBM has a great reputation for hardware, but I understand they're fairly pricey.  My Dell system has been very reliable, but I'm nervous about being able to get ubuntu on their RAID systems (a recent attempt to install 8.10 on my Poweredge didn't recognize any hard-drives).  Then there's the HP Proliant machines that CDW sells, but I haven't heard anything about them.  I'm hoping to find something in the $1000-1500 range, but I'll stretch that if somebody gives me a good reason to...

If anybody out there can offer any experience (positive or negative), I'm all ears.

Thanks in advance...
--Georgi

---

### Post by spynappels on 2009-04-15
Hi,

  I use HP ProLiant ML115 servers, also available as ML110 with Intel hardware. Very basic but had no reliability problems. Spending a little more money will get you a higher spec ProLiant. We use HPs in preference to Dell PowerEdge now. We don't run a RAID on them, so cannot comment on that aspect.

---

### Post by ikonia on 2009-04-15
all comes down to budget and requirments.

What is the maximum you want to spend, and what are the features you MUST have.

Dell and HP mentioned in the earlier post all have very solid linux support but won't care to much about you as a 1 server guy, so don't expect discounts or great customer support.

smaller companies will work with you for support and a more personal touch, but shift lower kit volumes so will be a bit more expensive for bang per buck.

---

### Post by georgikeith on 2009-04-15
> **ikonia said:**
> all comes down to budget and requirments.

What is the maximum you want to spend, and what are the features you MUST have.

Dell and HP mentioned in the earlier post all have very solid linux support but won't care to much about you as a 1 server guy, so don't expect discounts or great customer support.

smaller companies will work with you for support and a more personal touch, but shift lower kit volumes so will be a bit more expensive for bang per buck.

"more expensive for bang per buck"...  buck * (bang/buck) == bang? :)

I really was hoping that people could tell me stuff like "Installing ubuntu on X's server was a pain in the neck" or "My employer has bought dozens of machines from YYY and we have had a statistically significant number of hardware failures"...

I'm starting to lean towards system76, if only to support the little ubuntu guy.  It sounds (from other conversations here) like this is not a terrible idea...  Any thoughts?

--Georgi

---

### Post by donboling on 2009-11-04
> **georgikeith said:**
> "more expensive for bang per buck"...  buck * (bang/buck) == bang? :)

I really was hoping that people could tell me stuff like "Installing ubuntu on X's server was a pain in the neck" or "My employer has bought dozens of machines from YYY and we have had a statistically significant number of hardware failures"...

I'm starting to lean towards system76, if only to support the little ubuntu guy.  It sounds (from other conversations here) like this is not a terrible idea...  Any thoughts?

--Georgi

HI Georgi,

I'm wondering if you ultimately went with System76 for your server? I am looking at them now for the same reasons. 

Thanks
Don

---

