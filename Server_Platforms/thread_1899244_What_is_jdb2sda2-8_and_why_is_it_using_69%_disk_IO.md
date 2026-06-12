---
title: "What is jdb2/sda2-8 and why is it using 69% disk IO?"
date: 2011-12-23
forum: Server Platforms
---

### Post by c3ntury on 2011-12-23
I've tried googling to find out, but I've got no idea why this is happening :/

[IMG]http://localhostr.com/file/ycQuxyg/Untitled.png[/IMG]

Does anyone know what this process is, and why it's using so much disk IO?

---

### Post by lisati on 2011-12-23
Probably something to do with "[journaling block device]("http://en.wikipedia.org/wiki/Journaling_block_device")"

---

### Post by c3ntury on 2011-12-23
> **lisati said:**
> Probably something to do with "[journaling block device]("http://en.wikipedia.org/wiki/Journaling_block_device")"

So how can I stop it safety? :/

Edit ~ or at least, how can I perhaps limit it to only using a certain percentage of my disk IO?

---

