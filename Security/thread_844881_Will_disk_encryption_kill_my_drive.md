---
title: "Will disk encryption kill my drive?"
date: 2008-06-30
forum: Security
---

### Post by socceroos on 2008-06-30
Hello all,

I've just bought myself a new Dell laptop and have installed Ubuntu 8.04 (wiping Windows off) with full disk encryption.

But I'm a bit worried. Will disk encryption kill my hard drive a lot quicker than if I wasn't using it? I've been searching reviews but can't find anyone's opinion on the issue.

Any info would be much appreciated.

Socceroos

---

### Post by socceroos on 2008-06-30
Hmmm, I seem to be hearing constant disk reads.......

---

### Post by hyper_ch on 2008-06-30
no, it will not kill it faster.

---

### Post by /etc/init.d/ on 2008-06-30
Encryption should not make your drive seek or write any more than it usually does, but even if it does, hard drives are engineered to run and operate constantly for years on end.  

If you're worried about hard drive wear, you should check out what your BIOS and operating system power management settings are, especially if you're using a laptop.

In general it is not worth worrying about, though.

---

### Post by hyper_ch on 2008-06-30
only the processor has to perform more work as it has to de/encrypt on the fly.

---

### Post by shad0w_walker on 2008-06-30
The constant reading and writing shouldn't have anything to do with the encryption, most likely it's something indexing files for the search backend (Can't remember what it is in 8.04) or some program that is writing to the drive for whatever reason.

---

### Post by socceroos on 2008-06-30
Thanks for the replies fellas.

I thought Hardy had disabled indexing for the release, but I'll check into it.

---

