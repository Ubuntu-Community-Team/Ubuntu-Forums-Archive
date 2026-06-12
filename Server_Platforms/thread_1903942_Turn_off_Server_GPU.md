---
title: "Turn off Server GPU"
date: 2012-01-03
forum: Server Platforms
---

### Post by dh04000 on 2012-01-03
Hello, I have a server related question. The OS in question is not Ubuntu server, but MineOS Crux, which is CRUX linux based, but basic bash/linux command would be the same right?

Ok, I have an old laptop in which the GPU broke. It still trus on, but does not export video anymore. So I turned it into a minecraft server.

Now, I need to turn off the GPU because its creating ALOT of heat and wasting power.

Its a NVidia 7900GS GPU, and I can access this server using PUTTY.

How do I go about, via a PUTTY terminal, disable the videocard for this laptop?

Thanks.

---

### Post by rubylaser on 2012-01-04
To do this properly, you'd want to turn off the GPU in the BIOS (if your motherboard's BIOS supports it), which is fairly tricky when you don't have a monitor to view it with.

---

### Post by 2F4U on 2012-01-04
I would say that it is not possible. I haven't seen a laptop bios where you could turn of the GPU. Even if your laptop provides that option, you would need to be able to access the BIOS. There is no way to turn the GPU of through the operating system.

---

### Post by dh04000 on 2012-01-04
Could I put the GPU in a really DEEP sleep state from the OS? That could work too.

EDIT: Before anyone asks, I have tried removing the gpu. The laptop bios won't finish its sequence and allow booting of the OS IF the gpu is missing.

---

### Post by dh04000 on 2012-01-04
double post

---

### Post by 2F4U on 2012-01-04
> **dh04000 said:**
> Could I put the GPU in a really DEEP sleep state from the OS? That could work too.

The open source drivers don't have power management fully implemented. The proprietary nVidia drivers would be better at power management but I guess your card is not supported (haven't checked that). However, its questionable whether the hassle is worth the benefit since no graphics driver I know of would allow you to put the GPU in a deep sleep state. The only thing they are doing is to reduce the internal frequency.

---

### Post by dh04000 on 2012-01-04
> **2F4U said:**
> The open source drivers don't have power management fully implemented. The proprietary nVidia drivers would be better at power management but I guess your card is not supported (haven't checked that). However, its questionable whether the hassle is worth the benefit since no graphics driver I know of would allow you to put the GPU in a deep sleep state. The only thing they are doing is to reduce the internal frequency.

Decreasing its frequency would be nice.

Its an Nvidia 7900GS, which is supported by NVidia 192.xx driver family. I have no idea how to set up this driver using command line from putty, or how to use it though.

---

