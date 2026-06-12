---
title: "Studio 12.10 Overheating on HP P6310Y"
date: 2012-11-25
forum: Ubuntu Studio
---

### Post by kdec on 2012-11-25
Hi. I'm new to linux but successfully installed Ubuntu Studio 12.10 on my HP P6310Y Desktop PC (Duel boot w/Windows 7).

But it's been overheating and shutting down. 

It seems the CPU fan doesn't come on when needed, like it does while running Windows 7.

Please Help!

Thanks!
Ken

---

### Post by bumBumBUM on 2012-11-25
> **kdec said:**
> Hi. I'm new to linux but successfully installed Ubuntu Studio 12.10 on my HP P6310Y Desktop PC (Duel boot w/Windows 7).

But it's been overheating and shutting down. 

It seems the CPU fan doesn't come on when needed, like it does while running Windows 7.

Please Help!

Thanks!
Ken

Hi,

there are several things that you can try.

1. Check the BIOS for any fan related option
2. Disable fan control in linux with boot parameter thermal.off=1. This should leave the fan control down to the BIOS (which should be perfectly capable for this function). Careful with this option though, make sure you pay attention if you use it and read up about it first.
3. Is your graphics card overheating? try the proprietary drivers or add some powersaving options to the open source ones if you can.
4. Search on a more generic ubuntu forum. It's unlikely that your issue relates directly to ubuntu studio.
5. Search on the HP forums.

---

