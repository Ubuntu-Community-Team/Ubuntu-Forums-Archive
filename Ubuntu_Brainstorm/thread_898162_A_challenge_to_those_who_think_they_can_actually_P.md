---
title: "A challenge to those who think they can actually Program."
date: 2008-08-22
forum: Ubuntu Brainstorm
---

### Post by cooke77 on 2008-08-22
Hi, I'm a 'newbiee'(Noob or whatever) to Linux (any 'flavor' you care to think of).

Here's my 'idea'...

If a "Live CD" can Access your 'existing OS' (whatever it may be!).....with comparitive ease!.........and, do no harm to it.... is there a very brainy Programmer out there who can 'compile' this same 'KERNEL'.......into a fully operating Linux OS?

To achieve such an 'undertaking'.......would, in effect, 'eliminate' the use of "Virual Reality OS's"! (Like VMware, Wine, etc.)
 
I'm no programmer, so who's up for the 'Challenge'?

---

### Post by cardinals_fan on 2008-08-22
> **cooke77 said:**
> Hi, I'm a 'newbiee'(Noob or whatever) to Linux (any 'flavor' you care to think of).

Here's my 'idea'...

If a "Live CD" can Access your 'existing OS' (whatever it may be!).....with comparitive ease!.........and, do no harm to it.... is there a very brainy Programmer out there who can 'compile' this same 'KERNEL'.......into a fully operating Linux OS?

To achieve such an 'undertaking'.......would, in effect, 'eliminate' the use of "Virual Reality OS's"! (Like VMware, Wine, etc.)
 
I'm no programmer, so who's up for the 'Challenge'?
What you're asking for is impossible.  You cannot run more than one kernel at once without virtualization.

---

### Post by damis648 on 2008-08-22
> **cooke77 said:**
> Hi, I'm a 'newbiee'(Noob or whatever) to Linux (any 'flavor' you care to think of).

Here's my 'idea'...

If a "Live CD" can Access your 'existing OS' (whatever it may be!).....with comparitive ease!.........and, do no harm to it.... is there a very brainy Programmer out there who can 'compile' this same 'KERNEL'.......into a fully operating Linux OS?

To achieve such an 'undertaking'.......would, in effect, 'eliminate' the use of "Virual Reality OS's"! (Like VMware, Wine, etc.)
 
I'm no programmer, so who's up for the 'Challenge'?

It can access the files, but not ever start the OS without virtualization. I repeat what was above, that it not possible.

---

### Post by xeth_delta on 2008-08-23
> **cooke77 said:**
> Hi, I'm a 'newbiee'(Noob or whatever) to Linux (any 'flavor' you care to think of).

Here's my 'idea'...

If a "Live CD" can Access your 'existing OS' (whatever it may be!).....with comparitive ease!.........and, do no harm to it.... is there a very brainy Programmer out there who can 'compile' this same 'KERNEL'.......into a fully operating Linux OS?

To achieve such an 'undertaking'.......would, in effect, 'eliminate' the use of "Virual Reality OS's"! (Like VMware, Wine, etc.)
 
I'm no programmer, so who's up for the 'Challenge'?

I am not very sure I understand what you mean. The environment you run from the CD is basicly accessing the file systems where the files of the users or OSs are located, AFAIK, not running them. The kernel that is used on the CD is a regular Linux kernel that has to have access to the CPU. I am not sure it is possible to have two kernels have simultaneous access to the same CPU and memory.

---

