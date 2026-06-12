---
title: "Linux kernel 3.0 will be released"
date: 2011-07-22
forum: The Cafe
---

### Post by Harry33 on 2011-07-22
The release version of kernel 3.0 is expected today.
Also, kernel 3.1 merge window will open soon.

See here Linus Torvalds notes on the subject:
[https://lkml.org/lkml/2011/7/20/371](https://lkml.org/lkml/2011/7/20/371)

---

### Post by Sef on 2011-07-22
Moved to Community Cafe.

---

### Post by foxmulder881 on 2011-07-22
Yeah it's probably time to update from my RC1 build. :P

---

### Post by JASONFUSARO on 2011-07-22
jason@UbuntuStudio64bit:~$ uname -a
Linux UbuntuStudio64bit 2.6.39.3 #2 SMP Thu Jul 21 22:31:33 EDT 2011 x86_64 x86_64 x86_64 GNU/Linux


Just compiled my first kernel was 2.6.38-10-generic.

I activated core 2 and got rid of a few other things.
bumping up to 3.0 will be the same process I just went through shouldn't it

---

### Post by Dustin2128 on 2011-07-22
I'll upgrade when arch releases its version. Currently running 2.6.39. Aside- why didn't they call it linux 2.8? I pray this isn't the insidious beginning of chrome syndrome... :(

---

### Post by Legendary_Bibo on 2011-07-22
> **Dustin2128 said:**
> I'll upgrade when arch releases its version. Currently running 2.6.39. Aside- why didn't they call it linux 2.8? I pray this isn't the insidious beginning of chrome syndrome... :(

Linus wants to change the numbering system. So rather than have something like 2.6.39 it would stick to only one decimal place. 3.1, 3.2, 3.3, etc.

---

### Post by kaldor on 2011-07-22
> **Legendary_Bibo said:**
> Linus wants to change the numbering system. So rather than have something like 2.6.39 it would stick to only one decimal place. 3.1, 3.2, 3.3, etc.

He also complained about some vendors offering "Linux 2.6 support" but using a very old kernel. For those that do not know, Linux 2.6.0 was released around 2003. The numbering became way too high.

---

### Post by Dustin2128 on 2011-07-22
> **kaldor said:**
> He also complained about some vendors offering "Linux 2.6 support" but using a very old kernel. For those that do not know, Linux 2.6.0 was released around 2003. The numbering became way too high.
I know, and I agree. I'm just wondering why he didn't go for 2.8? About chrome syndrome, all I'm saying is that I really hope that we don't have kernel 49 by 2015.

---

### Post by el_koraco on 2011-07-22
> **Dustin2128 said:**
> I know, and I agree. I'm just wondering why he didn't go for 2.8? About chrome syndrome, all I'm saying is that I really hope that we don't have kernel 49 by 2015.

The voice in his head told him so. I think it's kinda symbolic - with the kernel entering its third decade, nr 3 is kinda appropriate.

---

### Post by JASONFUSARO on 2011-07-22
> **JASONFUSARO said:**
> jason@UbuntuStudio64bit:~$ uname -a
Linux UbuntuStudio64bit 2.6.39.3 #2 SMP Thu Jul 21 22:31:33 EDT 2011 x86_64 x86_64 x86_64 GNU/Linux


Just compiled my first kernel was 2.6.38-10-generic.

I activated core 2 and got rid of a few other things.
bumping up to 3.0 will be the same process I just went through shouldn't it



Yes I guess it is the same process

jason@UbuntuStudio64bit:~$ uname -a
Linux UbuntuStudio64bit 3.0.0 #1 SMP Fri Jul 22 03:05:50 EDT 2011 x86_64 x86_64 x86_64 GNU/Linux
jason@UbuntuStudio64bit:~$




If you look at the screenshot of system info it displays 3.0.0

---

### Post by NightwishFan on 2011-07-22
I am compiling 2.6.32 right now. You guys are too new for my blood. I think 3.0 is already in Debian Experimental so I might install it in virtualbox.

---

### Post by Bandit on 2011-07-22
> **Dustin2128 said:**
> I know, and I agree. I'm just wondering why he didn't go for 2.8? About chrome syndrome, all I'm saying is that I really hope that we don't have kernel 49 by 2015.

I agree with you. 2.8 would have made much better sense. Even if Linus didnt like the current numbering system, going from 2.6 to 3.0 represents a major release with new features or at least a huge bug and performance overhaul. Only think I remember being mentioned was a kernel clean up, I just dont feel that makes a 3.0 release.

---

### Post by 3Miro on 2011-07-22
From what I understand there is nothing exciting about 3.0, it is just a new number, but it comes with the same features as 2.6.40 would. Nobody got excited about 2.6.39 or 2.6.38, there is no reason to be excited about 3.0.

Basically 3.0 is a big non-event.

---

### Post by Harry33 on 2011-07-22
Here is the release announcement:

[https://lkml.org/lkml/2011/7/21/455](https://lkml.org/lkml/2011/7/21/455)

---

