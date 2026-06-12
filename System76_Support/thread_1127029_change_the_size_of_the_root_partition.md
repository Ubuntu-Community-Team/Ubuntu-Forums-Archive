---
title: "change the size of the root partition?"
date: 2009-04-16
forum: System76 Support
---

### Post by xakh on 2009-04-16
the part of the system that isn't the home partition on my pangolin performance is ridiculously small, weighing in at only 10 gb. I would like to up it to 20 gb, is there a way I can do this, without totally destroying everything?

---

### Post by dai_vernon on 2009-04-16
Yes, just not while you have booted from it.  Download an ubuntu live CD and go to system > administration > Partition Editor and resize from there

---

### Post by jdb on 2009-04-16
> **xakh said:**
> the part of the system that isn't the home partition on my pangolin performance is ridiculously small, weighing in at only 10 gb. I would like to up it to 20 gb, is there a way I can do this, without totally destroying everything?

The operating system would normally never use 10G.
Ubuntu/synaptic/apt puts stuff in /, if you put your stuff in /home then / won't run out of space.

jdb

---

### Post by sharon.gmc on 2009-04-17
just download an ubuntu live CD.

---

### Post by thomasaaron on 2009-04-17
This tutorial is about dual booting windows, but the partitioning part should give you a good idea of how to use Partition Editor from a live CD.

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by xakh on 2009-04-17
Cool, thanks for the help. are these non destructive resizings? as in, do I not lose data?

---

### Post by thomasaaron on 2009-04-17
Yes. But it is good practice to create a backup anyway.

---

