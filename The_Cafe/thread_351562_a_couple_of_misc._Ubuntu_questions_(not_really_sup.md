---
title: "a couple of misc. Ubuntu questions (not really support)"
date: 2007-02-02
forum: The Cafe
---

### Post by jdhore on 2007-02-02
Hi all, i'm currently running Ubuntu Edgy and....it's having some problems...i don't care to fix them since there are so many, here are my 2 questions:

1. if i'm going to be staying with Ubuntu (most likely), should i go to the latest alpha/herd of Fiesty so i don't have to upgrade in 3 months or should i stay with Edgy at least for now?

2. If i do decide to switch distros, the only one i'd be considering going to is SabayonLinux, i know many people (especially RAV_TUX) use it and are very happy with it, i have really 3 questions about it: 1. Is it anywheres near as hard to install as Gentoo? 2. is portage comparable/as easy to use as apt (also, is there a GUI frontend to it)? 3. is the CD version of Sabayon good enough to use to test and do a HD install from and get MOST of the good stuff/features?

THANKS!
JD

---

### Post by 23meg on 2007-02-02
> 
1. if i'm going to be staying with Ubuntu (most likely), should i go to the latest alpha/herd of Fiesty so i don't have to upgrade in 3 months or should i stay with Edgy at least for now?Stay with Edgy. Feisty isn't ready for full time use.

---

### Post by unbuntu on 2007-02-02
> **jdhore said:**
> 
2. If i do decide to switch distros, the only one i'd be considering going to is SabayonLinux, i know many people (especially RAV_TUX) use it and are very happy with it, i have really 3 questions about it: 1. Is it anywheres near as hard to install as Gentoo? 2. is portage comparable/as easy to use as apt (also, is there a GUI frontend to it)? 3. is the CD version of Sabayon good enough to use to test and do a HD install from and get MOST of the good stuff/features?

THANKS!
JD

I currently have Sabayon 3.26 installed.

1. No. The installation is as simple as Ubuntu, if not simpler.
2. emerge is quite straight forward, and yes there is a GUI front end (Kuroo) which is already there right from the start.  The tool is easy to use just as apt-get.  The difference is you can install either ebuilds (in debian's term: precompiled packages) or compile from source through emerge.  But I'm afraid the repository isn't as big as Debian's (someone confirm me on this)
3. I download the LiveDVD and everything is there.  Don't know about the CD version.  As far as I know, they put more effort on DVD version.

---

### Post by mips on 2007-02-02
> **jdhore said:**
> Hi all, i'm currently running Ubuntu Edgy and....it's having some problems...i don't care to fix them since there are so many, here are my 2 questions:

1. if i'm going to be staying with Ubuntu (most likely), should i go to the latest alpha/herd of Fiesty so i don't have to upgrade in 3 months or should i stay with Edgy at least for now?

2. If i do decide to switch distros, the only one i'd be considering going to is SabayonLinux, i know many people (especially RAV_TUX) use it and are very happy with it, i have really 3 questions about it: 1. Is it anywheres near as hard to install as Gentoo? 2. is portage comparable/as easy to use as apt (also, is there a GUI frontend to it)? 3. is the CD version of Sabayon good enough to use to test and do a HD install from and get MOST of the good stuff/features?

THANKS!
JD

If you want a stable ubuntu use Dapper LTS.

I have not used ubuntu for close to 4mnths now. I'm very happy with sabayon and it is fast. 

Try sabayon. I'm not saying it's gonna work perfectly for you but you wont know until you try.

---

### Post by daniel of sarnia on 2007-02-02
> **mips said:**
> If you want a stable ubuntu use Dapper LTS.



Edgy is vary stable too, so that is not an issue. Use edgy for now,  and it's probably only safe to think about moving to Fiesty in it's later betas or if you are not really experienced with linux it would be best to wait for at lest the RC.  

I don't know about sabayon but I used gentoo, and personally I think you really don't gain much from recompiling everything for your cpu type. That's why the kernel for ubuntu and fedora (and I bet other distros) just use one generic linux kernel for all x86 cpus. With ram as cheep as it is now if you're really dieing for speed that much I'd just buy another stick of ram and not wast my time compiling everything for source and hoping for gains.   

But it does not hurt to try both distros, it's just been my personal experience that you don't gain that much speed from a built form source distro. To me they don't seem that stable, mostly over long terms of use though, not bad at first though.

---

### Post by mips on 2007-02-02
> **daniel of sarnia said:**
> Edgy is vary stable too, so that is not an issue. Use edgy for now,  and it's probably only safe to think about moving to Fiesty in it's later betas or if you are not really experienced with linux it would be best to wait for at lest the RC.  


Dapper works fine here. Edgy on the other hand was nothing but a pain in the a$$ for me. There has been many complaints about edgy here. Some people had better luck though and did things for them that dapper did not.

---

### Post by fuscia on 2007-02-02
i had sabayon installed for about a week. it's very fast, but the bootup time and installing new apps was too slow for me. it's a nice distro, it just wasn't for me.

---

### Post by jdhore on 2007-02-02
thanks for your help everybody! i do have 2 final questions though:

1. i have a Nvidia graphics card and i really want/need dual-monitor...in Ubuntu all i had to do was install the binary driver and add 2 lines to my xorg.conf (the Twinview option and the orientation of my monitors), it is about that easy to setup dual-monitor in Sabayon?

2. If i do get dual-monitor working, will AIGLX/Beryl work?

---

### Post by shining on 2007-02-02
> **jdhore said:**
> 
1. i have a Nvidia graphics card and i really want/need dual-monitor...in Ubuntu all i had to do was install the binary driver and add 2 lines to my xorg.conf (the Twinview option and the orientation of my monitors), it is about that easy to setup dual-monitor in Sabayon?


Probably, it should be easy in every linux distribution. Even in the ones who don't have a package system, or don't have packages for nvidia, you can still download the driver from nvidia's site and launch it. And then edit xorg.conf as you like.
But Sabayon probably has something.

---

### Post by jdhore on 2007-02-02
*bump*

---

