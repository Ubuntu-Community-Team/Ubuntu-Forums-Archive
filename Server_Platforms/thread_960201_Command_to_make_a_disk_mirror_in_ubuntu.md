---
title: "Command to make a disk mirror in ubuntu"
date: 2008-10-27
forum: Server Platforms
---

### Post by Diana Rogger on 2008-10-27
Hi Everyone,

I am in a production environment.

Is there someone who can tell me how to do this in ubuntu?

I need to do this asp.

I have 250 GB disk.

I bought an other disk (250 GB)

How can I mirror this disk for redundancy reason?

Thank you in advanced

---

### Post by hyper_ch on 2008-10-27
do you mean a raid?

---

### Post by ilrudie on 2008-10-27
[http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.6](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.6)

---

### Post by Diana Rogger on 2008-10-29
>> do you mean a raid?

Yes a raid0 or a raid1

My first disk is 250GB

I am afraid to make a mistake causing my data or disk to damage.

So I want to be very sure about the exactly steps to take because of the fact that it is a **working environment**. Ok, I don't think this have to be a problem, because I can put the website that is on my server for some minutes down to do this steps.

Thanks

---

### Post by ilrudie on 2008-10-29
Always backup data you can't stand to lose before doing things like this.  The chances are good that everything will work just the way its meant to but if it doesn't you don't want to lose anything important.

---

