---
title: "torrenting and security"
date: 2009-11-29
forum: Security
---

### Post by Engromada on 2009-11-29
I have been havign issues downloading from torrent clients. i have the ports open correctly in my ip tables file, but no luck. the next step would be to follow advice i saw on forums saying to set the ports in my router to forward to my pc, but doesn't this open me up to all sorts of malicious mischief?

---

### Post by el Tedward on 2009-11-29
I'm someone of a n00b, but my n00bish gut instinct is that you would mostly only have to worry about the level of security built into/around the things operating under the ports you open up.

---

### Post by Lars Noodén on 2009-11-29
> **Engromada said:**
> I have been havign issues downloading from torrent clients. i have the ports open correctly in my ip tables file, but no luck. the next step would be to follow advice i saw on forums saying to set the ports in my router to forward to my pc, but doesn't this open me up to all sorts of malicious mischief?

You have to worry only about the security of the service that is listening to that open port.  If you have nothing listen, then there should be little to no problem.  

If you have something listening, then you are at the mercy of that application and want to lock it down.  Security is a matter of adding and managing layers.  Two possible ways are with a systrace policy or an SELinux policy.  Neither are new, but SELinux is fairly new to Ubuntu so you'll be breaking a bit of new ground.

Which torrent application?  Transmission? Ktorrent? btpd?

---

### Post by Engromada on 2009-11-29
it's the transmission bit-torrent client.

would AppArmor do the job of locking it down nicely? been reading about that and it sounds about the right tool?

---

### Post by movieman on 2009-11-29
> **Engromada said:**
> would AppArmor do the job of locking it down nicely? been reading about that and it sounds about the right tool?

Yes. If you configure an AppArmor profile properly it should ensure that if there is an exploitable hole in the torrent software that anyone who managed to hack in that way would not be able to do anything that the torrent software couldn't do.

For example, limit the software so it can only write to one specific directory where you downloaded the files, and can only read from that directory and those files required to start up (configuration, hostnames etc). Then if they try to read or write elsewhere the attempt would fail.

---

