---
title: "Ubuntu Netbook vs. x86 vs. x64"
date: 2011-03-14
forum: The Cafe
---

### Post by Shibblet on 2011-03-14
I did a recent trial at home.  I purchased a Dell Mini 1012.  This is equipped with an Atom N450 Processor.

I loaded the Ubuntu Netbook Edition first, and it seemed to run just fine, in Gnome and Unity.

I then loaded the standard desktop edition, and it ran similar to the Netbook version in Gnome.

Then I loaded the x64 version, and WHOA, the performance increase is very noticable.

I thought that the version differences only had to do with memory allocation.  Is the x64 version that much faster on a 64-Bit processor?

---

### Post by LowSky on 2011-03-14
On a netbook memory allocation is a very big deal.

---

### Post by Paqman on 2011-03-14
> **Shibblet said:**
> 
I thought that the version differences only had to do with memory allocation.  Is the x64 version that much faster on a 64-Bit processor?

64-bit is noticeably faster for some tasks, yes. There's no reason to throttle a 64-bit chip down by using 32-bit software IMO.

---

### Post by MadCow108 on 2011-03-14
> **Shibblet said:**
> I did a recent trial at home.  I purchased a Dell Mini 1012.  This is equipped with an Atom N450 Processor.

I loaded the Ubuntu Netbook Edition first, and it seemed to run just fine, in Gnome and Unity.

I then loaded the standard desktop edition, and it ran similar to the Netbook version in Gnome.

Then I loaded the x64 version, and WHOA, the performance increase is very noticable.

I thought that the version differences only had to do with memory allocation.  Is the x64 version that much faster on a 64-Bit processor?

the differences probably is due to the 64 bit versions being compiled only for amd64 and thus the compiler can utilize the 8 registers this architecture has more efficiently than it could when compiling for i386 where it must assume only 4 registers.

that the addressable memory space is larger should have nothing to do with it (in contrary it could even decrease speed in certain border cases)

---

### Post by ssam on 2011-03-14
> **MadCow108 said:**
> the differences probably is due to the 64 bit versions being compiled only for amd64 and thus the compiler can utilize the 8 registers this architecture has more efficiently than it could when compiling for i386 where it must assume only 4 registers.

that the addressable memory space is larger should have nothing to do with it (in contrary it could even decrease speed in certain border cases)

there are more registers than 4 and 8, but otherwise that is right. also all x86-64 chips have SSE so that can be enabled.

---

### Post by Shibblet on 2011-03-14
> **MadCow108 said:**
> that the addressable memory space is larger should have nothing to do with it (in contrary it could even decrease speed in certain border cases)

Well, I had thrown an extra gig of ram in there for good measure.  So it has 2 gigs now.  Ubuntu still utilizes memory a lot more efficiently than Windows does, so 2 gigs does me just fine.

x64 does use more system memory than x86 does, but the difference is minimal.

---

