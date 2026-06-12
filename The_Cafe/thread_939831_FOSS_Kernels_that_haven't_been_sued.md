---
title: "FOSS Kernels that haven't been sued"
date: 2008-10-06
forum: The Cafe
---

### Post by darrelljon on 2008-10-06
Hypothetical questions, if all the legal actions (either currently pending or settled) against FOSS kernels (I'm thinking mainly SCO v Linux and the BSD case) had succeeded, what kernel would FOSS enthusiasts be using? Hurd?

---

### Post by Tomosaur on 2008-10-06
> **darrelljon said:**
> Hypothetical questions, if all the legal actions (either currently pending or settled) against FOSS kernels (I'm thinking mainly SCO v Linux and the BSD case) had succeeded, what kernel would FOSS enthusiasts be using? Hurd?

They'd just carry on using the kernel anyway. The beauty of FOSS projects is that there is no central controlling group to sue. The worst they can do is sue the original developer of a particular piece of code - or some company who stands to profit from that code (Novell or whatever), then that doesn't stop you or I from using or continuing to develop the kernel. It's impossible to beat something that doesn't exist. If Novell (as an example) dissappeared tomorrow - then there'd still be people contributing and developing the code that Novell sponsors, who aren't in any way affiliated with Novell.

As a somewhat morbid example (well, it's nearly halloween!) - if somebody killed you tonight, it wouldn't stop me from breathing the same oxygen.

---

### Post by darrelljon on 2008-10-07
If you carried on using a kernel which had been sued successfully, wouldn't you be engaging in software piracy? I can't see FOSS enthusiasts doing that.

---

### Post by Tomosaur on 2008-10-07
> **darrelljon said:**
> If you carried on using a kernel which had been sued successfully, wouldn't you be engaging in software piracy? I can't see FOSS enthusiasts doing that.

Nobody owns the kernel. Who would you be pirating **from**? Besides which, there's no reliable way to track who's using a particular kernel, with which modules etc. No company would be willing to spend the ridiculous sum of money that would be required to put an end to the kernel.

The reason legality is called into question over the Linux kernel is copyright / IP claims. Kernel developers have always said that if a company can show them which parts of the kernel are infringing, and prove that they're infringing, then they will remove / alter those parts. So far, nobody has done this. The kernel is open for all to examine, so there's no reason why, if a company thinks the kernel is using 'stolen' code, the infringing parts can't be pointed out. The kernel developers don't WANT stolen code in the kernel - they're very vocal about this. But until somebody can prove that some code IS stolen, they can't do anything about it.

The issue is that you can't 'sue' a kernel. There's no single entity that lawyers can point to and say 'these guys have stolen our stuff'. The most they can do is threaten people, spread FUD, and all the general useless tactics that we see all the time.  Microsoft makes a lot of noise saying that the Linux kernel is in dubious legal territory, but this is a scare tactic. It benefits them more to just shout about how Linux users are pirates and better watch out, than to tell the kernel devs where they're infringing and how to do something about it.

---

### Post by qazwsx on 2008-10-07
Syllable (well it is rather complete OS)?
[LUnix]("http://en.wikipedia.org/wiki/Lunix")? :)
etc 


There are actually plenty of free kernels and OSs

---

### Post by ssam on 2008-10-07
> **Tomosaur said:**
> Nobody owns the kernel. Who would you be pirating **from**?

All the developers own the copyright to the kernel. They give you permission to copy/use it under the GPL. If you dont follow the GPL you are committing copyright infringement.

If SCO (or anyone else) could prove that they own the copyright to part of the kernel, they could choose under what conditions you could copy/use it. These conditions would likely be a 'you need to pay a licence fee'.

The only reason the GPL has any strength is because of copyright.

---

### Post by Tomosaur on 2008-10-07
> **ssam said:**
> All the developers own the copyright to the kernel. They give you permission to copy/use it under the GPL. If you dont follow the GPL you are committing copyright infringement.

If SCO (or anyone else) could prove that they own the copyright to part of the kernel, they could choose under what conditions you could copy/use it. These conditions would likely be a 'you need to pay a licence fee'.

The only reason the GPL has any strength is because of copyright.

Yes, but licenses can't be changed retroactively. If the developers suddenly decided 'oh actually no, im changing the copyright', the only the later versions would be affected. Current incarnations would be developed as usual.

On top of this - if a company could prove any part of the kernel was infringing, then the offending portion would be altered or removed.

---

### Post by ssam on 2008-10-07
the licence would effectively be changed if SCO proved they owned some of the code.

Suppose it was found that a significant part of linux kernel 2.6.27 had been written by SCO, and the kernel developers had taken this code and claimed authorship. Now the 2.6.27 kernel would not be GPL anymore, because the people who told you that it was would not have had the right to. (this is a very unlikely situation, not much need to worry)

If just a small bit of the kernel was found to have been taken from somewhere it should not have, then it could probably be rewritten. You may need to get someone who had never seen the stolen code to do it though.

There are quite a few kernels that could be dropped in if something like this were to happen. maybe Solaris or one of the BSDs

---

### Post by LaRoza on 2008-10-07
> **darrelljon said:**
> what kernel would FOSS enthusiasts be using? Hurd?

Hurd isn't a kernel.

---

### Post by Canis familiaris on 2008-10-07
> **LaRoza said:**
> Hurd isn't a kernel.

It is. At least all sources I read and Wikipedia says that
[http://en.wikipedia.org/wiki/GNU_Hurd](http://en.wikipedia.org/wiki/GNU_Hurd)

---

### Post by LaRoza on 2008-10-07
> **Anurag_panda said:**
> It is. At least all sources I read and Wikipedia says that
[http://en.wikipedia.org/wiki/GNU_Hurd](http://en.wikipedia.org/wiki/GNU_Hurd)

Well, technically it isn't, Hurd is a bunch of services running on top of a kernel (Mach, was the original). GNU Hurd is also the collective term for the kernel and those services, but technically, Mach is the kernel (a microkernel)

---

### Post by phrostbyte on 2008-10-07
> **ssam said:**
> the licence would effectively be changed if SCO proved they owned some of the code.

Suppose it was found that a significant part of linux kernel 2.6.27 had been written by SCO, and the kernel developers had taken this code and claimed authorship. Now the 2.6.27 kernel would not be GPL anymore, because the people who told you that it was would not have had the right to. (this is a very unlikely situation, not much need to worry)

If just a small bit of the kernel was found to have been taken from somewhere it should not have, then it could probably be rewritten. You may need to get someone who had never seen the stolen code to do it though.

There are quite a few kernels that could be dropped in if something like this were to happen. maybe Solaris or one of the BSDs

It's quite a bit of a crazy hypothetical, since even if SCO "owned" part of the kernel somehow, it would only be PART of the kernel, and that part could be discarded.

---

### Post by Tomosaur on 2008-10-07
> **ssam said:**
> the licence would effectively be changed if SCO proved they owned some of the code.

Suppose it was found that a significant part of linux kernel 2.6.27 had been written by SCO, and the kernel developers had taken this code and claimed authorship. Now the 2.6.27 kernel would not be GPL anymore, because the people who told you that it was would not have had the right to. (this is a very unlikely situation, not much need to worry)

If just a small bit of the kernel was found to have been taken from somewhere it should not have, then it could probably be rewritten. You may need to get someone who had never seen the stolen code to do it though.

There are quite a few kernels that could be dropped in if something like this were to happen. maybe Solaris or one of the BSDs

You can't retroactively apply laws and licences. If it wasn't illegal when you did it, then you can't be prosecuted for having done it. All they could do is say 'from now on, you have to pay to use this kernel'.

Of course, the situation may be somewhat different if you download and compile the source code yourself - but distributions who had already made the kernel binaries available couldn't be prosecuted. The businesses which had profited from distributing the illegal code could technically be fined or made to retroactively pay damages to the code's owners, but for users, nothing would happen.

---

