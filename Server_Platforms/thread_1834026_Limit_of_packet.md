---
title: "Limit of packet"
date: 2011-08-26
forum: Server Platforms
---

### Post by sulvus on 2011-08-26
Hi,

Today I have an emulator with over 1000 simultaneous connections at times, but to reach that amount (about 1100-1200) begins to lose packet, I have reviewed the traffic of packets and I've seen that does not pass the packet 7999X packet / s.
 I think the limit is at 1024 but I do not know the problem.
 I asked and they told me I have to recompile the kernel by modifying a data, but such action before requesting your help in case we should not be that. If it is necessary to recompile the kernel, which I have to change data?

Sorry for my bad english, I use translator.

Thanks.

Xavier V.

PD: I use Debian

---

### Post by Dangertux on 2011-08-27
Sounds like you might have an issue with not having enough file descriptors. 

Try recompiling the kernel with support for more. There are numerous tutorials for this, I  am on my phone so I can't link at the moment, google should help you out though.

---

### Post by sulvus on 2011-08-27
I have reviewed the file descriptors and are correct, and I edited it to the limits of 90000.
 The problem is not the file descriptors.

---

