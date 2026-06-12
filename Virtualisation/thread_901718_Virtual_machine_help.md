---
title: "Virtual machine help"
date: 2008-08-26
forum: Virtualisation
---

### Post by Umac on 2008-08-26
I run Ubuntu on my mac using a virtual box that's free by sun. It's called Virtual Machine. The problem is it's REALLY slow and constantly freezing. Is there a way to speed it up? Or even a different free virtual box?

---

### Post by aysiu on 2008-08-26
Maybe VirtualBox?

How much RAM do you have?

---

### Post by Umac on 2008-08-27
> **aysiu said:**
> Maybe VirtualBox?

How much RAM do you have?

Edited post. I use virtual box. I have 667 RAM.

---

### Post by bodhi.zazen on 2008-08-27
Most likely the problem is you are a little light on RAM. How much RAM did you give the guest ?

---

### Post by aysiu on 2008-08-27
667 MB of RAM is too little to be running a virtual machine and expect to get good performance.

I guess you'd have to allocate 192 MB or 256 MB for the guest and the rest for the host?

That's also a really odd amount. Doesn't RAM usually come in 128 MB, 256 MB, 512 MB, 1 GB, or 2 GB sticks?

Are you sure it's not a 667 MHz processor and a different number for the RAM?

---

### Post by Umac on 2008-08-30
> **aysiu said:**
> 667 MB of RAM is too little to be running a virtual machine and expect to get good performance.

I guess you'd have to allocate 192 MB or 256 MB for the guest and the rest for the host?

That's also a really odd amount. Doesn't RAM usually come in 128 MB, 256 MB, 512 MB, 1 GB, or 2 GB sticks?

Are you sure it's not a 667 MHz processor and a different number for the RAM?

Yes its a 667MHz processor. I'm not to sure about my RAM.

---

### Post by bodhi.zazen on 2008-08-30
Good pickup aysiu

Umac: open a terminal and enter :

```
free -m
```

---

### Post by Umac on 2008-09-06
> **bodhi.zazen said:**
> Good pickup aysiu

Umac: open a terminal and enter :

```
free -m
```
Okay I'll do that. Thanks.

---

