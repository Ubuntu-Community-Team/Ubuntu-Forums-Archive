---
title: "hardened image of ubuntu?"
date: 2019-08-24
forum: Security
---

### Post by sniper8752 on 2019-08-24
I recently ran a oscap scan of ubuntu 16.04 server, and noticed there were a good amount of findings (like CAT I and II's).  Are there any hardened images out there, of Ubuntu?

---

### Post by sniper8752 on 2019-09-19
*bump*

---

### Post by uRock on 2019-09-19
Not that I know of. You can do it yourself though. There's plenty of How-Tos on the subject. Here's one; [https://www.nuharborsecurity.com/ubuntu-server-hardening-guide-2/](https://www.nuharborsecurity.com/ubuntu-server-hardening-guide-2/)
There's also loads of documentation in the Security subforum stickies.

---

### Post by TheFu on 2019-09-20
> **sniper8752 said:**
> I recently ran a oscap scan of ubuntu 16.04 server, and noticed there were a good amount of findings (like CAT I and II's).  Are there any hardened images out there, of Ubuntu?

Many of the claimed "best practices" aren't for Ubuntu or Debian.  Slight differences in how permissions are setup makes a huge difference, as does the normal method of software deployment to the system.  20 yrs ago, I was trying to "harden" my servers and found that the tips had been crafted for different OSes and actually broke the distro I was running then.  Check out Bob Toxen's *Real World Linux Security* book.

For people who need to follow some govt standard, I'd suggest sticking with the OS those standards were written especially for.  CentOS/RHEL have lots of tools for that and lots of scanners to ensure SELinux is enabled and the 200+ other things validated.

For RHEL-based distros, there are STIGs.  [https://public.cyber.mil/?s=STIG](https://public.cyber.mil/?s=STIG)  Looks like there might be Ubuntu-specific versions now.

---

### Post by CharlesA on 2019-09-20
> **TheFu said:**
> Many of the claimed "best practices" aren't for Ubuntu or Debian.  Slight differences in how permissions are setup makes a huge difference, as does the normal method of software deployment to the system.  20 yrs ago, I was trying to "harden" my servers and found that the tips had been crafted for different OSes and actually broke the distro I was running then.  Check out Bob Toxen's *Real World Linux Security* book.

For people who need to follow some govt standard, I'd suggest sticking with the OS those standards were written especially for.  CentOS/RHEL have lots of tools for that and lots of scanners to ensure SELinux is enabled and the 200+ other things validated.

I definitely agree with you.

There are even things like [CIS Benchmarks]("https://www.cisecurity.org/cis-benchmarks/") for hardening, but they aren't a one-and-done deal. They need to be tailored to your environment.

---

### Post by sniper8752 on 2019-10-08
Thanks for recommending this book! I see it's from 2002 though... anything a little more recent? I'm sure most of it still applies.

---

### Post by TheFu on 2019-10-08
> **sniper8752 said:**
> Thanks for recommending this book! I see it's from 2002 though... anything a little more recent? I'm sure most of it still applies.

If you seek a checklist and commands, nothing.
If you seek knowledge so you can create a modern checklist and commands for your specific installations, then the core ideas in that book will serve you well.  And Bob is a really nice guy too.

O'Reilly and No Starch Press usually have excellent books, but they are out of date before the ink is dry.  I still use my Unix System Security books from the mid-1990s as references for "ideas."  They aren't cookbooks, however.

---

