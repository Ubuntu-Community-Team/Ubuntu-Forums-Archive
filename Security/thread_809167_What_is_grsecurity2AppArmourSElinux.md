---
title: "What is grsecurity2/AppArmour/SElinux?"
date: 2008-05-27
forum: Security
---

### Post by ShinHadoken on 2008-05-27
I think I have security down-pat, but I'm not sure about grsecurity2/AppArmor/SElinux. I mean, I know what they all do, but I have two main questions:

1. If I install grsecurity2, do I need to enable AppArmor/SElinux?

2. Do I need to run *both AppArmor and SElinux* or just one?

Also, what about buffer overrun protection? I hear Ubuntu has its own software enabled by default, but I'v also heard that I need more protection than that. Any answers?

Thanks,

SH

---

### Post by ShinHadoken on 2008-05-27
bump

---

### Post by ShodanjoDM on 2008-05-27
> **ShinHadoken said:**
> I think I have security down-pat, but I'm not sure about grsecurity2/AppArmor/SElinux. I mean, I know what they all do, but I have two main questions:

1. If I install grsecurity2, do I need to enable AppArmor/SElinux?

2. Do I need to run *both AppArmor and SElinux* or just one?

Also, what about buffer overrun protection? I hear Ubuntu has its own software enabled by default, but I'v also heard that I need more protection than that. Any answers?

Thanks,

SH

This [article]("http://www.ibm.com/developerworks/linux/library/l-selinux/?S_TACT=105AGX03&S_CMP=ART") seems able to answer some of your questions, especially regarding SE Linux.

> Linux® has been described as one of the most secure operating systems available, but the National Security Agency (NSA) has taken Linux to the next level with the introduction of Security-Enhanced Linux (SELinux). SELinux takes the existing GNU/Linux operating system and extends it with kernel and user-space modifications to make it bullet-proof. _If you're running a 2.6 kernel today, you might be surprised to know that you're using SELinux right now!_ This article explores the ideas behind SELinux and how it's implemented.

Re: AppArmor, somebody please correct me if I'm wrong, but it's already installed and running on your installation (iirc it was first implemented in Ubuntu 7.10 along with its Linux 2.6.22 (?) kernel).

---

### Post by MythosLegend on 2008-05-27
1. I'm not sure if you can use both. There's a another thread from a forum staff member trying to use both Grsecurity and apparmor. It seems difficult.
[http://ubuntuforums.org/showthread.php?t=809296](http://ubuntuforums.org/showthread.php?t=809296)

2. Apparmor is installed by default for Ubuntu (I think its 7.10 and later).
You should use one. Apparmor is supposedly easier to use than SElinux.

---

### Post by Arthur Archnix on 2008-05-27
I remove apparmor from my Ubuntu install. I've got separate partitions with appropriate permissions, I'm the only user of the laptop, and I've got no open services. No services period. For me, even policy kit is overkill. But that's too tightly integrated to unwind and its not like it has a performance cost.

Course, if you've got a server or even a desktop that you ssh into then I'd defintiely be running at least one. Probably app armor, though I'm not sure how many profiles are enabled by default. More than in Gutsy surely, but one is greater than none so i'm not sure how much that's saying.

Not expert advice. Just my own two cents. Probably worth one.

---

### Post by chrisccoulson on 2008-05-27
By default, Apparmor only protects cupsd, but it is easy to configure in order to protect other processes.

I sandbox all network daemons with Apparmor, and I also sandbox Firefox, Deluge and Pidgin to make sure that they can only ever write to the desktop or a dedicated download folder

---

### Post by ShinHadoken on 2008-05-29
So, here's what I'm getting:
 
I should configure Apparmor, and forget about SElinux.
 
Ok, but what about grsecurity? 
 
**1.** **Should I install it? If so, how?**
**2. If I do install it, should I still run AppArmor?**
**3. How do I configure grsecurity?**
**4. If I shouldn't install grsecurity, what do I do about memory overrun prevention (such as PaX)?**

---

