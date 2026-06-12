---
title: "Cannot compile VirtualBox 4.0.6"
date: 2011-05-05
forum: Virtualisation
---

### Post by DBQ on 2011-05-05
Hi Everybody, when trying to compile the latest version of VirtualBox (4.0.6), I keep getting this error:

```

VirtualBox-4.0.6_OSE/out/linux.x86/release/obj/pciprefix.entry.o:(.prefix+0x60): error: undefined reference to '_real_mode_stack_size'

```

Please help.

---

### Post by rewyllys on 2011-05-08
This isn't an answer to your problem, but I can offer this advice: **Avoid 4.0.6**.

On my laptop, trying to upgrade from 4.0.4 to 4.0.6 destroyed my VirtualBox installation completely.  I'd stick with 4.0.4 if I were you.

---

### Post by DBQ on 2011-05-08
The upgrade worked fine for me when I used a precompiled binary (i.e. deb).

However, I need to be able to build it from source.

---

### Post by cat2005 on 2011-05-08
> **DBQ said:**
> Hi Everybody, when trying to compile the latest version of VirtualBox (4.0.6), I keep getting this error:

```

VirtualBox-4.0.6_OSE/out/linux.x86/release/obj/pciprefix.entry.o:(.prefix+0x60): error: undefined reference to '_real_mode_stack_size'

```Please help.


I use virtualbox too.  Are you trying to get it from synaptic or the actual download site?  If I remember correctly, I think I downloaded it (not the OSE version) and installed with gdebi or some such program.  Try that.

---

### Post by DBQ on 2011-05-08
I need to be able to compile it from the source -- precompiled version is not an option.

---

### Post by Perryg on 2011-05-11
[http://forums.virtualbox.org/viewtopic.php?f=31&t=35883&p=160718#p160718](http://forums.virtualbox.org/viewtopic.php?f=31&t=35883&p=160718#p160718)
Building from SVN is basically the same and has the same package requirements.  You can read here on how to build the SVN and basically leave off the last few steps, and add --disable-hardening to the ./configure statement 

[http://www.virtualbox.org/wiki/Linux%20build%20instructions](http://www.virtualbox.org/wiki/Linux%20build%20instructions) also has the instructions but the package list is way out of date.

Remove from the package list for 32-bit installs:
ia32-libs libc6-dev-i386 lib32gcc1 libstdc++6

[http://forums.virtualbox.org/viewforum.php?f=31](http://forums.virtualbox.org/viewforum.php?f=31) also shows some more build restrictions if you don't want some of the services.

---

