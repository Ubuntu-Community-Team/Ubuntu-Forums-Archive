---
title: "Serious Security flaw in Linux kernel"
date: 2010-09-18
forum: The Cafe
---

### Post by jerenept on 2010-09-18
> The Linux kernel has been purged of a bug that gave root access to untrusted users &#8211; again.

The vulnerability in a component of the operating system that translates values from 64 bits to 32 bits (and vice versa) was fixed once before &#8211; in 2007 with the release of version 2.6.22.7. But several months later, developers inadvertently rolled back the change, once again leaving the OS open to attacks that allow unprivileged users to gain full root access.


[http://www.h-online.com/open/news/item/Hole-in-Linux-kernel-provides-root-rights-1081317.html]("http://www.h-online.com/open/news/item/Hole-in-Linux-kernel-provides-root-rights-1081317.html")
[http://www.theregister.co.uk/2010/09/15/linux_kernel_regression_bug/]("http://www.theregister.co.uk/2010/09/15/linux_kernel_regression_bug/")

---

### Post by kamaboko on 2010-09-18
This is simply impossible.  Doesn't everyone know that Linux is absolute perfection?  I am joking of course.  Now if this were a post about Microsoft, it would surely be followed with nothing but scathing remarks about the company, its approach to software, etc.  But...given that this is a Linux issue it will be treated with kid gloves and receive praise and glory.

---

### Post by CharlesA on 2010-09-18
I wonder if that was the reason for the kernel upgrade yesterday..

---

### Post by Bachstelze on 2010-09-18
That's bound to happen when the piece (more like a mountain actually) of code you're working on is such a mess. Still quite funny, though. :p

---

### Post by Frogs Hair on 2010-09-18
I had two kernel updates yesterday from proposed updates , so I wonder if it's fixed ?

---

### Post by CharlesA on 2010-09-18
> **Frogs Hair said:**
> I had two kernel updates yesterday from proposed updates , so I wonder if it's fixed ?

Could be. Neither article mentioned what kernel they were running and didn't link to any launchpad bug reports.

---

### Post by ubunterooster on 2010-09-18
And _now_ Linux is perfect...again :rolleye:

---

### Post by mr-woof on 2010-09-18
if it is the kernel headers that I'm upgrading now, well done to the devs for getting the fix out :)

---

### Post by Shining Arcanine on 2010-09-18
> **kamaboko said:**
> This is simply impossible.  Doesn't everyone know that Linux is absolute perfection?  I am joking of course.  Now if this were a post about Microsoft, it would surely be followed with nothing but scathing remarks about the company, its approach to software, etc.  But...given that this is a Linux issue it will be treated with kid gloves and receive praise and glory.

It is an open secret in computer science that virtually all OS kernels are imperfect. The only exception to that is possibly the seL4 kernel:

[http://ertos.nicta.com.au/research/sel4/](http://ertos.nicta.com.au/research/sel4/)

---

### Post by murderslastcrow on 2010-09-18
The point isn't to be invincible, but to be secure. Those are two different things.

The simple fact is that a computer can't do anything the code doesn't tell it to do. It's not like voodoo or magic that viruses work on Windows and don't on Linux, because of some market share B.S. It's reality, and the security is better than you can find anywhere else.

So really, I think we should be realistic and assert the security of our software packages. Then again, FreeBSD might be more secure than Linux at a core level, I'm not entirely certain. But I do know why Linux is secure. That's just it, you need to research things, rather than just blurt generalizations.

So yeah, Linux isn't perfect, just extremely good, and in security kills OS X and Windows. What product is perfect, for that matter?

---

### Post by Frak on 2010-09-19
> **murderslastcrow said:**
> The point isn't to be invincible, but to be secure. Those are two different things.

The simple fact is that a computer can't do anything the code doesn't tell it to do. It's not like voodoo or magic that viruses work on Windows and don't on Linux, because of some market share B.S. It's reality, and the security is better than you can find anywhere else.

So really, I think we should be realistic and assert the security of our software packages. Then again, FreeBSD might be more secure than Linux at a core level, I'm not entirely certain. But I do know why Linux is secure. That's just it, you need to research things, rather than just blurt generalizations.

So yeah, Linux isn't perfect, just extremely good, and in security kills OS X and Windows. What product is perfect, for that matter?
Nope.

---

### Post by Ctrl-Alt-F1 on 2010-09-19
> **Frak said:**
> Nope.

Agreed.

---

### Post by adn258 on 2010-09-23
Also as the article states it says you would basically have to be a user on there already which is true it does pose a threat to government agencies etc. but not really to home users where one person has physical access to the computer lol another sign of the power of the permission system built into linux.  Even when most hackers win they lose.

---

