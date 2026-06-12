---
title: "XD/NX/'Exec Shield' and  'DEP' for 32 bit Intel"
date: 2008-03-02
forum: Security Discussions
---

### Post by pingnak on 2008-03-02
Fresh from a 'rant' that Windows XP/Vista users should generally turn 'DEP' (Data Execute Prevention) on, I realized I'm not so certain its cousin is turned on in 32 bit Ubuntu by default.

I have 7.10 installed and I was wondering if there's a simple way to query whether 'XD' is used on 32 bit Intel machines that support it.

I couldn't seem to find an unambiguous answer from various web searches I tried.  Some state that 'XD'  is not used by default on 32 bit Intel kernels because many Intel CPUs don't have it.  I couldn't find a package to set it up, either... but not much current I could point at.

So I guess I'll ask it here.  Somebody's bound to know.

Where is a simple and accessible 'proof' of 32 bit 'No Execute' or 'Execute Disable' functionality, or absence thereof under Ubuntu?

Is there a package that can selectively enable/disable it?  After all, some software may not play nice with it.

For the moment I can't run 64 bit adequately because of some pesky driver issues and a stubborn black screen from X with no trivial work-around, and a lack the time to 'tinker'.

---

