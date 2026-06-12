---
title: "VMWare Tools installation (Fusion on Mac)"
date: 2008-02-12
forum: Virtualisation
---

### Post by rickbsgu on 2008-02-12
Transferred over a Parallels Ubuntu image to a VMWare Fusion image to try out.

When installing the tools, the installer prompted me for a lot of kernel builds to tune various aspects, but wasn´t able to, because I don´t have the kernel source on board.  It went on, I rebooted, and it seems to be running ok.

Two questions:[LIST]
[*]Is it worth doing the kernel patches?  I´m doing 3d development, using this to test the unix environment.  I wouldn´t mind wringing all the performance out I can get.
[*]If so, where do I get the kernel sources?  I´m not seeing anything apparent on the Ubuntu site.  Debian?[/LIST]Other than these questions, it seems to be much more solid under *Fusion* than *Parallels* - my inclination is to continue with *Fusion.*

Thanks,
rickb

---

### Post by fjgaude on 2008-02-12
Gosh, are you looking for Mac kernels or Ubuntu?

Use Synaptic to find the kernels you need if it is Ubuntu. Just do a Search for "kernel" and scroll down to see the ones that are being used.

What hardware are you using?

---

### Post by rickbsgu on 2008-02-12
> **fjgaude said:**
> Gosh, are you looking for Mac kernels or Ubuntu?]

It's (the VMWare tools installation) looking for linux (Ubuntu) kernel sources.  It wants to patch the kernel.

> 
Use Synaptic to find the kernels you need if it is Ubuntu. Just do a Search for "kernel" and scroll down to see the ones that are being used.

Synaptic doesn't seem to provide a "kernel source" package, which is what I'm looking for.

[QUOTE]
What hardware are you using?

This is on a Mac white powerbook, 2ghz duo/2gb/250gb.  Under VMWare Fusion.

rickb

---

### Post by fjgaude on 2008-02-12
Well, I don't understand why you would need the kernel source but likely you can get it through Synaptic by going to the Settings/Repositories and clicking on Source code.

I'm sure I don't have any source code on my machines, only the headers, vmlinux, and the like for the version installed.

Good luck.

---

### Post by fjgaude on 2008-02-12
Well, I don't understand why you would need the kernel source but likely you can get it through Synaptic by going to the Settings/Repositories and clicking on Source code.

I'm sure I don't have any source code on my machines, only the headers, vmlinux, and the like for the version installed.

Good luck.

---

### Post by rickbsgu on 2008-02-14
> **fjgaude said:**
> Well, I don't understand why you would need the kernel source but likely you can get it through Synaptic by going to the Settings/Repositories and clicking on Source code.

No, that just allows downloading source for whatever packages you want.

Found it, though - it's called 'kernel-package' and it includes kernel sources and a utility for building custom kernels.

rickb

---

### Post by fjgaude on 2008-02-14
Great, we all learn something new each day.

---

### Post by rickbsgu on 2008-02-15
Ok, here's the final answer (this came to a head when Ubuntu upgraded and I lost my network driver (grr)-


What VMWare tools are looking for is the kernel *headers* so it can create new drivers.  The headers it needs are here:

 [INDENT]/usr/src/linux-headers-2.6.22-14-generic/arch/i386[/INDENT]

Unfortunately, vmtools configure looks for them here:

 [INDENT]/usr/src/linux-headers-2.6.22-14-generic/arch/linux[/INDENT]

By creating a link from i386 to linux under the arch/ directory, the configure works and the modules are built.

And VMWare can do it's thing more efficiently.

And I've got my network driver back.

rickb

---

### Post by fjgaude on 2008-02-15
Very interesting, and thanks for the info. I've never had such an issue with using Ubuntu as my host and Windows as guest.

---

### Post by Mach1US on 2008-02-15
I have just installed VMWARE server by running :
```
# sudo aptitude install vmware-server
# sudo aptitude install vmware-tools-kernel-modules
```
Everything looked OK until i tried to start previously created VM-host-OS which works fine when i use XP as a host but does not turn on when i try it on Gutsy.
I get no error messages so i don't even know where to start looking, do i need to install additional stuff ?

---

### Post by Alfdog on 2008-03-09
> **rickbsgu said:**
> Ok, here's the final answer (this came to a head when Ubuntu upgraded and I lost my network driver (grr)-


What VMWare tools are looking for is the kernel *headers* so it can create new drivers.  The headers it needs are here:

 [INDENT]/usr/src/linux-headers-2.6.22-14-generic/arch/i386[/INDENT]

Unfortunately, vmtools configure looks for them here:

 [INDENT]/usr/src/linux-headers-2.6.22-14-generic/arch/linux[/INDENT]

By creating a link from i386 to linux under the arch/ directory, the configure works and the modules are built.

And VMWare can do it's thing more efficiently.

And I've got my network driver back.

rickb

I'm also having the network problem with ubuntu under fusion, could you please explain your solution in more detail.  I'm still quite a novice at Linux

---

### Post by Belathor on 2008-03-29
I would like to know more about your solution as well. I swear the directory you say the headers are found in doesn't exist. I've never bothered compiling my own kernel so I have never bothered looking for the header files on Ubuntu. The closest thing I see to i386 is 'x86' but that is a directory. If x86 is the new name for i386, then I will just create a link. Here are the contents of my /usr/src/linux-headers-2.6.24-12-generic/arch directory:
 
```
alpha  blackfin  h8300  m68k       parisc   s390  sparc    v850
arm    cris      ia64   m68knommu  powerpc  sh    sparc64  x86
avr32  frv       m32r   mips       ppc      sh64  um       xtensa

```

---

