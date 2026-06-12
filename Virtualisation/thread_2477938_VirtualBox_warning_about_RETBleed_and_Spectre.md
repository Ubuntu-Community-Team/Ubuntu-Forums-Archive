---
title: "VirtualBox warning about RETBleed and Spectre"
date: 2022-08-11
forum: Virtualisation
---

### Post by Paddy Landau on 2022-08-11
Host: Ubuntu 20.04
Guest: Ubuntu 22.04
VM: VirtualBox 6.1.36

Both host and guest are fully up to date.

Recently, when starting the guest Ubuntu 22.04, the VM has been showing a new message shortly after Grub:
> RETBleed: WARNING: Spectre v2 mitigation leaves CPU vulnerable to RETBleed attacks, data leaks possible!
What is causing this warning to suddenly show? Should I be concerned, and if so, what should I do about it?

---

### Post by oldfred on 2022-08-11
Both UEFI & kernels need to be most current versions.

Have you updated UEFI firmware to most current version vendor has available?

---

### Post by Paddy Landau on 2022-08-12
Thank you. I'm using Ubuntu 22.04 in the guest, and it's fully up-to-date, so I hope that this means that the kernel is sufficiently up-to-date.

It might be a VirtualBox problem: it's not possible to update VirtualBox's virtual UEFI system. However, I found nothing when I searched for others with this error, and I would have expected a problem like this to be reported widely.

---

### Post by ubumabo on 2022-08-12
Same issue here.
Virtual box 6.1.36 and Ubuntu 22.04 (both downloaded today).

---

### Post by Paddy Landau on 2022-08-14
I wonder if this problem is related to [this issue]("https://www.phoronix.com/news/AMD-Linux-Retbleed-STIBP-IBPB")?

---

### Post by rashed4004 on 2022-08-15
my ubuntu 22.04 guest OS was working a day ago and since yesterday i cant start it anymore as it turns itself off straight away with error - [COLOR=#000000][I]RETBleed: WARNING: Spectre v2 mitigation leaves CPU vulnerable to RETBleed attacks, data leaks possible!

what a situation![/I][/COLOR]

---

### Post by Paddy Landau on 2022-08-15
> **rashed4004 said:**
> my ubuntu 22.04 guest OS … turns itself off straight away with error - [COLOR=#000000]*RETBleed …*[/COLOR]
I think that this might be something to do with your guest specifically. I'm running Ubuntu 22.04 in VirtualBox. It's fully updated, and it still starts normally (albeit with that message during startup).

Start a new thread on this, and post the thread's link here. In that thread, post your host's OS and version, your VirtualBox version, and what happens when you try to start your Ubuntu 22.04 in Recovery Mode.

---

### Post by damnsavage on 2022-08-25
I also got the same this morning on a recent but slightly older setup. VBox Version 6.1.32 r149290, Ubuntu 20.04.4 LTS. Aside from the message it booted and works normally...

---

### Post by alberto-villar on 2022-10-10
I also got the same message from Ubuntu 16.04 / 20.04 hosts, running VBox versions 5 / 6 (respectively) and hosting Ubuntu 20.04, 22.04 and Debian 11 guests. Neither Ubuntu 16.04 nor Windows10 guests suffer from that. I'm wondering if that's related to the most recent kernels.
My VMs usually boot and work fine, but a few of them seem stuck at/after the message during installation.

---

### Post by Paddy Landau on 2022-10-10
> **alberto-villar said:**
> Neither Ubuntu 16.04 nor Windows10 guests suffer from that.
The message seems to come from the Linux kernel, not from VirtualBox itself (it appears only after I tell Grub to boot Ubuntu). That explains why Windows 10 doesn't have the message. It probably explains why Ubuntu 16.04 doesn't have the message, as that has an old kernel. (Ubuntu 16.04 is unsupported unless you use extended support, which includes security updates only.)

---

### Post by goblin-1994 on 2022-12-25
hey did you figure this issue out? I am having the same problem

---

### Post by Morbius1 on 2022-12-25
It looks like you can disable the error message but it **[COLOR="#FF0000"]may[/COLOR]** or **[COLOR="#FF0000"]may not[/COLOR]** come at a performance cost:
[https://forums.virtualbox.org/viewtopic.php?f=7&t=107103](https://forums.virtualbox.org/viewtopic.php?f=7&t=107103)

I just ignore it.

---

### Post by wjmacfarland on 2023-01-22
Disabling the error message doesn't do anything, since the issue is still there...

---

