---
title: "How do you tell if a computer has TPM?"
date: 2006-01-13
forum: The Cafe
---

### Post by vayu on 2006-01-13
I want to buy a new computer, but I don't want TPM.  I'm thinking I want a dual core Pentium M laptop and an AMD X2 desktop.  Are such new designs bound to have a TPM chip installed?

---

### Post by mstlyevil on 2006-01-13
[QUOTE=vayu]I want to buy a new computer, but I don't want TPM.  I'm thinking I want a dual core Pentium M laptop and an AMD X2 desktop.  Are such new designs bound to have a TPM chip installed?[/QUOTE]

Probally not with Windows XP. TPM is something that is fully supported in Windows Vista and OSX. TPM is useless under Linux so a TPM chip will probally have no effect on Ubuntu users.

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=vayu]I want to buy a new computer, but I don't want TPM.  I'm thinking I want a dual core Pentium M laptop and an AMD X2 desktop.  Are such new designs bound to have a TPM chip installed?[/QUOTE]

The X2 desktop won't. I checked before I bought mine.

No promises on the Intel- they are the leader in that area.

---

### Post by vayu on 2006-01-13
[QUOTE=poofyhairguy]The X2 desktop won't. I checked before I bought mine.[/QUOTE]

How did you check?


Off topic, do you have to sacrifice plugins like flash, quicktime, wmv and pdf viewers with the X2?

---

### Post by mstlyevil on 2006-01-13
[QUOTE=vayu]Off topic, do you have to sacrifice plugins like flash, quicktime, wmv and pdf viewers with the X2?[/QUOTE]

No, not at all. The X2 is A AMD Athlon 64 dual core processor. It will run any program or operating system that Intel will run because it is a full X86 compliant chip.

---

### Post by sudoMakeTea on 2009-06-23
> **mstlyevil said:**
> Probally not with Windows XP. TPM is something that is fully supported in Windows Vista and OSX. TPM is useless under Linux so a TPM chip will probally have no effect on Ubuntu users.

This is an old thread but I have to comment as this thread shows up as one of the first few results on google. Your statement is (and was 3 years ago) patently false.  The TPM is not fully supported under XP, Vista or OSX.  However, there are open source projects that allow you to leverage the TPM's capabilities on Linux.

---

### Post by DouglasAWh on 2009-10-08
> **vayu said:**
> How did you check?


This question seems to have gone un-answered and I'd like to know. :)

---

### Post by coldReactive on 2009-10-08
The Wikipedia Article might help: [http://en.wikipedia.org/wiki/Trusted_Platform_Module](http://en.wikipedia.org/wiki/Trusted_Platform_Module)

---

### Post by Bachstelze on 2009-10-08
> **mstlyevil said:**
> TPM is useless under Linux.

Where does that come from?

---

### Post by Xbehave on 2009-10-08
> **Bachstelze said:**
> Where does that come from?
TPM is to do with DRM and is pretty useless under linux (although you might be able to do some nice rootkit checks using it, but if somebody has a rootkit on your system them can just fudge the results so tbh it is pretty useless!)

---

### Post by Bachstelze on 2009-10-08
> **Xbehave said:**
> TPM is to do with DRM

No. DRM is *one of the possible applications* of TPM, just like it is one of the possible applications of encryption. Is it the only one? No. Does that make encryption useless on Linux systems? Definitely not. Same goes for TPM.

---

### Post by Xbehave on 2009-10-08
> **Bachstelze said:**
> No. DRM is *one of the possible applications* of TPM, just like it is one of the possible applications of encryption. Is it the only one? No. Does that make encryption useless on Linux systems? Definitely not. Same goes for TPM.
OK, give one use of it on a linux system?
You can sign stuff, but unless you sign and check 
1) your MBR
2) your bootloader
3) your kernel
it's not going to be any use!
AFAIK, no bios checks the MBR, no bios checks the bootloader and its hard to fit a keycheck algo in the MBR, no widespread bootloader (GRUB.GRUB2,LILO) can read a TPM chip or check the sig on the kernel. So i say again a TPM chip is next to usless under linux, sure you can use it but there is no reason to trust it above a kernel that already offers all of the TPMs features.

---

### Post by Warpnow on 2009-10-08
...I don't think a dual core pentium M exists...

---

### Post by caxap on 2011-10-19
Can I use TPM to encrypt data on my HDD?
Which software can I use?

---

### Post by sffvba[e0rt on 2011-10-19
Back to sleep thread...


404

---

