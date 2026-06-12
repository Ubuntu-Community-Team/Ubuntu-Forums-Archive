---
title: "Support for new 8 GB Raspberry Pi"
date: 2020-05-30
forum: Server Platforms
---

### Post by plazman30 on 2020-05-30
Does anyone know if Ubuntu Server for Raspberry Pi x86-64 will handle all 8 GB of RAM on these new PIs?  I just ordered one and was planning to drop Ubuntu Server on it.  If no one knows the answer, I would be happy to test it out and report back, once my Pi gets here.  Just tell me what I need to do to confirm Ubuntu sees the RAM AND can use it.

---

### Post by LHammonds on 2020-05-30
The RPi4 has a 64-bit CPU but there are no officially-supported 64-bit OS.  There is a beta version of 64-bit Raspbian being developed.

32-bit operating systems have a limitation of 4GB of addressable memory.

Using PAE (Physical Address Extensions), a 32-bit OS can access up to 64 GB but each process can only address 4GB of physical memory so don't expect a database server to use more than 4GB.

Please note that Raspbian does NOT support PAE so the 32-bit version of Raspbian is utterly useless for any Pi with more than 4GB of RAM.

The [64-bit ARM version of Ubuntu]("https://ubuntu.com/download/server/arm") should be able to see and use all 8GB of RAM.

I don't have one but from what I understand of the architecture, the above should hold true.

LHammonds

---

### Post by plazman30 on 2020-05-31
When it arrives, I'll have to put Ubuntu Server on it and report back.

---

### Post by TheFu on 2020-05-31
+1 for what LHammonds wrote.

Cannot imagine any reason that a 64-bit OS wouldn't see all the RAM, unless there is some forced hardware limit configured in boot.txt

---

### Post by plazman30 on 2020-08-31
It does see it.

---

### Post by QIII on 2020-08-31
How much is detected?

---

### Post by LHammonds on 2020-08-31
> **QIII said:**
> How much is detected?
I imagine the whole thing...typical of an 8GB system.

My post was to clarify what was available at the time of writing that post...and to be careful to NOT use a 32-bit OS.  They now have direct support for Raspbian 64-bit and other operating systems including Ubuntu Server 20.04.1 as [shown here]("https://www.raspberrypi.org/downloads/").

LHammonds

---

### Post by ameinild on 2020-09-01
> **QIII said:**
> How much is detected?

Unfortunately I only have a 4 GiB RPi 4, and the memory detected in this is 3793 MiB (or 3.7 GiB).

I assume this is because it shares video memory, so on that account I would assume that the 8 GiB version would have 7.7 GiB available.

---

