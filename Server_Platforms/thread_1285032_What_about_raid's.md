---
title: "What about raid's?"
date: 2009-10-07
forum: Server Platforms
---

### Post by sarfimenez on 2009-10-07
Hi, im new to this comunity, and i have a question, and is this,

i want to implemet a raid 1 or 5 in my server, and i dont see in any page how many resources of the pc consume a particular raid implemented by software. my question is 
how many resources of the pc consume a raid 1 or 5 implemented by software, it requires a minimum of ram or procesor speed??

well taht is my question, thank for your time spent reading it :).

---

### Post by psusi on 2009-10-07
Raid 5 uses some cpu for computing the checksums, but on a modern processor, it does not amount to much.  Raid 1 ends up using a little more cpu time indirectly by virtue of the fact that it is writing everything twice, but this is negligible.  There are no "minimum specifications".

---

### Post by cariboo on 2009-10-07
This really has nothing to do with security, moved to server platforms.

---

### Post by sarfimenez on 2009-10-08
tanks psusi for the answer, and sorry for put it in the forum of security but i really no has idea where post it.

---

### Post by fjgaude on 2009-10-08
Resources, not much... I've run raid5 using as little a single-core 1.66MHz CPU and one gig of RAM. Worked fine...

A raid1 takes only two drives; raid5, a minimum of three.

What is the useage of the array?

---

