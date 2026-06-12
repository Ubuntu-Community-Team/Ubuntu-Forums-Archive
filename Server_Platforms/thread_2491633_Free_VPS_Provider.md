---
title: "Free VPS Provider?"
date: 2023-10-15
forum: Server Platforms
---

### Post by ohiodissident on 2023-10-15
Are there any decent VPS providers that are free or really cheap?  I tried AWS.  It was supposed to be a free year but after a month it said I ran out of hours (750 hours).  I don't need much CPU storage or bandwidth.  This is for personal use, not business.  I will just need a public IP (preferably v4).

---

### Post by QIII on 2023-10-16
RamNode might cost you < $20US/mo depending on the number of processors/memory/storage.  I run my websites and blog with them.

I'm sure there are other similar providers.

---

### Post by ohiodissident on 2023-10-19
> **QIII said:**
> RamNode might cost you < $20US/mo depending on the number of processors/memory/storage.  I run my websites and blog with them.

I'm sure there are other similar providers.

Even $20/month is a bit more than I want to spend.  But I realize nothing is really totally free.  I'll check them out.  Thanks for the suggestion!

---

### Post by TheFu on 2023-10-19
Digital Ocean and Vultr are less than $5/month for their smallest systems.  I've seen some less quality VPS for $4/month.  They oversold for the hardware, so if you are willing to wait 30 seconds for your VPS to be swapped in, that $1 savings could be worth it.  If you don't need the CPU all the time, it isn't hard to automate starting one and configuring it for your specific needs.  For example, I need a VPN every few weeks for a few hours, not all the time.  When I need one, I'll spin up a vultr minimal instance and have a script that installs the VPN and my keys.  In less than 2 minutes, it is ready to go.  Running it for 4 hrs costs less than $0.30.

---

