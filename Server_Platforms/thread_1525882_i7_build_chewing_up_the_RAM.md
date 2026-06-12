---
title: "i7 build chewing up the RAM"
date: 2010-07-07
forum: Server Platforms
---

### Post by R.Bucky on 2010-07-07
I just built a new Intel i7 box with a DP55KG motherboard and soft RAID1. I installed AMP, ssh, and a few other apps. It is running 64-bit Ubuntu Server 10.04LTS. 

The box is really chewing on the RAM. Any thoughts why this is so, or is it the 64-bit talking?

[IMG]http://blog.markimoore.com/uploads/i7.png[/IMG]

---

### Post by infamous-online on 2010-07-09
1 gig of ram usage isn't bad considering you have 8 gigs total. I have pretty much the same setup and I'm using about the same amount of memory that you're using. Now my question is are you running any other programs like firefox and such or is that amount of ram being is when the system is first booted?

---

### Post by The Real Dave on 2010-07-09
Try using ```
sudo htop
```

and using F6 to sort the list by memory usage. That should give you an idea of what's using all that up :)

---

