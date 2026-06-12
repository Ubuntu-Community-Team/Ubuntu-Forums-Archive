---
title: "evil maid scenario"
date: 2011-08-27
forum: Security
---

### Post by webdorq on 2011-08-27
Is there a log file entry when someone accesses my system with a live cd?

Which log?
What am I looking for?
Which log besides syslog shows shutdown/login times?
How do I create a duplicate log somewhere else and compare for tampering?
Am I too paranoid?
Is this too many questions?

---

### Post by snip3r8 on 2011-08-27
What do these questions have in common with your topic?

---

### Post by jwbrase on 2011-08-27
Unless there's some way to set your BIOS up to record what device it boots from on each boot, no. Physical access is root access.

Given that you're asking whether you're being too paranoid, you likely are. Most places that would need that level of security wouldn't hire you to run their IT security unless you were security-savvy enough to know the level of paranoia required (such places probably wouldn't be using home-desktop grade hardware and software either), and a home computer is unlikely to be storing anything requiring that level of paranoia, unless you know that someone living with you, or a frequent visitor, is both tech savvy enough and of rotten enough character to try to break in to the machine and make use of your personal information. (Even then, the best course of action is to find a new roommate/friend). If you trust everybody that is likely to be left alone in a room with the machine for any significant length of time, then there's no need to take measures against things like LiveCD boots. Sure, someone you don't even know can always break in and steal the machine, but once they've stolen it, they have all the time they want to crack whatever security you have in place.

---

### Post by jwbrase on 2011-08-27
> **snip3r8 said:**
> What do these questions have in common with your topic?

I think he's using "evil maid" as a catchphrase for "untrusted persons who might be left in a room with my computer for a significant amount of time". Unless he actually has a maid, I wouldn't expect this to crop up in a home situation much.

@OP: What brings the topic up? Are you just generally paranoid, or is there a specific person you're thinking of as the "evil maid" in this scenario?

---

### Post by scorp123 on 2011-08-27
> **webdorq said:**
>  Am I too paranoid? Use Thin Clients. No local disk, no local OS = no worries. The required server infrastructure can be safely locked away inside a bunker ...

That's how some Swiss banks around here do it.

---

### Post by snip3r8 on 2011-08-28
Its actually quite a funny thread title...my maid wont go near my pc's and other electronics because all the cables "scare" her

---

### Post by cprofitt on 2011-08-29
> **snip3r8 said:**
> Its actually quite a funny thread title...my maid wont go near my pc's and other electronics because all the cables "scare" her

It is actually a fairly standard way to describe an information security situation.

[http://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html](http://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html)

---

### Post by tgm4883 on 2011-08-30
As mentioned before, it's a pretty common name for a certain type of attack.

From Wikipedia [http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)
> Bootkits
A kernel-mode rootkit variant called a bootkit is used predominantly to attack full disk encryption systems, for example as in the **"Evil Maid Attack"**, in which a bootkit replaces the legitimate boot loader with one controlled by an attacker; typically the malware loader persists through the transition to protected mode when the kernel has loaded.[35][36][37][38] For example, the "Stoned Bootkit" subverts the system by using a compromised boot loader to intercept encryption keys and passwords.[39] More recently, the Alureon rootkit has successfully subverted the requirement for 64-bit kernel-mode driver signing in Windows 7 by modifying the master boot record.[40]
The only known defenses against bootkit attacks are the prevention of unauthorized physical access to the system—a problem for portable computers—or the use of a Trusted Platform Module configured to protect the boot path.[41

---

