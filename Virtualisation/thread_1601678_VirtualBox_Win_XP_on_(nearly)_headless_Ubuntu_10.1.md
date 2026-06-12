---
title: "VirtualBox Win XP on (nearly) headless Ubuntu 10.10 64 bit server"
date: 2010-10-20
forum: Virtualisation
---

### Post by prshah on 2010-10-20
Hello,

I have setup an Ubuntu 10.10 64-bit server for various website hosting working (private use only).

Now I wish to setup and use a virtual Windows XP environment on the server to which I can connect using RDP from various clients.

After trawling through tons of posts, including the stickies in the virt section, I am at a loss where to begin.

I do not want a GUI on the server machine. I do not want to change it to a desktop machine, it's role is strictly that of a LAMP server+Email.

As far as I understand, I should be using KVM, but I cannot since this is a Pentium D processor that does not have Virtualization support.

My next option is Qemu (without KVM support) but apparently that is poorly supported.

So I think I need a VirtualBox headless setup. I have no problem with having to manually login (via ssh) and starting the virtual machine on demand, ie, no problem if it does not start automatically at bootup.

Can someone please confirm my thinking about VirtualBox being the solution for me? And also guide me to a step-by-step guide of sorts to get started? 

Tech level: intermediate-high.

Thank you very much in advance:

---

### Post by prshah on 2010-10-23
Bump.

Fine, I need to use VirtualBox PUEL, not virtualbox-ose. That works fine.

Any idea of the logic of including VBoxHeadless, if virtualbox-ose does not support remote display in any case?

---

