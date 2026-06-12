---
title: "Auto-shutdown when AC power is off. Cron?"
date: 2009-07-06
forum: Server Platforms
---

### Post by zmjuanpablo on 2009-07-06
Hi Ubuntu community:

I've installed Ubuntu Server in my old laptop. It's battery life is about 5 minutes so it's still useful if there's a blackout or something...

But, is there a way to safely **auto-shutdown it if the AC Power runs off?** i've read about configuring Cron to do it at a certain *time*, but nothing about events like this.

Any advice?

Apologies in advance for my poor english =(

---

### Post by Boondoklife on 2009-07-06
Well Im sure you could do some string mangling and get the status out of /proc/acpi/ac_adapter/AC/state and from there check the status. If it reads offline then issue the shutdown command.

---

