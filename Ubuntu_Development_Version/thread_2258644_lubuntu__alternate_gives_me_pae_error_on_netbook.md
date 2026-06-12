---
title: "lubuntu  alternate gives me pae error on netbook"
date: 2014-12-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-12-29
lubuntu i386 and alternate give me a pae error, say that I have to use <forcepae> but that the option is not allowed on Celeron M?? 

it is an EasyPeasy netbook that already has a version of Linux installed.

---

### Post by schragge on 2014-12-30
If it already has Linux on it, you can
```
grep pae /proc/cpuinfo
``` to see if your CPU sports pae flag. If not, and it's Pentium M/Celeron M then there's a decent chance that it supports PAE nevertheless, but you will need the boot option forcepae in order to be able to run PAE-enabled kernels.
See [uhelp]community/Lubuntu-fake-PAE[/uhelp]

---

### Post by sudodus on 2014-12-30
**forcepae** as well as **fakepae** will work with most **Celeron M** and **Pentium M** CPUs. Try, if it does not work, I think it will just refuse to work.

See this link [https://help.ubuntu.com/community/Lubuntu-fake-PAE#Test](https://help.ubuntu.com/community/Lubuntu-fake-PAE#Test)

---

### Post by ventrical on 2014-12-30
@schragge, sudodus

 I thought alternate and i386 *were* for non pae machines.

Thanks .. I'll give it a try because the curent version of linux needs a password which I do not have and I just wnat to try ligthweight x11 DE on there.

 I'll check back in .. let you know what happened.

---

### Post by ventrical on 2014-12-30
Ahhhh...

> 
With the **Install** choice high-lighted press F6. (This option needs less RAM than installing from 'Try Lubuntu') 
A menu with a number of options appears. The option 'forcepae' is not there, so press Escape to close the list. 
Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'forcepae' to the string **after** the two dashes. 
... quiet splash -- forcepaePress return, and the installation begins. 
 
[h=2][/h]Thanks very much .. the missing link :)

---

### Post by sudodus on 2014-12-30
You are welcome and happy new year :-)

---

### Post by ventrical on 2014-12-30
Success:) 

Thanks!

Happy New Years to you all..:)

---

### Post by sudodus on 2014-12-30
By the way, I have been updating and polishing the standard version of One Button Installer during these days between Christmas and New Year.

An alternative that you might want to test, is to use it to install a mini system (originally made from Ubuntu 14.04 mini.iso) with a menu to select various light (ultra light to medium light) desktop environments. It installs a portable system even as a text based system.

The following tarball contains *phillw*'s nonpae kernel, that you tested some time ago (I think during last summer).

**Trusty-nonpae-txt5.tar.xz**

This tarball was updated/upgraded today to the following tarball, and the kernel was replaced with the current generic pae kernel.
[B]
Trusty-mini-txt6.tar.xz[/B]

This standard version of the One Button Installer works only from mass storage devices (USB pendrives, but also from IDE drives and SATA drives). And you can install in one computer and port the drive to another computer. See this link for more details.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by ventrical on 2014-12-30
ASUS Eee PC Series running Lubuntu forcepae.

[https://www.youtube.com/watch?v=jZ1bmsMeRzI&feature=youtu.be](https://www.youtube.com/watch?v=jZ1bmsMeRzI&feature=youtu.be)

Unbelievable...

---

