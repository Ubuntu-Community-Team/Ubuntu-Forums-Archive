---
title: "hyper-v integration"
date: 2013-03-26
forum: Server Platforms
---

### Post by Vegan on 2013-03-26
I was wondering if the server variants of Ubuntu have any software that make information available to Hyper-V such as health and memory demand along with the IP address in use etc?

---

### Post by CharlesA on 2013-03-26
If they have anything, they should be built into the kernel. I was running a debian box in HyperV but I don't recall if it reported CPU usage or whatever to the hyper-v manager, though.

I won't be able to check for sure for a couple weeks.

---

### Post by sandyd on 2013-03-26
> **Vegan said:**
> I was wondering if the server variants of Ubuntu have any software that make information available to Hyper-V such as health and memory demand along with the IP address in use etc?
I was looking around in the vanilla kernel the other day, and noticed that Hyper-V support was added.
[s]If you give me a while, I might get some kind of screenshot up...[/s]
[https://dl.sandyd.me/public.php?service=files&t=40b34336a7c00b16f0e311dc01f46d66](https://dl.sandyd.me/public.php?service=files&t=40b34336a7c00b16f0e311dc01f46d66)

---

### Post by Vegan on 2013-03-29
Hyper-V can see CPU utilization but not memory demand. There is a feature to dynamically allocate RAM depending the load. Another tab shows the network MAC and IP address.

I run everything virtualized simply as this way if it blows up, I am safe.

---

