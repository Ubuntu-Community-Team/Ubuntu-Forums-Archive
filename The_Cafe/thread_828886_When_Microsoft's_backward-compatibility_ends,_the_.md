---
title: "When Microsoft's backward-compatibility ends, the only solution will be Wine"
date: 2008-06-14
forum: The Cafe
---

### Post by Mazza558 on 2008-06-14
Microsoft has three choices at the moment, as they're pretty much stuck:

- Keep the old NT kernel in order to preserve backwards compatibility, at the risk of bloat (Vista), and try and provide other reasons for people to upgrade (e.g from XP).

- Scrap the old NT kernel and start again, but lose pretty much all the compatibility they had before. If they do this, Wine will thrive.

- (The most likely) - create a new kernel and keep compatibility around by using virtualisation. However, this'd be slower and businesses would complain.

Could wine, in the future, become a better compatibility layer than Microsoft themselves can manage? Could we get a situation in a few years where the fastest way to run Crysis is through wine?

---

### Post by Barrucadu on 2008-06-14
Could be. I have often wondered why they keep the NT kernel - it is just a little bloated. Writing a new one from scratch, but virtualising NT would be their best bet.

---

### Post by koenn on 2008-06-14
> **Mazza558 said:**
> 
- (The most likely) - create a new kernel and keep compatibility around by using virtualisation. However, this'd be slower and businesses would complain.

- (More likely) - ... and provide compatibility by means of virtualization, emulation or other technical means.
Businesses will applaud Microsoft for maintaining compatibility which buys them time, and start the migration of "legacy" applications to the new kernel.

Wine devs are suddenly faced with a whole new Windows environment they need to emulate and know nothing about. They need to start all over again, while the projects popularity and usefulness drops to near zero as it only supports soon to be obsoleted applications

---

### Post by plun on 2008-06-14
> Contrary to some speculation, **Microsoft is not creating a new kernel for Windows 7**. Rather, we are refining the kernel architecture and componentization model introduced in Windows Vista.  While these changes will increase our engineering agility, they will not impact the user experience or reduce application or hardware compatibility. In fact, one of our design goals for Windows 7 is that it will run on the recommended hardware we specified for Windows Vista and that the applications and devices that work with Windows Vista will be compatible with Windows 7.

[http://windowsvistablog.com/blogs/windowsvista/archive/2008/05/27/communicating-windows-7.aspx](http://windowsvistablog.com/blogs/windowsvista/archive/2008/05/27/communicating-windows-7.aspx)

The Crysis challenge can only be solved if either nVidia opens their driver (not likely) or that open source devs starts to work with nVidias devs with OpenGL, after that the game industry will adopt OpenGL as a better choice the DirectX10

---

### Post by Tomatz on 2008-06-14
Doubt it.


For example you can still run the .COM file extension in xp and vista using NTVDM ([http://en.wikipedia.org/wiki/Virtual_DOS_machine](http://en.wikipedia.org/wiki/Virtual_DOS_machine)).

Windows will always keep some level of backwards compatability.

---

### Post by mister_pink on 2008-06-14
I also think it's unfair to say there's anything wrong with the NT kernel. I saw something recently posted on this forum about how tiny it actually is (I'll post it here if I find it). All the vista bloat is userspace rubbish.

---

### Post by quanumphaze on 2008-06-14
There is nothing stopping Microsoft from making their own Wine like application. After all they have the code, so it would easily be 90+% perfect API compatibility for their (hypothetical) new *NIX operating system.

This will hopefully never happen.

---

### Post by Sand &amp; Mercury on 2008-06-14
> **koenn said:**
> - (More likely) - ... and provide compatibility by means of virtualization, emulation or other technical means.
Businesses will applaud Microsoft for maintaining compatibility which buys them time, and start the migration of "legacy" applications to the new kernel.

Wine devs are suddenly faced with a whole new Windows environment they need to emulate and know nothing about. They need to start all over again, while the projects popularity and usefulness drops to near zero as it only supports soon to be obsoleted applications

> **Mazza558 said:**
> 
- (The most likely) - create a new kernel and keep compatibility around by using virtualisation. However, this'd be slower and businesses would complain.
I think the result would be a bit between these two predictions... wine would remain an option for legacy apps along with virtualisation with a new kernel. Even now, Wine isn't any good for many of the bleeding-edge apps coming out at the moment so I don't see how a new kernel to learn would (immediately) affect peoples' usage of it.

---

### Post by LaRoza on 2008-06-14
I use Linux for DOS programs (although I could use DOSBox in Windows as well, that is just masochistic)

MS likes to force upgrades, but people don't like changes. A Linux distro with Wine could become the most popular OS in the future, if MS deviates too far.

---

### Post by Dr. C on 2008-06-15
This is not something in the future but reality today. There are 32bit Windows applications that work on Ubuntu / Wine and do not work on Vista. Also 16bit Windows applications work with Wine on 64bit Ubuntu but not on 64bit Windows Vista.

Wine will not be the only version there will also be [ReactOS]("http://www.reactos.org") which uses a lot of the Wine code.

---

### Post by lisati on 2008-06-15
> **FineE said:**
> This is not something in the future but reality today. There are 32bit Windows applications that work on Ubuntu / Wine and do not work on Vista. Also 16bit Windows applications work with Wine on 64bit Ubuntu but not on 64bit Windows Vista.

Wine will not be the only version there will also be [ReactOS]("http://www.reactos.org") which uses a lot of the Wine code.
That reminds me: the old copy of MS Word I picked up refused to work on Win 98SE and promptly told me to get hold of a newer copy (of Word, that is). If memory serves correctly, there's an option in the EXE file header to specify which versions of DOS and/or Windows the file is designed for

Never mind, there's always Open office, and that saves me from blowing the dust off the old 5.25" disk drives in my cupboard and then having to mess around trying to get them usable.

---

