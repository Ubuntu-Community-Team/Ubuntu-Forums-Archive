---
title: "Nvidia driver pain"
date: 2012-07-10
forum: Server Platforms
---

### Post by Trunkles on 2012-07-10
Hi folks.

I'm running a server with an nvidia graphics card in it. The card has a DVI and a VGA output. The monitor is analogue but plugged into the VI socket via an adapter.

I remember installing nvidia drivers but can't remember exactly what that entailed.

Anyway, I rebooted the server and now I'm getting the following in syslog repeatedly, as in umpteen times every second!

```
[drm] nouveau 0000:01:00.0: unplugged DVI-I-1
```

Any idea on how to get rid of this nuisance?

Thanks.

Simon.

---

### Post by SeijiSensei on 2012-07-10
You're running the open-source nouveau driver.  You could try using the proprietary driver from NVIDIA by running "sudo apt-get install nvidia-current" and see if that helps.

Any reason why you just can't use the VGA port?

---

### Post by Trunkles on 2012-07-10
I've installed the current driver and it hasn't made a difference, probably because I'm dumb!

The card has two DVI connectors, an HDMI and no VGA at all!

However, the problem now seems to have gone away. YAY! :D

Thanks for your help. :)

Simon.

---

