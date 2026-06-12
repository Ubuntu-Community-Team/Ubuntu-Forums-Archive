---
title: "How to regenerate parity in RAID 5/6 system"
date: 2015-08-26
forum: Server Platforms
---

### Post by kim19 on 2015-08-26
**Is there any way to remake parity in RAID?**

Let me explain the situation, the conditions of this problem.

- current system is ok so far.
- However parity parts are wrong. so that, data would be broken after kind of rebuild or assemble occur.
- We think parity parts are contaminated by RAID_ZERO_COPY option of kernel.
- We expect that it will be ok after we rewrite parity part with proper system which doesn't use RAID_ZERO_COPY option.
- Linux system using raid 5 nor 6.
- We don't want to interrupt current running system. 
- We are looking for some solution that rewrite parity parts only during current system is running.

Any suggestion?

I really appreciate any help you can provide.

---

### Post by CharlesA on 2015-08-26
Are you not able to run a verify against the array? I think this should work: [https://www.thomas-krenn.com/en/wiki/Mdadm_checkarray](https://www.thomas-krenn.com/en/wiki/Mdadm_checkarray)

But before you do anything I would suggest copying the data off the array or backing it up somehow in case you need to rebuild it from scratch to get the parity to be recreated.

As far as the "RAID_ZERO_COPY" option.. I haven't found that listed anywhere, what OS are you running and what version?

---

### Post by kim19 on 2015-08-30
thanks. I'll try.
the OS is customized linux by freescale.

---

### Post by CharlesA on 2015-08-30
Never heard of that company, but it looks to be an embedded system.

Maybe try reaching out to them and see if they have any ideas?

---

### Post by kim19 on 2015-09-01
Of course, we did it.
Unfortunately we didn't hear any useful answer from them.

---

### Post by CharlesA on 2015-09-01
> **kim19 said:**
> Of course, we did it.
Unfortunately we didn't hear any useful answer from them.

Heh, figures. Reminds me of my experience with a SNAPserver at work. Hopefully you are able to rebuild the parity data after making a backup.

---

