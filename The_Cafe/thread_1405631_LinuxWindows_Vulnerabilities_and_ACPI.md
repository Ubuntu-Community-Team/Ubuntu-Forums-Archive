---
title: "Linux/Windows Vulnerabilities and ACPI"
date: 2010-02-12
forum: The Cafe
---

### Post by neu5eeCh on 2010-02-12
After starting the Win8 thread last night (only to have it shut down). Some of the back & forth was, to me, genuinely informative.

Disclaimer: Though I was accused of it, I'm not a Microsoft basher (I dislike Apple more) and I'm not a mindless Linux booster.

One contributor commented that Ubuntu has 400 vulnerabilities compared to Windows 20. That was news to me, since I had always read that Linux was a more stable (if less easily configured) and more secure OS. So, I think I found out where the vulnerabilities assertion came from:

[Windows 7]("http://secunia.com/advisories/product/27467/?task=statistics_2009") 
[Ubuntu 9.04]("http://secunia.com/advisories/product/21851/")
[Ubuntu 9.10]("http://secunia.com/advisories/product/28063/")

What I found interesting, vis-a-vis 9.10, was that while there were more vulnerabilities, Secunia states:

There are no unpatched Secunia advisories affecting this product, when  all vendor patches are applied..                                 

As opposed to Windows:

The most severe unpatched Secunia advisory affecting Microsoft Windows  7, with all vendor patches applied, is rated Less critical 

Which implies that Windows is, in fact, less secure than Linux when all patches are applied. This is what I've read about Linux OS. (And it bears repeating, I'm not interested in defending Linux or bashing Windows, just interested in the facts. I use Linux because its free, it works (with some work), and I like it.

I was also interested to read about Linux's poor ACPI implementation and found the [following]("http://www.osnews.com/thread?230516"):
[INDENT]The reason most ACPI-implementations are horrible and don't work well  with non-MS OS's is that Microsoft has been so friendly to create an  easy DSDT compiler (easy because it doesn't complain about bugs &  warnings, perfect for lazy programmers).  

The DSDT (Differentiated System Description Table) is like the index of  the a BIOS's ACPI functions. Now it so happens to be that MS's DSDT  compiler generates non-100%-ACPI compliant & bugged code which only  Windows can understand and work with. 

Intel has a free DSDT compiler that does work 100% compliant, why are  the OEM manufacturers so bloody stupid,you get one for free, why buy  MS's? 

One can load a custom fixed DSDT table into the kernel at boot time (see  [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php))  for more info. They have several fixed DSDT's available as well and  there's plenty of documentation to learn the AML language for fixing  your own table. 
I got my laptop with ACPI working that way [IMG]http://www.osnews.com/images/emo/smile.gif[/IMG]

[/INDENT]Related, I also found this:

[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

So.... FYI.

---

### Post by JT9161 on 2010-02-12
Number of known exploits itself means nothing, it's a matter of how many are patched upon discovery and reporting.

---

### Post by Mustard on 2010-02-13
I'm glad you took the time to follow up on the statements made in the closed thread. It's interesting to see your results.

---

### Post by gsmanners on 2010-02-13
You can learn a lot about ACPI, if you know where to look:

[http://www.groklaw.net/articlebasic.php?story=2010011422570951](http://www.groklaw.net/articlebasic.php?story=2010011422570951)

---

### Post by murderslastcrow on 2010-02-13
Isn't it more likely that there are security holes in Windows that aren't discovered due to Windows being closed source?

---

