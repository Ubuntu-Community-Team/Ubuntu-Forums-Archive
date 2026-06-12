---
title: "what if MS base vista on the lin kernel?"
date: 2006-11-04
forum: The Cafe
---

### Post by Somenoob on 2006-11-04
They said they where gonna use another kernel for it. And no one would noticed since it's close source. And they are known for copying software they're interested in.

---

### Post by Klaidas on 2006-11-04
That simply won't happen.

---

### Post by MedivhX on 2006-11-04
Impossible... DOS prompt wouldn't exist... All commands would be like in terminal...

---

### Post by DoctorMO on 2006-11-04
They'd be sued by the FSF because the linux kernel is the linux kernel regardless of how you hide it; you'd still see the compiled version in memory.

Infact they'd be in such big trouble that they might as well hack half of their fortune and give it to the FSF.

Not happening. besides I believe Microsoft to be egotistical and they really do thing kernel32 is better than linux.

---

### Post by lwr on 2006-11-04
It's closed source, but my understanding is that some authorities, like the EU, are allowed to see the source code. I might be wrong. Anyway, Apple tell everyone they used BSD to build OS X, and it hasn't made any difference to their closed-sourceness. Not entirely sure how it all works, but what you suggest would never happen.

---

### Post by jbtito03 on 2006-11-04
Well... actually i think that they might copy the kernel and rewrite it. What do the commands matter? Just "pimp" it like we do with our desktops to look like os x or vista, so the prompt looks like ms dos. Or emulate ms dos :D

I thnik they took quite a lot of ideas and knowlege from other systems.

Have no examples thou. ](*,) 


JB

---

### Post by Joe_CoT on 2006-11-04
> They said they where gonna use another kernel for it. And no one would noticed since it's close source. And they are known for copying software they're interested in.

Vista might include symlinks and XGL-like effects, but think of it this way: which would take more effort

a) Adding aero, symlinks, and ... oh yeah, that's about it for new features at this point

b) switching to the linux kernel, implementing the entire windows API on a posix operating system, and keeping every driver vendor ever shut up about it  .

---

### Post by etc on 2006-11-04
> **MedivhX said:**
> Impossible... DOS prompt wouldn't exist... All commands would be like in terminal...

The GNU utils are separate from the kernel, Microsoft could easily port the DOS stuff if they were motivated.

---

### Post by MedivhX on 2006-11-04
Commands come from kernel... Not from GNU utils... I think...

---

### Post by shining on 2006-11-04
> **lwr said:**
>  Anyway, Apple tell everyone they used BSD to build OS X, and it hasn't made any difference to their closed-sourceness. Not entirely sure how it all works, but what you suggest would never happen.

Isn't that the main difference between GPL and the BSD license?

---

### Post by ultraata on 2006-11-04
That can't happen.

---

### Post by Joe_CoT on 2006-11-04
> Anyway, Apple tell everyone they used BSD to build OS X, and it hasn't made any difference to their closed-sourceness. Not entirely sure how it all works, but what you suggest would never happen.

BSD isn't GPL. Simple as that.

Secondly, even if Microsoft decided to base their OS on linux, were it feasible, or BSD .... who would buy it? They'd be admitting that unix was better, and basically make their operating system linux + wine.

This only worked for Apple because Apple has culture around their stuff, so people actually use OS X, even though it's based on BSD. Also, because it's **based** on BSD; they've made so many changes to it, it's ridiculous, and a good portion of their improvements and fixes were committed back into upstream. No one shakes their fists at Apple over it because OS X has been nothing but good for FreeBSD; the same wouldn't occur with Microsoft.

---

### Post by kuja on 2006-11-04
> **shining said:**
> Isn't that the main difference between GPL and the BSD license?
BSD License: Anyone may copy/use/redistribute the source, be they proprietary or be they free.
GPL: Source may be copied/used/redistributed only as part of free software projects which are distributed under the same terms.

---

### Post by Iandefor on 2006-11-04
> **MedivhX said:**
> Commands come from kernel... Not from GNU utils... I think... Nope. 'Commands' are just binaries laying about, and the vast majority of the ones in Linux-based operating systems are straight GNU utilities compiled against the Linux kernel. Do an ls /bin sometime.

---

### Post by Iandefor on 2006-11-04
> **lwr said:**
> Apple tell everyone they used BSD to build OS X, and it hasn't made any difference to their closed-sourceness. Not entirely sure how it all works, but what you suggest would never happen. The Darwin operating system upon which OS X is built is open-source.

