---
title: "Fans fail to run after Hibernate; system overheats"
date: 2008-04-15
forum: System76 Support
---

### Post by atorch on 2008-04-15
Hi,

This has happened several  times.  After Hibernate, my Pangolin's fans no longer work.  If I have the computer on my lap, I notice the heat (and Nvidia Settings -> Thermal Monitor tells me the Core Temperature is at 70, 80, 90 degrees), and I restart the computer.  But if the computer's on a desk, it can overheat until it shuts down...

Why does this happen?  

Can it be fixed by adding a line of code somewhere, to tell the fans to turn on again, that would be executed after "waking up" from hibernate?

Does anyone else experience this problem?

---

### Post by thomasaaron on 2008-04-15
That's a tad scary. Please don't use hibernate until this one is figured out.

What version of Ubuntu are you using? Hardy or Gutsy?
32-bit or 64-bit?
Which Pangolin Model to you have?

---

### Post by atorch on 2008-04-15
Yeah, I don't like it either.  The overheating until shutdown has only happened once (I wasn't typing, so I didn't feel it).  Does that do permanent damage?

I'm running Gutsy, 32-bit, and I bought my Pangolin on Jan 10, 2008 (hopefully that tells you the model -- my S76 driver tells me I have a serp3, but that must be a glitch.)

---

### Post by thomasaaron on 2008-04-15
OK. Please file a bug report here...
[https://launchpad.net/system76](https://launchpad.net/system76)

Please include as much info about your configuration as you can. nvidia, etc...

We will give it priority, try to reproduce the problem and come up with a fix.

Also, I seriously doubt it did any damage. If it did, you'd be noticing it. That's why they make
them shut down. However, repeated overheating can cause problems.

---

### Post by atorch on 2008-04-15
[https://bugs.launchpad.net/system76/+bug/217839](https://bugs.launchpad.net/system76/+bug/217839)

---

### Post by kutjara on 2008-04-16
> **atorch said:**
> Hi,

This has happened several  times.  After Hibernate, my Pangolin's fans no longer work.  If I have the computer on my lap, I notice the heat (and Nvidia Settings -> Thermal Monitor tells me the Core Temperature is at 70, 80, 90 degrees), and I restart the computer.  But if the computer's on a desk, it can overheat until it shuts down...

Why does this happen?  

Can it be fixed by adding a line of code somewhere, to tell the fans to turn on again, that would be executed after "waking up" from hibernate?

Does anyone else experience this problem?

I was reading another thread this evening about Acer laptops with the same problem. It seems the cause is that the Acer machines require the use of some Windows-only power management software to reenable the fans after suspend/hibernate. The recommended workaround was not to use suspend or hibernate on laptops displaying this behavior.

I don't know anything about the OEM of the Pangolin machines, but if they were made for use with Windows, is it possible they require an additional Windows power management app  that Ubuntu doesn't provide?

Just my poorly-informed two cents, in case it helps.

---

