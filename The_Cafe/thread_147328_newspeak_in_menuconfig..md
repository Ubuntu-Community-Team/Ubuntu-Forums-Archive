---
title: "newspeak in menuconfig."
date: 2006-03-20
forum: The Cafe
---

### Post by Ptero-4 on 2006-03-20
Hi. I compiled a kernel some time ago on my Xubuntu partition in my "eBuntu". And I saw something in the menuconfig utility that kinda creept me out, somewhere in the menuconfig utility there's an option to compile support for TPM's (Trusted Platform modules, I made another thread about it earlier), and when I looked at that option's description  I realized that the description talked about "security device" support in the same way M$, RIAA, MPAA, etc talks about this topic. I kinda freaked out b/c that misleading definition of "security devices" is bound to be found in M$ and their friends, but I never expected to see such deceiving message in a GNU, OSS utility. And I wanted to know. Why it is there? and have anyone of you seen similar M$esque misleading messagery on menuconfig or any other GNU app?

---

### Post by Ptero-4 on 2006-03-22
Has anybody here compiled a f*ckin kernel. 'Cause what I'm talkin about is the frea*** ncurses util that you see when you compile a kernel.

---

### Post by tageiru on 2006-03-22
[QUOTE=Ptero-4]Why it is there?[/QUOTE]
It is an open source driver for a piece of hardware, thats why it is there. If you have no need for it, dont use it.

---

### Post by Stormy Eyes on 2006-03-22
[QUOTE=Ptero-4]Has anybody here compiled a f*ckin kernel. 'Cause what I'm talkin about is the frea*** ncurses util that you see when you compile a kernel.[/QUOTE]

Yes, I've compiled the kernel. Yes, I know that Linus allows DRM support in the kernel; I think it's why the kernel will still be distributed under version 2 of the GPL, since v3 forbids DRM support. If you don't want DRM support in your kernel, don't compile it. What's the big f---ing deal?

---

### Post by Ptero-4 on 2006-03-23
Tageiru and Stormy. I know it's an OSS tool, and my problem isn't that option, is it's descriptive text. What I meant to ask is Why the description message for that option is written in the way M$ would write such options to keep ppl ignorant (Support for security devices) and not in the clarifying way we would do it (Support for hardware restrictions management).

---

### Post by Brunellus on 2006-03-23
...so talk to the relevant maintainers and/or hurl bombs in their direction.  

The sort of person who is compiling a kernel is not likely to be the sort of person who is as ignorant as you believe all of us to be.

---

### Post by briancurtin on 2006-03-23
[QUOTE=Ptero-4]Has anybody here compiled a f*ckin kernel. 'Cause what I'm talkin about is the frea*** ncurses util that you see when you compile a kernel.[/QUOTE]
calm down.

---

### Post by GeneralZod on 2006-03-24
This is roughly similar to complaining that a kitchen knife is not advertised as a "Human Stabbing Weapon".  The TPM *is* a security device - it's hardware can be conscripted to keep your data private even if, say, someone has physical access to your machine.  The fact that, like a kitchen knife, it can be used for nefarious purposes is irrelevant, and it would be unprofessional of the maintainer to write some political screed in the description.

---

### Post by tageiru on 2006-03-24
[QUOTE=Ptero-4]Tageiru and Stormy. I know it's an OSS tool, and my problem isn't that option, is it's descriptive text. What I meant to ask is Why the description message for that option is written in the way M$ would write such options to keep ppl ignorant (Support for security devices) and not in the clarifying way we would do it (Support for hardware restrictions management).[/QUOTE]
Well the intended use of the device is to increase the security and integrity of a system, so what else would they call it?

---

