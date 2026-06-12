---
title: "Any way to run a program from my Windows partition using WINE?"
date: 2010-01-27
forum: Wine
---

### Post by cAlpha on 2010-01-27
I've got Exact Audio Copy (EAC) installed on my Windows partition, which I have mounted to access my shared Firefox profile.  

Is there any way to run it (preferably maintaining all of my settings) from within Ubuntu via Wine without installing a second copy on my Ubuntu partition?

---

### Post by dino99 on 2010-01-27
Some docs and howto talks about that already but it's the hard way, not sure it's very stable.
Better to run your program with wine under your existing ubuntu partition (no need an other partition)

---

### Post by brian70809 on 2010-01-27
It depends on how it runs.  If it is standalone and doesn't use Registry to run, then you can just run with wine in Ubuntu.. Otherwise you have to install through wine.

---

### Post by cAlpha on 2010-01-27
> **brian70809 said:**
> It depends on how it runs.  If it is standalone and doesn't use Registry to run, then you can just run with wine in Ubuntu.. Otherwise you have to install through wine.

How can I tell if it uses the registry to run?

---

### Post by beastrace91 on 2010-01-28
In terminal do ```
wine /path/to/my/file.exe
``` and see if it runs. You should also note that this is **not** the best/ideal way to run an application through Wine, it is known to causes stability issues. Part of this is because the ntfs-3g drivers are not the best as of yet and another part is because actually installing the application is *almost* always best.

Regards,
~Jeff

---

### Post by szaka on 2010-01-28
> **beastrace91 said:**
> In terminal do ```
wine /path/to/my/file.exe
``` and see if it runs. You should also note that this is **not** the best/ideal way to run an application through Wine, it is known to causes stability issues. Part of this is because the ntfs-3g drivers are not the best as of yet
Why not?

---

### Post by beastrace91 on 2010-01-28
Example:

> This is a known limitation of the driver and/or older kernels. Steam requires functionality (mmap with shared write access) which Wine can not emulate if it's not supported on file system.

It appears to be more stable with newer kernels, but my statement still stands that it is better to actually install applications in Wine than just run them form the Windows partition. For example TF2 runs perfectly fine for me installed under Wine however when I run it from a vfat or ntfs partition it chokes and dies quite often.

Regards,
~Jeff

---

### Post by Puppyite on 2010-01-28
I realize this is not what you asked for but Puppy Linux can [run Windows software without installing](http://www.puppylinuxfaq.org/content/13/144/en/run-windows-software-without-installing.html).

---

### Post by beastrace91 on 2010-01-29
> **Puppyite said:**
> I realize this is not what you asked for but Puppy Linux can [run Windows software without installing](http://www.puppylinuxfaq.org/content/13/144/en/run-windows-software-without-installing.html).

That is not any different than how you would run Windows software with out installing in Ubuntu - meaning it is not any more or less stable. Whether or not an application will run with out installing it first under Wine is hit or miss regardless of your distro.

Regards,
~Jeff

---

### Post by cAlpha on 2010-01-29
Tried running EAC as you'd suggested (wine /directory/to/EAC/EAC.exe), and it seemed to work though it didn't include any of the settings I've saved.  

When using it on my Windows partition, I launch it from within the Start Menu (it's one of the last used programs listed)--any ideas about where this version would be located?

---

### Post by beastrace91 on 2010-01-29
You are launching the same "version" of your application on Ubuntu - however the program odds are saves configuration files elsewhere on the hard drive. You will have to hunt these down and copy them to Ubuntu if you want the same setup you have in Windows.

Regards,
~Jeff

---

### Post by szaka on 2010-01-29
> **beastrace91 said:**
> Example:
> 
This is a known limitation of the driver and/or older kernels. Steam requires functionality (mmap with shared write access) which Wine can not emulate if it's not supported on file system.



This is totally irrelevant of NTFS-3G. Kernels older than 2.6.26 didn't support the needed functionality:

 [http://www.tuxera.com/community/ntfs-3g-faq/#wine](http://www.tuxera.com/community/ntfs-3g-faq/#wine)

> 
It appears to be more stable with newer kernels, 

What do you mean by "appears". People are using it every day and we get zero bug report. The only complain I have seen in the past years is yours but you didn't describe any specific problem, only refer to an old issue which was a kernel problem, solved two years ago.
 
> 
but my statement still stands that it is better to actually install applications in Wine than just run them form the Windows partition. For example TF2 runs perfectly fine for me installed under Wine however when I run it from a vfat or ntfs partition it chokes and dies quite often.

That statement is right, I never questioned that. Wine is not designed to run software which were not installed via Wine. No matter if it's FAT, NTFS, ext3, or whatever. Most people use NTFS, so when it doesn't work then some people blames NTFS-3G when the problem is actually that, that the application must be installed via Wine, not via Windows to be run via Wine. This is how Wine was designed to be used.

You wrote "ntfs-3g drivers are not the best as of yet". That's what I'm only interested. What are the NTFS-3G problems? If there is any then we would very much like to know about it to be fixed! Thanks.

---

