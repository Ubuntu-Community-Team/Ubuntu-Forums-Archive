---
title: "Is it less likely to get a BIOS virus in GNU/Linux than other OS's?"
date: 2012-07-07
forum: Security
---

### Post by Rytron on 2012-07-07
Hi.

Is it less likely to get a BIOS virus in GNU/Linux than windows or apple or FreeBSD etc.?

Please leave a comment, especially if you ever updated the BIOS or successfully removed a BIOS virus.

---

### Post by Redblade20XX on 2012-07-07
If the attacker has access to the physical system then it doesn't matter what OS you have. 

From a pure software point of view, you'll have the highest probablility of getting BIOS infected from whatever platform your BIOS manufacturer has chosen to build the BIOS updater in (most likely windows).

-Red

---

### Post by uRock on 2012-07-07
Moved to ***Security Discussions***.

---

### Post by Hungry Man on 2012-07-07
Any BIOS attack would have to be fairly targeted. It's basically incredibly unlikely on any platform. The two BIOS infecting malware I've ever heard of attacked Windows users though.

---

### Post by Rytron on 2012-07-08
> **uRock said:**
> Moved to ***Security Discussions***.

Sorry, I was not certain as to where to launch the thread. :oops:

Thanks for the info, Redblade20XX & Hungry Man.

---

### Post by samiux on 2012-07-08
> **Rytron said:**
> Hi.

Is it less likely to get a BIOS virus in GNU/Linux than windows or apple or FreeBSD etc.?

Please leave a comment, especially if you ever updated the BIOS or successfully removed a BIOS virus.

Long time ago when there is no Linux, there is a virus that can infect the BIOS and making the hardware malfunction.

BIOS is written on a flash ROM that is writable.  That mean, it can be written something bad by hackers.  However, almost all BIOS developers have protect their BIOS from being written by malware by design since the last attack.

It is still unknown that if the developers have do their best to secure the BIOS.  May be there is a flaw there.  Or, the UEFI BIOS can be exploit or not.

So, the last word is that it is possible to infect a BIOS in Linux system.

Samiux

---

### Post by uRock on 2012-07-08
> **samiux said:**
> So, the last word is that it is possible to infect a BIOS in Linux system.

How?

---

### Post by samiux on 2012-07-08
> **uRock said:**
> How?

Old BIOS is written in assembly language.  The UEFI may be in C (but I don't know).

Just flash the malware to the flash ROM and bypassed the protection protocol if any.

In the theory, it is possible.

Samiux

---

### Post by Hungry Man on 2012-07-08
It's entirely possible and it's happened before. It's just an incredibly unreliable attack for multiple reasons.

1) You have to attack very specific hardware down to the exact model often times.

2) You need admin rights to do this

3) Often times if the user has an older or newer BIOS version (software) the attack will fail

---

