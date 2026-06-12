---
title: "[REQUEST] qemu cvs"
date: 2005-02-20
forum: Ubuntu Backports
---

### Post by TravisNewman on 2005-02-20
I'd like to see the qemu cvs backported, just for the new kqemu module:
[http://slashdot.org/article.pl?sid=05/02/19/1538231&tid=190&tid=126&tid=1](http://slashdot.org/article.pl?sid=05/02/19/1538231&tid=190&tid=126&tid=1)

---

### Post by jdong on 2005-02-20
> 
Terms of Use
The QEMU Accelerator is free to use, but it is a closed source proprietary product. You are not allowed to distribute it yourself to other people without an explicit authorisation. Distributors wishing to include the QEMU accelerator on CDs, ISO images or packages must contact the author to know the exact terms.

I can't do anything about that new accelerator module,  and I'm not sure how stable qemu's CVS branch is. Anyone want to comment on the stability?

---

### Post by TravisNewman on 2005-02-20
ah, ok, I didn't know about the distribution snag. I knew it had a questionable license, but not that it couldn't be distributed. That's out then ;) the qemu CVS seems to be stable from what I've seen.

---

### Post by ruben_b on 2005-06-08
i know this is an older topic but i´d like to use kqemu and had problem with compiling it. so i thought, why should i compile when i perhaps can use a deb!?

you´re saying something that you can´t backport it, because of license problems, but i read the following about using kqemu on there webpage:

"The QEMU Accelerator is free to use, but it is a closed source proprietary product. You are not allowed to distribute it yourself to other people without an explicit authorisation. Distributors wishing to include the QEMU accelerator on CDs, ISO images or packages must contact the author to know the exact terms."

so isn´t there a way to ask them and then backport it?

---

### Post by AgenT on 2005-06-08
[QUOTE=ruben_b]i know this is an older topic but i´d like to use kqemu and had problem with compiling it. so i thought, why should i compile when i perhaps can use a deb!?

you´re saying something that you can´t backport it, because of license problems, but i read the following about using kqemu on there webpage:

"The QEMU Accelerator is free to use, but it is a closed source proprietary product. You are not allowed to distribute it yourself to other people without an explicit authorisation. ***Distributors wishing to include the QEMU accelerator on CDs, ISO images or packages must contact the author to know the exact terms.***"

so isn´t there a way to ask them and then backport it?[/QUOTE] [added bold/italic]

Nice catch! Will anyone that is part of the backports project email the author and ask? It would also be a good idea to ask about cvs *and* official builds because it may be that CVS is excluded while the official build is not, or something to that effect (yes, that seems far fetched, but it is better to ask).

---

### Post by sidd-tx on 2005-12-09
I used Lunde's HOWTO and it worked like a champ. But I have never used the qemu package in the repositories. Is the kqemu that much faster than qemu?

---

