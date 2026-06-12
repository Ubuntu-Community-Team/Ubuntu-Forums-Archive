---
title: "Virtualization questions"
date: 2008-05-03
forum: Virtualisation
---

### Post by Catalyst2Death on 2008-05-03
Hello,

I've been looking around at virtualization to finally kill the XP dual boot.  However, It has been difficult to find the answers to a few questions.  I apologize if they have been answered already, if you could kindly point me to the correct posts, I would be very grateful.

Anyway here they are:

Will virtualization behave EXACTLY as though I were living in XP.  Namely, will I be able to run games (Half-life 2, Guild Wars, etc)  from Windows?

Will I be able to play DVD's from Windows?

Will I need to crack windows to run under virtualization (I'm only asking yes or no, and I do NOT want methods or links to the appropriate answer)?

How much of a performance hit will I see as compared to a dedicated install?

My specs:
AMD 3000+ athlon
Radeon 9600XT 128mb
SoundBlaster Live! 5.1
1gb 333mhz ram
160gb HD

Do different programs offer different levels of efficiency?  If so, which is the most efficient?


Thanks in advance for all of the advice!

---

### Post by Catalyst2Death on 2008-05-04
*bump*
Right now DVD playback is most important...

---

### Post by Shiva88 on 2008-05-04
I can't answer for sure as to the DVD playback, but I think it will work.

Your graphics acceleration will not work, however, so Half-Life, etc, are out.

As far as cracking windows goes, it's going to operate exactly as a stand-alone installation would; you're still going to need a valid cd key, etc.

The performance hit is, in my opinion, substantial.  Assuming you have decent hardware, windows will be perfectly usable, but noticeably slower.

---

### Post by Kokopelli on 2008-05-04
> **Catalyst2Death said:**
> 
Will virtualization behave EXACTLY as though I were living in XP.  Namely, will I be able to run games (Half-life 2, Guild Wars, etc)  from Windows?

No, not realistically. You might be able to play games (xen is your best chance there) but if it is a major point then I would stick to dual booting.

> **Catalyst2Death said:**
> 
Will I be able to play DVD's from Windows?


Yes, though you might have to fiddle to get sound working correctly.  (I would recommend playing DVDs straight in the host system as well.)

> **Catalyst2Death said:**
> 
Will I need to crack windows to run under virtualization (I'm only asking yes or no, and I do NOT want methods or links to the appropriate answer)?


No, as long as you have a legitimate key cracking is not necessary.

> **Catalyst2Death said:**
> 
How much of a performance hit will I see as compared to a dedicated install?


It really depends.  If you are not doing anything that requires 3d performance I would say between 5 and 20%, most of the time a little under 10% hit.  EDIT: That is after tuning your VM for performance.  raw, just throw on XP and see how it does, would be leaning ~15% in my opinion.  I have no hard facts to back this up, just numbers off the cuff.

> **Catalyst2Death said:**
> 

My specs:
AMD 3000+ athlon
Radeon 9600XT 128mb
SoundBlaster Live! 5.1
1gb 333mhz ram
160gb HD

Do different programs offer different levels of efficiency?  If so, which is the most efficient?
Different virualization technologies do have different levels of performance, yes.

Xen generally should provide the best performance but it does require more effort to install.  (Disclaimer:  I have never tried installing XP on Xen.)

KVM is the next option. If your CPU and motherboard both support virutalization extensions it is a decent choice.

VMWare would be the next ranking in performance, with a strong showing in non 3d performance.  It will also be easier to install XP on VMWare (once you have VMWare installed) than in the previous two.

Virtualbox is next.  Virtualbox is much like VMWare but it does not perform quite as well in my experience.  It does have the benefit of being an open source solution though.

Finally there is QEMU.  without vitualization extensions QEMU performance has been awful in my experience.  Generally I would only recommend it if you can not get anything else working.

---

### Post by Catalyst2Death on 2008-05-04
Thank you guys so much, this is exactly what I needed to know!

---

