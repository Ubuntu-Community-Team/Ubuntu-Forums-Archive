---
title: "Non-Executable Memory bit."
date: 2012-08-23
forum: Security
---

### Post by kleenex on 2012-08-23
Hi. I have a question about the Non-eXecute (NX) feature. I am using 32 bit system with 1 GB of RAM memory and non-PAE generic kernel. In [COLOR=SeaGreen]kern.log[/COLOR] and [COLOR=SeaGreen]syslog[/COLOR] files I see something like this; ```
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
``` According to wiki page and [_Security Features_]("https://wiki.ubuntu.com/Security/Features#nx") (also it is interesting [_x86, cpu; Clear XD_DISABLED flag on Intel to regain NX_]("https://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ae84739c27b6b3725993202fe02ff35ab86468e1")) if neither (info) are seen, I do not have any NX protections enabled. But in my case second info from [COLOR=SeaGreen]kern.log[/COLOR] file containing **approximated by x86 segement limits** is very similar to that from Ubuntu Wiki. In my log file, there is also information, that protection cannot be enabled in hardware (see above). Of course my computer supports NX (and others) technologies. ```
[COLOR=Blue]$[/COLOR] [COLOR=Green]egrep --color '(nx|pae)' /proc/cpuinfo[/COLOR]
flags        :  [COLOR=Red]pae nx[/COLOR] 
``` So, does my system is secured from arbitrary code execution, or do I need to install the PAE kernel? But what about 1GB of RAM memory? It is enough? Informations from the wiki and from the [COLOR=SeaGreen]syslog[/COLOR] file are confusing me. Wiki also contains this information: *Starting in Ubuntu 9.10, this protection is partially emulated for  processors lacking NX when running _on a 32bit kernel_ (built with or  _without PAE_). *So?

---

### Post by Hungry Man on 2012-08-23
Maybe try running this:
[http://www.trapkit.de/tools/checksec.html](http://www.trapkit.de/tools/checksec.html)

and see if it says you're using NX?

---

### Post by kleenex on 2012-08-23
Hi **Hungry Man**. I know this **checksec** script, but to be honest I do not like to run the scripts from unfamiliar sources. Of course, I can browse the code from the point of "bad code", but I'm not good at it. There is no other opportunity to check if my computer supporting NX bit? For now I would like to refrain from using this code. Yes, I know that - too paranoid. Maybe... :- )

---

### Post by samiux on 2012-08-25
> **kleenex said:**
> Hi. I have a question about the Non-eXecute (NX) feature. I am using 32 bit system with 1 GB of RAM memory and non-PAE generic kernel. In [COLOR=SeaGreen]kern.log[/COLOR] and [COLOR=SeaGreen]syslog[/COLOR] files I see something like this; ```
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
``` According to wiki page and [_Security Features_]("https://wiki.ubuntu.com/Security/Features#nx") (also it is interesting [_x86, cpu; Clear XD_DISABLED flag on Intel to regain NX_]("https://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ae84739c27b6b3725993202fe02ff35ab86468e1")) if neither (info) are seen, I do not have any NX protections enabled. But in my case second info from [COLOR=SeaGreen]kern.log[/COLOR] file containing **approximated by x86 segement limits** is very similar to that from Ubuntu Wiki. In my log file, there is also information, that protection cannot be enabled in hardware (see above). Of course my computer supports NX (and others) technologies. ```
[COLOR=Blue]$[/COLOR] [COLOR=Green]egrep --color '(nx|pae)' /proc/cpuinfo[/COLOR]
flags        :  [COLOR=Red]pae nx[/COLOR] 
``` So, does my system is secured from arbitrary code execution, or do I need to install the PAE kernel? But what about 1GB of RAM memory? It is enough? Informations from the wiki and from the [COLOR=SeaGreen]syslog[/COLOR] file are confusing me. Wiki also contains this information: *Starting in Ubuntu 9.10, this protection is partially emulated for  processors lacking NX when running _on a 32bit kernel_ (built with or  _without PAE_). *So?

NX can be bypassed by a technique namely ROP and ret2libc.

Samiux

---

### Post by rookcifer on 2012-08-25
> **samiux said:**
> NX can be bypassed by a technique namely ROP and ret2libc.

Samiux

Yes, but it cannot bypass ASLR, which comes enabled in Ubuntu by default.

---

### Post by samiux on 2012-08-26
> **rookcifer said:**
> Yes, but it cannot bypass ASLR, which comes enabled in Ubuntu by default.

ASLR can be overcame by partial overwrite technique.

Samiux

---

### Post by kleenex on 2012-09-01
Okay, please let's leave hacking techniques to bypass NX technology. It is possible to install PAE kernel on computer with 1GB of RAM memory and achieve benefit from NX technology? In the previous post, I gave a link to an interesting description called: **x86, cpu: Clear XD_DISABLED flag on Intel to regain NX** and there is written quite interesting thing:
[quote=Kees Cook](...) This bit was traditionally used for operating systems that did not understand how to handle the NX bit. Since Linux understands this, this BIOS flag should be ignored by default (...)[/quote]
Pretty interesting, but I do not know if it fits to this thread. Is there a possibility to check if my computer is using NX bit, because I do not have ideas. PAE kernel is profitable with 1GB of RAM memory? What I should do? Fortunately, this problem is on the computer for testing some features. I just want, that NX technology was one of these tested features.

---

