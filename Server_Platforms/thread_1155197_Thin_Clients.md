---
title: "Thin Clients"
date: 2009-05-10
forum: Server Platforms
---

### Post by bilboe on 2009-05-10
Hi Everyone,
I am going to be managing a small (4-8 computer) thin client rollout.

I have read the stuff about Ubuntu LTSP, and the quick install guide, which I am assuming is for the server setup. Once I have done this, how do I set up my thin clients? Will this work over wan, not just lan. Does this require extra configuring?

Thanks!

-Bilbo

---

### Post by pmla on 2009-05-10
Good question.
Also interested in how it works with the thin clients!?

---

### Post by albinootje on 2009-05-10
> **bilboe said:**
> Will this work over wan, not just lan. 

Over WAN ? Sounds scary as most data traffic will be unencrypted I think.
> 
Does this require extra configuring?

I tested this around 2006 I think with Edubuntu. For the clients it is basically a matter of network booting them afair.
I remember I had a hard time with it, with various different network cards, and making it all work properly in the end.
I think I used VirtualBox or Qemu to test the server first, before using a real network card with bootrom.

---

