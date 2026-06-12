---
title: "Usage of Intel C/C++ Compiler for faster applications."
date: 2008-11-28
forum: Ubuntu Brainstorm
---

### Post by yaknowwat on 2008-11-28
The Intel C/C++ Compiler has been proved to be capable of compiling at a very well done level.  Maybe seeing if its possible to use it for the x86/x86_64 ports of the ubuntu repositories in order to provide a faster experience overall.


If gcc has been made faster than Intel C/C++ in their development version or something disregard this.

---

### Post by smartboyathome on 2008-11-28
What I don't think will happen by doing this will be that we will gain a significant enough speed boost. I think what we have now is good.

---

### Post by yaknowwat on 2008-11-29
> **smartboyathome said:**
> What I don't think will happen by doing this will be that we will gain a significant enough speed boost. I think what we have now is good.

There have been reported pretty optimized code coming out of Intel compiler like normally up to a capable 30% or more and about 10% on average ( These are underestimations of actual statistics that i've seen. ).  10% is plenty enough to make a noticeable difference in speed if its done across the board.

---

### Post by Progressive on 2008-11-29
Is it open source? If not then it is out of the question. If it is open source, then the improvements will likely wind up in gcc unless there is a good reason not to.


A lot of the newest improvements actually can be implemented with gcc, it is just that it is not always good to use them to maintain compatibility with older processors.

If you are interested in having a fully optimized computer, use Arch Linux or Gentoo. If you want a hassle-free computer, use Ubuntu.

Cheers

---

### Post by mentallaxative on 2008-11-29
1. It's not open source. The license is for personal, non-commercial use.

2. It's not fully compatible with gcc. I spent several hours today compiling various applications in Arch Linux. Some of them use options specific to gcc which will cause the compilation to fail with icc. I have avoided compiling anything system-critical as most of them are gnu-related.

3. For the best optimisation you have to specify compiler flags specific to your processor. Since Ubuntu caters for a large range of processors, this is not possible. Even when optimised fully the difference is not great or consistent.

---

### Post by Maduroutmb on 2008-11-29
This would be an issue for people who use AMD chips.  In fact, using the Intel x86 compiler would blunt one of the great benefits that open source computing will eventually allow: architecture agnostic software.  Right now, only x86 sells because commercial software is delivered in binary.  Mac folks get a bone every once in a while, while SPARC and POWER are largely ignored. As long as source code is closed and compilers are not free, this will persist.

In contrast, open source code and a compiler that anyone can use (even people who are scared of computers) allow non-x86 architectures to compete on their own merits, rather than on the results of an architecture popularity contest.  See Itanium and Intel's new effort to build an x86 GPU/GPGPU. In one case, you have a novel approach to processor architecture and compiler tech thrown under the bus because it was not popular enough.  In the other, you have Intel overcompensating by applying x86 to a market that does fine without it.  

Breaking the chicken-egg stranglehold of x86 chips and x86 binaries is a distant goal, but it may wind up being one of the most important results of the open source movement.  Using the Intel compiler moves things in the opposite direction, to everyone's ultimate detriment.

---

### Post by cmay on 2008-11-29
to the best of my knowledge about compilers which is not that great i seem to have the understanding than gcc is the only compiler that can build the linux kernel. if such compiler as intel which is not standard on all distributions where to be used then ubuntu would begin to work against the stream too much in my opinion regardless of speed or being able to compile kernel or not. i would still use gcc as i do on bsd open-solaris and all other linux distributions. since its the standard compiler collection.

---

### Post by bruce89 on 2008-11-29
> **mentallaxative said:**
> 1. It's not open source. The license is for personal, non-commercial use.


As I'm sure you know, Ubuntu is not a personal project, and there is no non-commercial ban. This is therefore a non-starter.

---