[http://en.wikipedia.org/wiki/Darwin_%28operating_system%29](http://en.wikipedia.org/wiki/Darwin_%28operating_system%29)

[http://en.wikipedia.org/wiki/XNU](http://en.wikipedia.org/wiki/XNU)

---

### Post by Anthem on 2006-11-07
There's nothing illegal about building a proprietary desktop on a GPL kernel.  They could do that with no (legal) problem.

But they won't.  It would be utterly stupid on a lot of levels.  There's absolutely no reason for them to do it, especially after spending a lot of time and effort re-writing their own kernel.

---

### Post by EdThaSlayer on 2006-11-07
I don't think Microsoft would do something like this.Why would you use the tool of your enemy?Why not mix that tool with yours to create a superior tool? I think that Microsoft may have borrowed little bits and pieces and combined it with their own to speed up development of their kernel.

---

### Post by Anthem on 2006-11-07
> **EdThaSlayer said:**
> I think that Microsoft may have borrowed little bits and pieces and combined it with their own to speed up development of their kernel.
What pieces?  And where's your evidence?

I dislike Microsoft as much as anybody, but there's no reason for them to do that.

---

### Post by Kimm on 2006-11-07
> **Iandefor said:**
> The Darwin operating system upon which OS X is built is open-source.

Not any longer, as far as I know :/

---

### Post by DoctorMO on 2006-11-07
Windows is well known for using a really old version of the bsd tcp/ip stack way back in windows 95. they wouldn't use any of the newer versions though and it got them into trouble.

They've been using bsd code here and there but they wouldn't touch gpl code.

---

### Post by mips on 2006-11-07
> **Anthem said:**
> What pieces?  And where's your evidence?

I dislike Microsoft as much as anybody, but there's no reason for them to do that.

As far as i know they took the tcp/ip stack from bsd years ago.

---

### Post by dca on 2006-11-07
The only things I noticed, Vista is switching to a more super-user admin account w/ single user(s) a la Linux - which has been doing this for years...  There is no difference in the Windows kernel than that from XP except for the added ability to handle 3D desktops and other crap (which again has been in Linux for quite a while).  There's no difference in its command line interface which has been nothing more than a DOS emulator (not link to kernel or anything) since Win2k...
 
 
Who knows, if they ever got rid of that dreaded Registry (which of course Windows couldn't function w/o it), I might be more supportive or even positive to a new Windows release.

---

### Post by kuja on 2006-11-07
After stopping to think for a minute, I've come up with yet another reason why this would be more or less impossible. Keep in mind that the Windows kernels include the entire GUI in the kernel.

---

### Post by prizrak on 2006-11-07
> 
Who knows, if they ever got rid of that dreaded Registry (which of course Windows couldn't function w/o it), I might be more supportive or even positive to a new Windows release.
They are trying to replace the registry with XML config files. Kinda combining the strenghts of both I guess.
> After stopping to think for a minute, I've come up with yet another reason why this would be more or less impossible. Keep in mind that the Windows kernels include the entire GUI in the kernel.
NT is a modified microkernel, it does not include the entire GUI it includes an interface to it. It's even more of a microkernel in Vista actually with audio running in user space. FYI Linux is a monolithic kernel (which is why driver installation is a nightmare) and is quite a bit larger than the NT one.
> As far as i know they took the tcp/ip stack from bsd years ago.
You are correct, sir! It's not in Vista though, it uses a new stack MS created.

Windows would not ever be based on a Linux kernel. 
1) Basing the rest of the OS on a different kernel would mean redoing the entire API to work with Linux. It would also require their own X server or a new GUI shell that would work with the Linux kernel. If they were to try and hide the kernel as part of their OS (as opposed to just running on top like Gnome/KDE) they would have to rewrite so much of it they might as well just go with a new one. 
2) Linux based Windows would enable ALL other Linux distributions to use Windows software and drivers. What would be the point of Windows then? 
3) Legal risks would be huge, if it were discovered (and it is quite easy w/o source code) that MS modifyed the Linux kernel and made it closed they would get sued by just about every agency in the world. Not to mention that if they did openly adopt the Linux kernel MS would have to defend every little piece of code in their software to make sure it doesn't violate the GPL.
4) Hidden API's wouldn't fly in Linux. MS's own software runs quite a bit better then 3rd party because it uses undocumented API functions. Impossible using Linux. 
5) While the Linux kernel is nice it's a very small part of the OS. There is alot to say about all the other stuff that comes with a Linux distribution. 
6) NT kernel is actually pretty good and stable, the problems come from other things such as the registry and IE. 
7) Last but not least! If MS wanted to adopt a different kernel and thought that the NT architecture is broken they would do what Apple did. They would take some flavor of BSD, modify it to fit their needs and release a 100% legal OS based on a free one. 

P.S. NT family is actually POSIX compliant.

---

