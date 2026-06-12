---
title: "Is verify and repair for a RAID 1 available and/or necessary?"
date: 2012-04-30
forum: Server Platforms
---

### Post by frotzed on 2012-04-30
So, with most other RAID 1's I've set up on Windows servers and Windows desktops I've always made a habit of running a verify and repair on the RAID on a regular basis.

I'm running Ubuntu Server 10.04 with a RAID 1 and I'm wondering if:

1) Is it possible to run a verify and repair on the RAID?

2) Is it necessary?

---

### Post by rubylaser on 2012-04-30
mdadm has a cron task in /etc/cron.d/mdadm that runs on the first Sunday of every month and runs a check action that does exactly what you're talking about.  I'd recommend you keep that in place, and it will run automatically.

---

### Post by frotzed on 2012-04-30
> **rubylaser said:**
> mdadm has a cron task in /etc/cron.d/mdadm that runs on the first Sunday of every month and runs a check action that does exactly what you're talking about.  I'd recommend you keep that in place, and it will run automatically.

So it's enabled and on that schedule by default then, on every install?  Excellent.  Thank you for your help.

---

### Post by rubylaser on 2012-04-30
Yes it is.  You will want to make sure you have mdadm setup to email you and that you have email setup properly to send emails, if it detects any problems.

---

### Post by frotzed on 2012-04-30
I did set up the email function.  Thanks for the reminder :)

---

