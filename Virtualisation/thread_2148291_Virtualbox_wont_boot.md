---
title: "Virtualbox wont boot"
date: 2013-05-24
forum: Virtualisation
---

### Post by Timmy0829 on 2013-05-24
Hi guys,


The problem is I installed Virtualbox in ubuntu 12.04 And i want to run win7. When I click on start this is coming up:

No bootable medium found! System halted.

I told to the program where to find the win7 iso image.
But its just not doing it.

And also I opened the win iso file and I can just see 1 txt inside what says:

This disc contains a "UDF" file system and requires an operating system
that supports the ISO-13346 "UDF" file system specification.

So I opened the synaptic package manager and installed the udf packages. But still a can`t see anything just the txt in the iso. 

Is this the reason why the virtualbox not booting the windows?

Please help me, i was looking for the solution the whole day...

Thanks

---

### Post by Cheesemill on 2013-05-24
Where did you get your iso file from?

---

### Post by Timmy0829 on 2013-05-24
From a torrentsite. With a lot of positive feedback. And I already downloaded 3 version. So I dont think the problem is the iso.

---

### Post by Timmy0829 on 2013-05-24
I installed AcetoneISO, and with this I can see the folders inside my Windows.iso.

But in virtualbox its not booting still.

Any ideas?

---

### Post by Timmy0829 on 2013-05-24
Well, the problem was i was in secondary master, not secondary slave. Its booting now in slave mode...

---

