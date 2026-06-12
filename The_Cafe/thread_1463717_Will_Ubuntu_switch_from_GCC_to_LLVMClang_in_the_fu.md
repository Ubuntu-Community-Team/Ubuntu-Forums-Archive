---
title: "Will Ubuntu switch from GCC to LLVM/Clang in the future?"
date: 2010-04-27
forum: The Cafe
---

### Post by Shining Arcanine on 2010-04-27
The FreeBSD people are switching from GCC to LLVM/Clang:

[http://www.phoronix.com/scan.php?page=news_item&px=NzI1Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzI1Ng)

Will Ubuntu do the same?

---

### Post by gnomeuser on 2010-04-27
LLVM will be a core part of the desktop since our video drivers will be using it. There is also work being done to improve pythons, pitiful, performance using LLVM. Mono now also has support for using LLVM as a backend. More and more projects are being built using LLVM, and it isn't just compilers but the static code analysis and many other things we get along with it that will improve the system in ways GCC simply doesn't allow.

LLVM still doesn't have the same security features as GCC has currently but it is quickly catching up on performance and correctness. It is just a matter of time.

The point being that we will need LLVM and more and more GCC will become a target for replacement if for anything to save space or converge on one compiler.

I doubt it will happen before the next LTS release but I am pretty confident that GCC will eventually be replaced. It would be interesting to try to set up a complete rebuild of something like Ubuntu 10.04 to see how close we are to being able to build a fully working system. 

Even if we won't see a switch in the near future developers have already started using LLVM to analyse their code, e.g. Totem has gotten several bugs fixed thanks to such use. So it will improve the system even if it isn't used to compile it.

Personally I am looking forward to the LLVM powered future.

---

