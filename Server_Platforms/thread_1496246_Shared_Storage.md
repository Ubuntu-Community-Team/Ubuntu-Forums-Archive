---
title: "Shared Storage"
date: 2010-05-29
forum: Server Platforms
---

### Post by ductiletoaster on 2010-05-29
My Question is simple. I have a couple computers that im goin to set up as a small cluster. Now i was wondering how would i go about having them share the same disk space. 

Should they share just the a main directory or more? Would each computer still need a HDD for System files and swap? Give me details. I am familiar with clustering but i have little experiance with shared drives.

---

### Post by craigp84 on 2010-05-29
You can share as much or as little as you want between the two. There's only a couple of filesystems that physically can't be shared (/proc, /sys etc.), and only a couple more that would be a bad idea to share, but technically possible if you want to (/etc, /var, /usr/local).

A machine doesn't need a local HDD, if you're building a compute node it might even be a poor idea (extra expense, extra power consumption but most importantly, extra failure scenario).

Your question's too broad for me to give you much insight. What do you want to do with it? Lots more details please, it's really not a simple field if you want to get it right.

---

### Post by ductiletoaster on 2010-06-03
Sorry to take so long to replay hope fully your still checking this. Well Im not new to setting up servers however, i must say im a little confused how the best way to setup the servers so that they all run the same instance of an OS such as Ubuntu Server and share data?
1) Files system?
2) i have five computers of different hardware types that are all canidates.  I was thinking about having four of them running Ubuntu Server edition headless. out of those four three would be as u called them compute nodes and the other would host the drives. Is that possible? The fith computer would act as a workstation. Should it to be apart of the cluster of not?

Now most of this is just for learning... Though the idea is to eventually use it to host my webserver, FTP and so on!

---

### Post by ductiletoaster on 2010-06-03
what about shared nothing? I know that it basically means that instead of having a single point of failure such as  a single hard drive it instead maintains multiple copies in different areas essential. 

So would each computer then need a hard drive or just as many copies as i want to have. Is this even worth it?

COMPUTERS AVAILABLE
--------------------------
AMD Athlon 64 3700 2.2 ghz (This one i was thinking about making a Gui workstation)
2gb DDR 400 RAM
200 gb HDD

AMD Athlon 64 3200 2.0 ghz
512mb DDR 400 RAM (might be 1gb don't remb)
160gb HDD

Pentium 4 1.7 ghz
256mb RAM
NO! HDD

Pentium 4 1.7 ghz
256mb RAM
NO! HDD

Celeron 667 mhz
192mb (might be 128mb)
15gb HDD

---

### Post by ductiletoaster on 2010-06-06
Nobody?

---

### Post by craigp84 on 2010-08-26
Hi,

I don't visit here often, only when i'm not getting enough of a challenge in my day job i come to help other people's interesting problems :)

It sounds like you want to learn about clustering (rather than have a business itch to scratch), this is cool. Since you are free to get wacky with this, i suggest looking into ClusterKnoppix.

It is a simple to use implementation of seriously cool clustering software -- processes can migrate between nodes!

Once you've done that i'd go looking at cluster storage solutions and get your head round the different approaches.

For the business world there's been a step away from OS level clustering and now a lot of companies have decided implementing the cluster in user space is a better way to go, so i wouldn't spend too much time on the traditional linux cluster format other than to understand the concepts. Of course some businesses use this approach but it is my experience that most are now running their cluster jobs ontop of cluster middleware.

Hope this helps

---

