---
title: "MS Windows' use of 'hlt' instruction"
date: 2008-11-12
forum: Windows
---

### Post by blackhole54 on 2008-11-12
Hi All,

I was trying to help a MS Windows user with a borked system.  (He didn't listen to my pleas that I don't know anything about MS. ;) )  While trying to assess the situation, I attempted to boot several different Linux live CDs.  They all hung at the kernel message:  *Checking 'hlt' instruction*.  At the time I was thinking this was a serious hardware problem, but after an Internet search, I now realize that this will likely be able to be handled by using the *no-hlt* kernel parameter.  (I have not been back to try this.)  Since I plan on looking at this machine again in maybe a few days, I am trying to get my "facts" about this lined up ahead of time, which is why I am posting what amounts to a "what if" on this thread ...

Assuming *no-hlt* allows my live CDs to boot and I don't find anything else horribly wrong while poking around using Linux, I am wondering what the implication of this problem with the *hlt* instruction is for MS Windows. This guy has both Win2000 and XP installed.  My understanding is that NT and all its descendants (as opposed to Win9x) use the *hlt* instruction to allow the processor to idle.  So my question is if the *hlt* instruction on this processor does indeed fail, whether there is any hope of Win2000 or XP running on this machine.  I gather in the past they have both run.

I have searched the Internet for understanding on this and have come up empty handed.  Can these MS OSes operate with a defective 'hlt' instruction?  Is there some option to allow it work, comparable to the Linux *no-hlt* parameter?

Thanks in advance for any insight you can give.

---

