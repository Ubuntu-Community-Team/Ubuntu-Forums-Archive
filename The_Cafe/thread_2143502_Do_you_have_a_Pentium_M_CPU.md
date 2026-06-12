---
title: "Do you have a Pentium M CPU?"
date: 2013-05-09
forum: The Cafe
---

### Post by sudodus on 2013-05-09
We have issued this poll in order to know how much effort to focus on the Pentium M problems with PAE kernels .

[SIZE=4]Do you have a Pentium M CPU?[/SIZE]

To find out, please run

```
cat /proc/cpuinfo
```

 in a terminal window if are using Linux.

If you are using Windows, check

***Control Panel > System***

So, please ***before*** voting, make sure what type of CPU you have :)

[COLOR=#0000ff]{The poll is stopped. See post #7}[/COLOR]

---

### Post by Dragonbite on 2013-05-09
I know I do because my laptop couldn't bootup with the stock-12.04, but was able to with the alternative kernel or with Xubuntu.

As annoying as it is, I don't know if it is worth spending a lot of time on a work-around.

---

### Post by sudodus on 2013-05-09
> **Dragonbite said:**
> I know I do because my laptop couldn't bootup with the stock-12.04, but was able to with the alternative kernel or with Xubuntu.

As annoying as it is, I don't know if it is worth spending a lot of time on a work-around.

You can live happily with Xubuntu 12.04 until April 2015 :-) unless you want to test a new version. I have tried to make it easy at

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by Dragonbite on 2013-05-09
> **sudodus said:**
> You can live happily with Xubuntu 12.04 until April 2015 :-) unless you want to test a new version. I have tried to make it easy at

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

I know, but by that time the computer may be so old it'll be time to get a new one.  Or I can switch to another distro until they implement the non-PAE kernel only position.  Then I guess I'd be stuck with Windows 7 only.

---

### Post by mips on 2013-05-09
I also have one. I need to use non-PAE kernels/distros.

---

### Post by sudodus on 2013-05-09
> **mips said:**
> I also have one. I need to use non-PAE kernels/distros.

There are still several non-pae 'Ubuntu family' alternatives. But look at this link if you want to run pae kernels

