---
title: "Daru2 and 64bit Ubuntu"
date: 2008-10-27
forum: System76 Support
---

### Post by gamx on 2008-10-27
I have a Daru2 and I would like to make a fresh install when Intrepid comes out later this week. I am planning to replace the original 32bit Ubuntu with the 64bit one. Is there any major problem I should be aware of? Is power management working better/worse than with the 32bit version?
I guess I only need to install Ubuntu in the standard way and add the System76 driver, right?
Thanks.

Gamx

---

### Post by thomasaaron on 2008-10-27
We've not tested 8.10 on the DarU2 yet. You'll probably want to go with 64-bit. But based on some other threads, their may be some power management issues we need to work out.

So, I'd recommend not jumping the gun just yet. If you wait until it is released, we should have any issues worked out.

---

### Post by gamx on 2008-10-27
Thanks for the advice.

---

### Post by Dareajoe on 2008-10-31
Which is better?:lolflag:
If you are doing heavy work where you have started to hit the 4GB memory barrier, then 64-bit is for you...
Also certain type of encoding tasks (ie video) run faster on 64-bit processors (NOTE: this is implementation specific).
Early 64-bit adopters were plagued by incompatibility problems (most noticeably Java and Flash), however this is no longer an issue.
Some applications do run slower in 64-bit mode, however work continues to improve on this.
Other platforms (like Windows) which also come in 32 and 64-bit flavours are experiencing significantly more problems especially due to a lack of 64-bit device drivers as incompatible user application. As Ubuntu is entirely open source, this is not the case as all hardware supported by Ubuntu works equally well in 32-bit and 64-bit environments. The same applies to user applications as well........

---

### Post by gaussian on 2008-10-31
> **Dareajoe said:**
> Which is better?:lolflag:
Early 64-bit adopters were plagued by incompatibility problems (most noticeably Java and Flash), however this is no longer an issue.


I would have to say the proper wording there is "this is less of an issue" now. I just switched back to 32-bit (I have 64-bit Gutsy and 32-bit intrepid on my Daru) just because at least using Flash 9 some kiddie game websites worked better/worked at all only using 32-bit (nspluginviewer is good, but not perfect). You can get everything working as well under 64-bit if you are willing to use 32-bit programs. There are two options:

1) chrooting (I've done that).
2) installing 32-bit libraries and programs alongside 64-bit (never tried).

Both are somewhat hackish things to do, but the second can be made easier with getlibs-script (never tried myself). Note that 2 has the big downside of having a lots of programs/libraries that are not installed in the proper debian/ubuntu way in your system.

---

### Post by jdb on 2008-10-31
> **gamx said:**
> I have a Daru2 and I would like to make a fresh install when Intrepid comes out later this week. I am planning to replace the original 32bit Ubuntu with the 64bit one. Is there any major problem I should be aware of? Is power management working better/worse than with the 32bit version?
I guess I only need to install Ubuntu in the standard way and add the System76 driver, right?
Thanks.

Gamx

64 bit can address memory above 4 gig, that's it's main advantage.

It's disadvantage is that there is more overhead required to handle 64 bits.
There is an extra layer of pointers in the memory lookup tables.
Whenever an address is stored it takes up twice as much space and that causes more ram to be used.

Almost (I haven't run into any that aren't) all programs are available in 32 bit versions that will run with no fuss or added effort.
That can't be said about 64 bit versions.

When the day comes that a normal computer comes with over 4 gigs (it will), then 64 bit will be ubiquitous.



jdb

---

