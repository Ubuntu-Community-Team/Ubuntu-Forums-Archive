---
title: "Command for figuring out if Dapper is AMD64/i386"
date: 2006-07-15
forum: The Cafe
---

### Post by compwiz18 on 2006-07-15
I'm not sure this is the right forum for it, but here goes...  Is there a command that you can run in the terminal that will tell you whether someone is running the AMD64 version or the i386 version?  Sometimes people have an AMD 64 proccessor, but are running the i386 version (me!), but say they have AMD 64 Dapper (not me :P), which adds another layer of difficulty to troubleshooting.

Thanks in advance.

---

### Post by compwiz18 on 2006-07-15
Does **apt-get --version** work?  I think it might, it tells what it was compiled on...

---

### Post by OffHand on 2006-07-15
```
uname -r
```

---

### Post by dabear on 2006-07-15
I believe the command lsb-release can give you some info too

---

### Post by compwiz18 on 2006-07-15
> **dabear said:**
> I believe the command lsb-release can give you some info too
Hm...it says command not found...

---

### Post by dabear on 2006-07-15
should be something like 
```
lsb_release -a
``` :)

---

### Post by Compucore on 2006-07-15
Or what you can do before the computer boots up. Just hit escape before grubs comes up and you can see which kernels are there. I know I had made some manual changes in the grub so that I didn't have to worry for the IRQ's Since  one of the newer release of the kernel had trouble see my irq. I just inserted irqpoll for my old amd K62 processor over here. And sure enough it worked. 

Compucore

---