[http://ubuntuforums.org/showthread.php?t=2143297](http://ubuntuforums.org/showthread.php?t=2143297)

Which version of Pentium M is it? Would it be interesting for you to check, if it has pae capability, even if it has no pae flag?

---

### Post by sudodus on 2013-05-09
This brief poll is stopped now. The result at 100 replies is

* 30 persons have a Pentium M CPU
* 70 persons do not have a Pentium M CPU

This percentage may be biased, because people who have this CPU may be more willing to reply, so let us only count the number of Pentium M CPUs reported.

This can be combined with the number of people who have reported that they are affected by 'the bug' at Launchpad.

The bug report shows 93 effected + 13 duplicates:  [https://bugs.launchpad.net/baltix/+bug/930447](https://bugs.launchpad.net/baltix/+bug/930447)

My conclusion is that many Pentium M CPUs are still used, and we should keep them in focus. At Windows XP end of life, there is an opportunity to convert a fair part of them to the Ubuntu flavours with a light foot-print. See this link

[http://ubuntuforums.org/showthread.php?t=2143297](http://ubuntuforums.org/showthread.php?t=2143297)

---

### Post by mips on 2013-05-09
> **sudodus said:**
> 
Which version of Pentium M is it?

Celeron M 360, [http://ark.intel.com/products/27143](http://ark.intel.com/products/27143) , [http://en.wikipedia.org/wiki/Dothan_(microprocessor)#Dothan](http://en.wikipedia.org/wiki/Dothan_(microprocessor)#Dothan)

It's OC'ed to 1.87GHz and I run a Arch based distro on it which still does non-pae by default.

---

### Post by sudodus on 2013-05-09
It's an early one with only 1.4 GHz nominally. So the chance that there is pae capability may be low. But if you like, you can test it with a 'grub-n-iso' USB boot pendrive, that you create via the instructions and image files at

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by zer010 on 2013-05-09
Stuff like this has interested me since I started using *buntu/Linux on an 800Mhz PIII in 2009.   People say that using a light-weight distro is great for reviving old computers, but for how long?  I started hearing that the kernel was getting cleaned up and some older hardware was getting phased out back then. Most people told me not to worry, that my PIII was still good for another 10 years or so, but it got me thinking.  I guess one could still use an old kernel, but that would essentially negate the many, MANY improvements made in the newer versions that does not pertain to specific hardware.  I'm glad to see that at least some thought is put to these issues.

---

### Post by sudodus on 2013-05-09
I think your PIII will work with the current Lubuntu kernels, because it has PAE. 800Mhz is rather low, but with enough RAM, the computer might do a good job with the right mixture of desktop environment and application programs. I would say that Lubuntu is the first choice among the Ubuntu flavours.

So how long an old computer is useful depends a lot on what you want to do with it, how many applications you want to run at the same time and how long you want to wait. See also the general recommendations of *mörgæs* at this thread

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by zer010 on 2013-05-10
> **sudodus said:**
> I think your PIII will work with the current Lubuntu kernels, because it has PAE. 800Mhz is rather low, but with enough RAM, the computer might do a good job with the right mixture of desktop environment and application programs. I would say that Lubuntu is the first choice among the Ubuntu flavours.

So how long an old computer is useful depends a lot on what you want to do with it, how many applications you want to run at the same time and how long you want to wait. See also the general recommendations of *mörgæs* at this thread

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

Thanks, but I got rid of that dumpster dinosaur a while back. Since then I've rescued many other desktops and have enjoyed them all.  Now that I've got a modern laptop, this doesn't worry me as much as it used to, still, I use Lubuntu on my new machine.  I can't help it, I love LXDE! ^_^d

---

### Post by sudodus on 2013-05-13
[SIZE=3]Lubuntu-fake-PAE[/SIZE]

Hello all Pentium M users,

Please visit the preliminary wiki page  [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)   and tell me what you think.   

Now there is also a new  GUI method to install directly from Windows.

---

### Post by sudodus on 2013-06-06
I have improved the security of Lubuntu-fake-PAE referring to a new Ubuntu  Forum ***tutorial***, that should be hard to edit by others than myself and  trusted forum administrators. See this link

[https://help.ubuntu.com/community/Lu..._and_signature]("https://help.ubuntu.com/community/Lubuntu-fake-PAE#Checksums_and_signature")

and its link to the tutorial

[http://ubuntuforums.org/showthread.php?t=2151890](http://ubuntuforums.org/showthread.php?t=2151890)

---

### Post by TNFrank on 2013-06-06
My HP has a Pentium "M" Centrino, 1.86GHz, 32 bit and seems to be running just fine on the standard Ubuntu 12.04.2 OS.  Was there suppose to be a problem with it or something?

---

### Post by sudodus on 2013-06-06
No, the newer Pentium M CPUs have the PAE flag, typically (but not only) with clock frequency above 1.7 GHz, and bus speed 533 MHz. Your CPUs is not affected by this problem :-)

[https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

> Revisions of the Dothan core were released in the first quarter of 2005 with the **Sonoma** chipsets and supported a 533 MT/s FSB and **XD** (Intel's name for the [NX bit]("https://en.wikipedia.org/wiki/NX_bit")) (and [PAE]("https://en.wikipedia.org/wiki/Physical_Address_Extension")  support required for it was enabled, unlike earlier Pentium Ms that had  it disabled). These processors include the 730 (1.6 GHz), 740  (1.73 GHz), 750 (1.86 GHz), 760 (2.0 GHz) and 770 (2.13 GHz). These  models all have a TDP of 27 W and a 2 MB L2 cache.

But I think all Banias and I know many Dothan Celeron M and Pentium M CPUs have PAE capability but do not show a PAE flag. I have a Dothan Pentium M at 1.7 GHz without a PAE flag.

---

### Post by TNFrank on 2013-06-06
Yep, my FSB is 533MHz so I'm ok then. Just wanted to make sure all was well with my 'puter in Ubuntu land.;)

---

