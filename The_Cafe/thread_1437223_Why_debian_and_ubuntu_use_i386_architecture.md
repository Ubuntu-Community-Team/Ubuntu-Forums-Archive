---
title: "Why debian and ubuntu use i386 architecture"
date: 2010-03-23
forum: The Cafe
---

### Post by anantgowerdhan on 2010-03-23
Hi,

Recently I found that the openUSE uses i586 and Fedora uses i686 architecture but Debian and Ubuntu still uses i386. I would like to know the difference between these and also what are the advantages using i686 over i386.

I will appreciate any information if anyone has about this. 

Regards,
Anant

---

### Post by steindor2 on 2010-03-23
> **anantgowerdhan said:**
> Hi,

Recently I found that the openUSE uses i586 and Fedora uses i686 architecture but Debian and Ubuntu still uses i386. I would like to know the difference between these and also what are the advantages using i686 over i386.

I will appreciate any information if anyone has about this. 

Regards,
Anant
```
Linux ipad 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux
```

would you look at that, my ubuntu is on i686;)

---

### Post by cguy on 2010-03-23
That's just the generic name for the 32 bit platform.

---

### Post by xc1024 on 2010-03-23
Actually, it's not exactly generic name. It refers to i386-compatible processors, so basically anything Pentium 2 and up. i386 is ancient and was replaced by i486. The i486 got replaced by i586 and now i586 is getting replaced by i686.

If your computer NEEDS to run i386, it probably remembers dinosaurs. i386 kernels are shipped with big systems for compatibility reasons (why Ubuntu, it puzzles me. It won't run on less than about 380 MB of RAM)

---

### Post by JT9161 on 2010-03-23
> **xc1024 said:**
> It won't run on less than about 380 MB of RAM


I've run on 256MB comfortably, you may be thinking of the (normal) Live CD

---

### Post by swoll1980 on 2010-03-23
> **xc1024 said:**
> Actually, it's not exactly generic name. It refers to i386-compatible processors, so basically anything Pentium 2 and up. i386 is ancient and was replaced by i486. The i486 got replaced by i586 and now i586 is getting replaced by i686.


Actually the 686 is the Pentium. They are on 786 now.

---

### Post by Shining Arcanine on 2010-03-23
> **steindor2 said:**
> ```
Linux ipad 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux
```

would you look at that, my ubuntu is on i686;)

My laptop seems to be on i686 too, although I compiled the kernel specifically for my processor, so it should have better optimizations. The pre-emption support probably makes the biggest difference.

```
Linux laptop 2.6.33.1 #1 SMP PREEMPT Mon Mar 15 23:10:01 EST 2010 i686 Genuine Intel(R) CPU T2400 @ 1.83GHz GenuineIntel GNU/Linux
```

> **swoll1980 said:**
> Actually the 686 is the Pentium. They are on 786 now.

The i786 name has not really been defined to signify any particular extension of i686, which is why it is not even in use. You probably could call it i686++.

---

### Post by mickie.kext on 2010-03-23
> **swoll1980 said:**
> Actually the 686 is the Pentium. They are on 786 now.

No, Pentium is 586(P5), while 686(P6) is Pentium Pro, Pentium II and Pentium iii. They cnaged name they count with Pentium IV so 786 do not exist. They called Itanium P7 but that is not x86 so it is only P7, not 786.

---

### Post by foxmulder881 on 2010-03-23
To the OP, just forget all the mumbo jumbo of keep it simple and think of it this way. Generally, anything i*86 is 32bit cpu architecture and AMD64 or EM64T is 64bit cpu architecture.

---

