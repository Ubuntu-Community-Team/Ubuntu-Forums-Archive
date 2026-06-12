---
title: "ubuntu 64 bits"
date: 2014-12-10
forum: Ubuntu, Linux and OS Chat
---

### Post by joach on 2014-12-10
I'm currently learning how works the kernel, and found that in the sources of the kernel there is not sources for x86_64

So how ubuntu can be 64 bits compliant as the kernel does not support it ?

see : [https://github.com/torvalds/linux/tree/master/arch](https://github.com/torvalds/linux/tree/master/arch)


or maiby a miss something.....


Thanks

---

### Post by TheFu on 2014-12-10
Certainly, it is in the x86 tree and controlled through compiler options/macros.
I suspect that x64 is the default and the 32-bit version is the special case more these days.

OTOH, I don't **know** anything.  I usually get my kernels from kernel.org to get only stable versions, not whatever is being tested today.

---

### Post by grahammechanical on 2014-12-10
May I suggest that you do some research on 32 bit and 64 bit CPU instruction sets?

A 32 bit OS/kernel will run on a CPU that has a 64 bit instruction set because the CPUs were designed to be backwards compatible with the 32 bit instruction set. But a 32 bit OS and its 32 bit applications can never make full use of the potential that comes with the 64 bit CPU's ability to run instructions that are 64 bits long. Which by the way, are twice the length of 32 bit instructions. 64 bit instructions = faster computing.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Ubuntu uses the kernel that comes from the Linux kernel developers. You could put your conclusion to Linus Torvalds but I warn you, from what I have heard, well to put it politely, Linus is often impolite in his speech.

If Linux was not a 64 bit kernel, then it would not be used on the massive super computers as it would not have the capability to address all the memory that those machines have and as a 32 bit OS it would be a lot slower then the users of those machines desire.

> [COLOR=#252525][FONT=sans-serif]Linux runs as the main operating system on IBM's [/FONT][/COLOR][Blue Gene]("http://en.wikipedia.org/wiki/Blue_Gene")[COLOR=#252525][FONT=sans-serif] and other fastest [/FONT][/COLOR][supercomputers]("http://en.wikipedia.org/wiki/Supercomputer")[COLOR=#252525][FONT=sans-serif]. As of November 2014[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif], the Linux OS family has a 97% share of all systems on the [/FONT][/COLOR][TOP500]("http://en.wikipedia.org/wiki/TOP500")[COLOR=#252525][FONT=sans-serif] supercomputers list.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

As a test, you could try running a Ubuntu AMD64 live session on a machine with a 32 bit CPU. See, what happens. Something will stop the process. Linux 64 bit will push 64 bit long instructions to the CPU and if that CPU can only accept 32 bit long instructions, what then?

Regards.

---

### Post by oldfred on 2014-12-10
Are you confused as the name is amd64 in the ISO?

There is a bit of history marketing, legal, and contractual involved. 

But AMD had license from Intel for 32 bit chips as vendors required two sources. And Intel decided to develop Intel Itanium (formerly IA-64) which was not compatible with the 32 bit versions. AMD developed a 64 bit version that was compatible and also ran the 32 bit versions. Intel then went back and developed its 64 bit version that is compatible with AMD's version and 32bit/64bit systems.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

