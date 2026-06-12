---
title: "Am I running 64 bit ubuntu?"
date: 2007-08-12
forum: The Cafe
---

### Post by jgrabham on 2007-08-12
Ok this install was done from a DVD, and on IP chicken it says

 	Name Address: host-84-13-5-39.opaltelecom.net.5.13.84.in-addr.arpa
	Remote Port: 40184
	Browser: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

i686?  I know I have a 64 bit CPU, but i always assumed I was running 32bit :s

---

### Post by Nekiruhs on 2007-08-12
> **jgrabham said:**
> Ok this install was done from a DVD, and on IP chicken it says

 	Name Address: host-84-13-5-39.opaltelecom.net.5.13.84.in-addr.arpa
	Remote Port: 40184
	Browser: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

i686?  I know I have a 64 bit CPU, but i always assumed I was running 32bit :s
You are using 32 bit. i686 is your processor type. i386 is another type.

---

### Post by jgrabham on 2007-08-12
> **Nekiruhs said:**
> You are using 32 bit. i686 is your processor type. i386 is another type.

Oh good, I started feeling a bit stupid there...

EDIT: but how do you know??

---

### Post by lepz on 2007-08-12
Bet it was <snip /> you really tried. ;)

---

### Post by jgrabham on 2007-08-12
> **lepz said:**
> Bet it was <snip /> you really tried. ;)

WOW, didnt know that existed - thanks mate (kidding)

---

### Post by Ultra Magnus on 2007-08-12
Well, I'm pretty confused aswell - I have a 64 bit cpu, 32 bit ubuntu but when I type gcc -dumpmachine it says i464 - Whatever that is

---

### Post by Nekiruhs on 2007-08-12
> **Ultra Magnus said:**
> Well, I'm pretty confused aswell - I have a 64 bit cpu, 32 bit ubuntu but when I type gcc -dumpmachine it says i464 - Whatever that is
Again, its just your processor architecture.There are a bunch more statistics to processors that just 32 or 64 bit.

---

### Post by yatt on 2007-08-12
If it follows the pattern ix86, where x is an integer between 3 and 6, then it is 32bit (the i stands for Intel). 64bit is usually x86-64, x64, or AMD64.

---

### Post by Darkhack on 2007-08-12
Don't you just love how these guys name their processors?  It's almost as though they enjoy confusing us.

The first set below is your standard Intel and AMD 32 bit processors which can be extended into sub-architectures with new features and performance improvements.  Most decent computers will be i686 if you have a 32 bit CPU.  

**_x86 / x86-32 / IA32_**
i386
i486
i586 - Pentium / K5 / K6
i686 - Pentium II / Pentium III
Pentium 4 / Athlon / Athlon XP / Pentium D
Intel Core

The second set are your Athlon64 and Core 2 processors.  EM64T is Intel's name for Extended Memory 64 bit Technology which is fancy talk that simply means they are Intel processors that are compatible with AMD's 64 bit extensions.  They are compatible with 32 bit and 64 bit instructions although you must be running a 64 bit OS to run 64 and 32 bit software.  It will not work vice-versa (64 bit on 32 bit OS).  These are also called x64 CPUs, but I personally hate that term because x86 is the name of the architecture and such a name would imply that x32 is the 32 bit version of it, which it is not, but some stupid idiot decided to call the new architecture x64 anyway and it spread on internet forums.

**_x86-64 / AMD64 / EM64T / x64_**
Athlon64 (X2/FX)
Opteron
Turion 64 (X2)
Intel Core 2

This is the confusing part.  As seen above, x86, x86-32, and IA32 are all different names for the same thing, although most people will only call Intel processors IA32 even though it is the same thing while the other two terms are generic, non brand specific names.  In the 64 bit world however, you have x86-64 for the generic term, AMD64 for AMD's processors and EM64T for Intel's processors.  However, unlike the above naming convention, IA64 is NOT part of this group.  It is completely separate.  This is Intel's name for the Itanium processors which are 64 bit only and NOT compatible with 32 bit software.  These are typically only used on servers because most desktop users still run at least some 32 bit applications.

**_IA64_**
Itanium
Itanium 2

---

### Post by mk4umha on 2008-02-09
How do I confirm that I did install 64 bit Ubuntu? Is there a command I can run to check? thanks.

---

### Post by akiratheoni on 2008-02-10
You can try:
```
uname -a
```

---

### Post by helliewm on 2008-02-10
or go to [www.getdeb.net](www.getdeb.net) and try downloading a 64 bit piece of software. It will come back as wrong architecture if its not 64 bit just makesure its not an All Deb these cover 32 bit and 64 bit. It will say All Deb when you download it.

Helen

---

