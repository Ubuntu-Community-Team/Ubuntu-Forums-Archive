---
title: "Ubuntu Studio RT have PAE?"
date: 2009-10-31
forum: Ubuntu Studio
---

### Post by Jestersage on 2009-10-31
Does the 32-bit RT Kernel of Ubuntu Studio have PAE? If not, how do i add the PAE onto it?

---

### Post by Stochastic on 2009-10-31
I don't believe it does, as the RT patches for the linux-rt package in ubuntu (the one used in Ubuntu Studio) are applied to the generic kernel.  I found this info on the Ubuntu 9.10 release notes > [Non-eXecutable (NX) memory protection]("https://wiki.ubuntu.com/Security/Features#Non-Exec%20Memory"), also known as eXecute-Disable (XD), has always been available in Ubuntu for any systems that had the hardware to support it and ran the 64-bit kernel or the 32-bit server kernel. The 32-bit PAE desktop kernel (linux-image-generic-pae) now also provides the PAE mode needed for hardware with the NX CPU feature.

For systems that lack NX hardware, the 32-bit kernels now provide an approximation of the NX CPU feature via software emulation that can help block many exploits an attacker might run from stack or heap memory.

Which suggests that a separate kernel is used for PAE on 32-bit systems.  One could go about mixing these kernels if they were crazy enough to try, buy manually applying [the RT patch from rt.wiki.kernel.org]("http://rt.wiki.kernel.org/index.php/Main_Page") to the supplied linux-image-generic-pae kernel  OR by applying a PAE patch to the supplied RT kernel.

Keep in mind this thread is the first time I've heard of PAE (that I can recall) so my knowledge is based purely on the RT kernel development process and google search results on PAE.  TAKE MY ADVICE WITH A GIANT ROCK OF SALT.  I have no idea if any of this is actually possible, or if it's already compiled by default without me being aware of it.

---

### Post by trulan on 2009-10-31
The only audio-oriented linux distro with a PAE real time kernel I have heard of is AVLinux, put out by a guy called GMaq and heavily favored by some users on the Ardour forums.  I have tested it a bit (not the PAE kernel as I only have 2gigs ram) but I liked Ubuntu Studio better - just personal preferences, nothing major wrong with it.

---

### Post by AutoStatic on 2009-10-31
> **Jestersage said:**
> Does the 32-bit RT Kernel of Ubuntu Studio have PAE? If not, how do i add the PAE onto it?Hello Jestersage, Ubuntu Studio does not have a PAE & RT kernel. If you want such a kernel you have to compile it yourself. If your machine is 64-bit I'd suggest trying the 64-bit version of Ubuntu Studio.

---

### Post by trulan on 2009-10-31
Here's a link for AVLinux, if you want to test his PAE kernel.  Unlike Ubuntu Studio, this will actually boot as a live CD.
[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

---

### Post by Jestersage on 2009-10-31
> **Stochastic said:**
> I don't believe it does, as the RT patches for the linux-rt package in ubuntu (the one used in Ubuntu Studio) are applied to the generic kernel.  I found this info on the Ubuntu 9.10 release notes 

Which suggests that a separate kernel is used for PAE on 32-bit systems.  One could go about mixing these kernels if they were crazy enough to try, buy manually applying [the RT patch from rt.wiki.kernel.org]("http://rt.wiki.kernel.org/index.php/Main_Page") to the supplied linux-image-generic-pae kernel  OR by applying a PAE patch to the supplied RT kernel.

Keep in mind this thread is the first time I've heard of PAE (that I can recall) so my knowledge is based purely on the RT kernel development process and google search results on PAE.  TAKE MY ADVICE WITH A GIANT ROCK OF SALT.  I have no idea if any of this is actually possible, or if it's already compiled by default without me being aware of it.

Thanks. I will do some experiment.

If I managed to get a RT+PAE Ubuntu Kernel going, what do I need to do to get in submit to the repo?

---

### Post by AutoStatic on 2009-11-01
Then you have to build it as an official Ubuntu package and have it gpg signed.

---

