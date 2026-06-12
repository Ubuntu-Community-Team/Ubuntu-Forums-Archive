---
title: "Ubuntu 10.10 in VMware Player - no network!"
date: 2010-10-22
forum: Virtualisation
---

### Post by dwilbank on 2010-10-22
Hi.
Rather than installing Ubuntu on a partition on my laptop, (the partitions were labeled very weird and I feared messing something up), I had the brilliant idea of installing it inside VMware so I could learn a bit.

It's a Win 7 64 bit laptop.
My settings are NAT (I also tried Bridged)
I tried getting Ubuntu to auto-update both while the laptop was wireless as well as when it was plugged into the ethernet cable.
No connection.
I saw somewhere on the forum where I should type ifconfig, so I did, and got a message which even to my unskilled eyes looks like bad news.

inet addr:127.0.0.1 Mask 255.0.0.0

UP LOOPBACK RUNNING
RX packets:368 errors

etc
etc

Seems like a lot of people are having the same problem, but all the solutions are over my head at the moment.

What's wrong please?

---

### Post by dcstar on 2010-11-05
> **dwilbank said:**
> Hi.
Rather than installing Ubuntu on a partition on my laptop, (the partitions were labeled very weird and I feared messing something up), I had the brilliant idea of installing it inside VMware so I could learn a bit.

It's a Win 7 64 bit laptop.
My settings are NAT (I also tried Bridged)
I tried getting Ubuntu to auto-update both while the laptop was wireless as well as when it was plugged into the ethernet cable.
No connection.
I saw somewhere on the forum where I should type ifconfig, so I did, and got a message which even to my unskilled eyes looks like bad news.

inet addr:127.0.0.1 Mask 255.0.0.0

UP LOOPBACK RUNNING
RX packets:368 errors

etc
etc

Seems like a lot of people are having the same problem, but all the solutions are over my head at the moment.

What's wrong please?

Install the VMware Tools - do a search for details of read the posts at the top of this forum.

---

### Post by dwilbank on 2010-11-05
Have network!
Thanks


Now Update Manager refuses to do anything except ask for my password over and over.

Which is fun, I guess.

---

