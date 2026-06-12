---
title: "Confused about Linux kernel and GPL 3"
date: 2006-08-12
forum: The Cafe
---

### Post by Bragador on 2006-08-12
The issue is quite complex so I was hoping some of you could clarify things for me.

The GPL version 2 was really good until people started talking about DRMs and the GPL 3 is mainly about that if I understood correctly.

Since Linux (the kernel) will not move to gpl version 3, does it mean in the long term GNU/Linux is screwed ? Does it mean that if we truly want an FOSS alternative something new will come up to replace linux ?

If that's the case I find it sad since linux is jsut starting to be seen as something serious.

---

### Post by Mathiasdm on 2006-08-12
> **Bragador said:**
> The issue is quite complex so I was hoping some of you could clarify things for me.

The GPL version 2 was really good until people started talking about DRMs and the GPL 3 is mainly about that if I understood correctly.

Since Linux (the kernel) will not move to gpl version 3, does it mean in the long term GNU/Linux is screwed ? Does it mean that if we truly want an FOSS alternative something new will come up to replace linux ?

If that's the case I find it sad since linux is jsut starting to be seen as something serious.

Why would this be a problem?
This means what it means: Linux is sticking with GPL2. That doesn't cause any problems, as far as I know :)

---

### Post by Kimm on 2006-08-12
As far as I know, GPL v3 banishes DRM completely. Meaning that it would be impossible to implement in Linux (which, sadly enough, will probably be needed).

---

### Post by Kernel Sanders on 2006-08-12
My interpretation of GPL 2 vs 3 is mainly this:

_GPL 2_

Right now, the Linux code is open source, but anybody has the right to make it closed source/add DRM to it etc if they so desire. Think TiVo, TiVo uses the Linux operating system, and for that matter think mobile phone operating systems. AFAIK, all Nokia handsets use  linux?

_GPL 3_

The Linux code is open source, and it must stay open source. You do not have the right to close it off, or add DRM to it. And (I dont know what this bit means but) you have to make you private signing keys available to anyone who wants them.



Therefore, IMO, GPL 2 is less restrictive, and in fact, more free that GPL 3.

---

### Post by G Morgan on 2006-08-12
This is badly misunderstood. GPLv3 will not stop DRM being used in Linux, it will stop DRM from being used with Linux.

A program could utilise DRM within your GPLv3 Linux. What it aims to stop is TiVo-isation where only their version of Linux will work via DRM locks. It would also stop DRM being used in a program that is derived from GPLv3 code. So if I made a media player under GPLv3 and a company adopted it and added DRM they'd have to give me the ability to make my own keys. If Linux was GPLv3 it still wouldn't stop them from using a different license and running DRM.

Personally I think this is flawed. The point of the GPL is to give you access to the code. Companies can sell whatever hardware they like. They are still releasing the code and allowing you to develop your own hardware for that code. All they have said is that you can't run a modified program on their hardware. We still gain the benefits of the work they have put in.

The GPLv2 is correct currently for what it does, people just need to be more selective consumers.

---

### Post by Polygon on 2006-08-12
i read an article that linus torvalds was critizing gpl v3 and the people who are making it, for one reason or another.

---

### Post by Donshyoku on 2006-08-12
Does GPL v3 make GPL v2 obsolete or discontinued?

They way I understood it was the GPL v3 would be a newer licenese, but GPL v2 would still be in use...

---

### Post by G Morgan on 2006-08-12
> **Donshyoku said:**
> Does GPL v3 make GPL v2 obsolete or discontinued?

They way I understood it was the GPL v3 would be a newer licenese, but GPL v2 would still be in use...

A lot of GPLv2 code has been licensed under the terms of GPLv2 or any later GPL at the pleasure of the distributor. This means this can be switched to GPLv3 but people are allowed to continue under 2 licenses if they wish. The licenses will likely be incompatible so a fork would be permenant unless you could get the agreement of all the copyright holders of the post-fork code.

Some projects are specifically GPLv2 so require every single copyright holders permission to switch license. The Linux kernel is in this boat.

People can still use whichever license they want. I fancy people will still be using GPLv2 far more than v3. If GNU tried to stop the use of GPLv2 I fancy people would just write a new license or move to something else.

---

### Post by Iandefor on 2006-08-12
> ***John* said:**
> My interpretation of GPL 2 vs 3 is mainly this:

_GPL 2_

Right now, the Linux code is open source, but anybody has the right to make it closed source/add DRM to it etc if they so desire. Think TiVo, TiVo uses the Linux operating system, and for that matter think mobile phone operating systems. AFAIK, all Nokia handsets use  linux? No, not anybody can close Linux if they so desired. That's actually in direct opposition to the GPL. If the kernel developers wanted to, they could go about changing the license, but it would be damn near impossible.

> _GPL 3_

The Linux code is open source, and it must stay open source. You do not have the right to close it off, or add DRM to it. And (I dont know what this bit means but) you have to make you private signing keys available to anyone who wants them. They wouldn't force you to make your private signing keys available to anyone who wanted them. That would totally and utterly defeat the purpose of a private signing key. As I recall it, it would disallow signing as a means of copy protection.

---

### Post by prizrak on 2006-08-13
I guess I will concentrate on what TiVo did as many people might not actually know (I didn't till recently). TiVo is basically a Linux kernel with a remote driven GUI on top of it (there are other mods of course but this is simplistic for the sake of illustration). The interface is closed source and so are the drivers for certain parts of the TiVo (some parts are the same as any other computer). The TiVo OS is also signed with a hash key that precludes the user from running a modified version of the OS on the TiVo device.

---

### Post by kripkenstein on 2006-08-13
Actually I don't think there is a clear answer about the GPL3 / Linux Kernel question. We know that much of the Kernel will be staying at version 2 of the GPL, while only parts of it (that are "2 or higher") will be able to become 3 immediately. Copyright owners of other parts might also move to 3. But at least the part owned by Linus will remain at 2, it seems...

What this implies is less certain. It is a bit similar to the GPL/CDDL issue (CDDL being the open-source license used by Sun for Solaris, which is NOT compatible with the GPL). There is at least one project mixing GPL and CDDL (Nexenta, aka GNU/Solaris), and arguments about its legality were quite lengthy. The final verdict *seems* to be that this is fine.

So, I am not sure how easy it will be to create a distro containing both GPL2 and GPL3 parts, which is what the Linux community will be facing. This may or may not turn out to be a serious issue - only time will tell.

---

### Post by gorilla on 2006-08-13
I'd be happy to have protection against Trusted Computing coming to Linux.
I wouldn't be surprised if governments will want to rule it mandarory as soon as the technology is spread into most homes. 
Linux already plays an important role, I doubt one could simply rule it illegal and walk away as if nothing happened.

---

### Post by Kernel Sanders on 2006-08-13
> **Iandefor said:**
> No, not anybody can close Linux if they so desired. That's actually in direct opposition to the GPL. If the kernel developers wanted to, they could go about changing the license, but it would be damn near impossible.

 They wouldn't force you to make your private signing keys available to anyone who wanted them. That would totally and utterly defeat the purpose of a private signing key. As I recall it, it would disallow signing as a means of copy protection.

I stand corrected :)

---

