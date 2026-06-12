---
title: "Minimum memory advice needed"
date: 2013-11-23
forum: Virtualisation
---

### Post by junk.here on 2013-11-23
What is the recommended minimum amount of memory for a Ubuntu Server 12.04 VM running Samba?

---

### Post by DuckHook on 2013-11-25
My ancient NAS (first generation HP Media Vault) runs samba, nfs, lptd, USB and a stripped down web server on 64KB! That's "K" as in "Kilo", so clearly, the "requirements" *can* be tiny.

Usually though, questions such as yours belie a more complicated use-case, so if you don't mind telling us what that is, we could advise you more fully.

---

### Post by Doug S on 2013-11-25
Typically, to be able to install the VM in the first place you need to allocate 256 megabytes of memory. However, thereafter it will, typically, run on 128 Megabytes of memory.
But as DuckHook mentioned, tell us more about your specific case.

see also: [https://help.ubuntu.com/13.10/serverguide/preparing-to-install.html](https://help.ubuntu.com/13.10/serverguide/preparing-to-install.html) (and yes, I gave the link to the 13.10 version ,even though you mention 12.04. There were some edits that were not backported, but apply.)

---

### Post by junk.here on 2013-11-28
> **DuckHook said:**
> Usually though, questions such as yours belie a more complicated use-case, so if you don't mind telling us what that is, we could advise you more fully.

You're right. To provide further detail, this minimum is the amount of RAM that should remain exclusively assigned to the VM in memory overcommit scenarios.

I'd like to get this number as low as possible to enable potentialy higher VM density, but not at the cost of performance. Hopefully you guys can help me out with this delicate balancing act :)

---

### Post by DuckHook on 2013-11-28
Aha! The usual something-for-nothing motive, is it? Join the club. Most members on this forum get a kick out of driving our machinery to the edge.

Virtualization has come a-long-way-baby and the answer to your question is: it depends. VirtualBox now uses memory ballooning which is phenomenal for low-memory systems. Memory ballooning allows the VM manager to free unused memory from a VM and give it back to the host. Obviously, this is extremely bleeding edge, sensitive and more than smacks of living dangerously. But the fact is that many organizations run production boxes that host a theoretical 128 GB of VMs on 64 GB of actual RAM. I've heard of some going higher still. The rationale is obvious: most VMs do not run at anywhere near their maxed out capacity. With memory ballooning, RAM is assigned only when it is needed. It's not carved out exclusively at initialization. The process is not (and should not) be 100% efficient. That is to say, you can't just commit only what is barely required for each VM. There is overhead and there must be a significant safety factor. I don't know enough about the tricks and processes used to give you any sort of algorithm, so to answer your question, only your own experimentation can give you the real answer.

You can start by running utilities like *top* when you are exercising your VM, to see what memory/CPU/resources usage looks like. VM memory can always be adjusted after installation.

Does that sort of non-answer constitute a sufficient answer?

---

