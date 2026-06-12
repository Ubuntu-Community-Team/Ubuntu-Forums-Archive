---
title: "Virtualization on an ARM machine?"
date: 2016-05-23
forum: Virtualisation
---

### Post by The_Forgotten_King on 2016-05-23
I have a Samsung ARM chromebook with ubuntu 16.04 armhf. Is it possible to run virtualization software, specifically for running an x86 OS?

---

### Post by TheFu on 2016-05-24
Maybe. Might try this: [https://fedoraproject.org/wiki/Architectures/ARM/HowToQemu](https://fedoraproject.org/wiki/Architectures/ARM/HowToQemu) obviously swapping the RPM/Fedora cmds for Ubuntu ones.

You may be able to use a chroot or "containers" which use the same kernel, however.  Something like crouton for x86 chromebooks.  With only 2G of RAM, it will be a less than great result.

I specifically purchase x86 Chromebooks to avoid this issue.  Both of mine have VT-x support. KVM worked on one, but it only had 2G of RAM. I haven't gotten Ubuntu loaded on the newer, 4G, chromebook in a way I'm willing to leave it.  Hummmmm.  That gives me an idea. Thanks for the question!  You might have just provided a needed workaround for me that I've been trying to solve for 5 months!

Even if you can't get that working, an alternative would be to use the chromebook to remotely access an x86 machine.  X/Windows does that out-of-the-box, or you can use ssh + VNC over the internet.  Too bad x2go hasn't been ported to ARM, that would be 2-3x faster and still use ssh.

---

### Post by gordintoronto on 2016-05-25
What you need is emulation, not virtualization.

---

### Post by MAFoElffen on 2016-05-26
You have some options.

Most run Ubuntu on a Samsung Chromebook uing Crouton. It is actually a chroot environment, where you can switch between Chromebook and Ubuntu. But a chroot is a subset of virtualization (no hypervse) and limited.

For real virtualization, you could do [KVM]("http://www.virtualopensystems.com/en/solutions/guides/kvm-on-chromebook/") or [VMware Horizon]("http://blogs.vmware.com/euc/2014/02/google-chromebook-vmware-horizon-view-windows-applications.html")

---

### Post by TheFu on 2016-05-26
[s]KVM doesn't work on non-x86 CPUs.  OP has an ARM-based Chromebook.[/s]

Wow:> 
 Linux KVM has been designed to be portable, and has proven itself in a number of architectures, like Intel VT-x, AMD SVM, PowerPC and IA64, and is now implemented for the ARM Cortex-A15 and Cortex-A7 platforms.

Thanks for pointing that out @MAFoElffen.

---

### Post by MAFoElffen on 2016-05-26
@ TheFu
I saw that and posted ARM solutions. ... Quote from the KVM link I posted:
> 
[COLOR=#000000][FONT=Verdana]For Chromebook we use as a base version the mainline 3.13 branch which also includes [/FONT][/COLOR][COLOR=#ff0000][FONT=Verdana]KVM on ARM support[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]. To download the kernel from the Virtual Open Systems repository, follow these steps:[/FONT][/COLOR]

EDIT-- 
To the OP, that doesn't mean that is *easy*, just that it is *possible*.

---

