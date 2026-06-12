---
title: "Hibernation broken after last kernel upgrade"
date: 2008-07-23
forum: System76 Support
---

### Post by perce on 2008-07-23
Dear Tom,

after the last kernel upgrade, my DARU1 doesn't hibernate anymore, it hangs with a kernel panic, and bumps a bunch of numbers and error messages on the screen. Unfortunately the error messages related to the kernel panic are not registred in the logs. I'll post them tomorrow morning (Italian time).

---

### Post by perce on 2008-07-24
Here is the error message as promised:

```

[ 2106.706848] Code: c5 74 ec 8b 4c 24 18 89 c2 89 d8 89 34 24 ff 17 89 e9 89 c6
89 d8 ff 57 10 eb b0 8d 76 00 8d bc 27 00 00 00 00 53 8b 50 20 89 c3 <ff> 52 1c
8b 43 20 8b 40 38 e8 dc 3b e9 ff 89 d8 5b e9 a4 11 ed
[ 2106.709226] EIP: [<c02bc8f6>] tcf_destroy+0x6/0x20 SS:ESP 0068:ef74be7c
[ 2016.709368] Kernel panic - not syncing: Fatal exception in interrupt

```

The kernel I'm using is:

```

Linux Bach 2.6.24-20-generic #1 SMP Thu Jul 17 16:29:46 UTC 2008 i686 GNU/Linux

```

---

### Post by thomasaaron on 2008-07-24
I'll image a darter and see if I can replicate the problem.

Question: Do you have any virtual machines running when you hibernate and get these errors?

What happens if you hibernate with no apps running? Same thing?

---

### Post by perce on 2008-07-24
> **thomasaaron said:**
> I'll image a darter and see if I can replicate the problem.

Question: Do you have any virtual machines running when you hibernate and get these errors?


No

> 
What happens if you hibernate with no apps running? Same thing?

Yes. Of course "no apps" here means just a Gnome session running. I'll try more tests tonight, like booting an older kernel, or hibernating with no X running, and I'll post the result.

---

### Post by thomasaaron on 2008-07-24
So, with my computer completely updated, my hibernate and suspend work perfectly.

Here is my kernel version (and I'm fully updated)...

Linux thomasaaron-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

Since you are a version ahead of me, I'm guessing that you have proposed updates turned on. So, you're a little ahead of the curve on this one.

---

### Post by perce on 2008-07-24
Yes, it works with the 2.6.24-19. I didn't notice that it was only a proposed update. I'll stick to the older kernel, if I have time in the week end, I'll file a bug report against the newer kernel on the Ubuntu launchpad. Thank you.

---

### Post by lefox on 2008-11-03
Hi,

I'm currently experiencing the same problem as described above. My current kernel is
 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

It started from the auto update to 2.6.24-20 or 21...
I haven't tested much though yet.

---

### Post by thomasaaron on 2008-11-04
lefox,

What is your System76 model number?

---

### Post by lefox on 2008-11-04
Hi thomasaaron,

My mistake as I am not using system76 (I'm not even sure what it is :))
I just looked in the forum for somebody having the same error than me and found this one but didn't check the actual forum title.
I'll try to find a more general forum.

Thanks for the reply anyway!
For information, I am using a Panasonic R5 laptop.

---

