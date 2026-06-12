---
title: "KVM works like a CHARM!"
date: 2008-04-22
forum: Virtualisation
---

### Post by jdong on 2008-04-22
Over the weekend, I played with Xen, KVM, VirtualBox, and VMWare Server in the process of setting up a FreeBSD 7 virtual machine. And to my surprise, KVM with virt-manager really rose above all the other solutions. Way to go, Ubuntu devs, I guess I underestimated the potential of KVM...

---

### Post by -Rick- on 2008-04-22
Just being curious, but why do you like it better than vmware?

---

### Post by jdong on 2008-04-22
> **-Rick- said:**
> Just being curious, but why do you like it better than vmware?

(1) VMware added several additional kernel modules to my system configuration and also a few additional network adaptors by default. I was concerned about the security implication of this, as I doubt any of these modules have been peer-reviewed and even bridging isn't handled by the standard bridge interface available in Linux.

(2) VMWare is proprietary and we only have a free VMWare Server out of the generousity of VMWare folks. Don't get me wrong -- I applaud the free products from VMWare but I also don't know if they'll be here tomorrow or the day after, or if there's a serious bugfix/security update whether or not the free products will get the same attention to urgency as the enterprise-class versions.

(3) I had some issues with host latency under VMWare Server. If I command my FreeBSD guest to do a large compile job, even under the lowest priority setting, my host has noticeable additional latency while playing back high-def videos, gaming, and even some Compiz effects. I also noticed this effect with VirtualBox, but I did not notice this with KVM (yet).

(4) Headless reattachment on VMWare Server worked sporadically at best. Sometimes I can't close down the main window without the guest wanting to power off, other times when I open up the server console again, the reattached screen is blank. libvirt uses standard VNC that worked reliably and consistently.


EDIT:

(5) KVM and libvirt are both in main in Hardy which gives me more confidence that they will receive good support as time goes on. Unfortunately the same cannot be said about VMWare Server, which is not in Hardy Parter repos yet, and even throughout Gutsy's lifespan there were instances where the kernel modules lagged behind the Gutsy kernel updates.

---

### Post by -Rick- on 2008-04-22
Even though vmware is not open source, I think it's not going anywhere soon as they are doing pretty well in the virtualization market afaik :)

I have to agree on security though...I'm not really bothered with it, but I can see your point.

> 
(3) I had some issues with host latency under VMWare Server. If I command my FreeBSD guest to do a large compile job, even under the lowest priority setting, my host has noticeable additional latency while playing back high-def videos, gaming, and even some Compiz effects. I also noticed this effect with VirtualBox, but I did not notice this with KVM (yet).
Thats pretty cool I guess. I'm a bit spoiled with my fairly recent system, as compiling things on 1 or 2 systems is pretty doable.

So far my experiences with vmware are the best, simply because it seem to run more different OS'es than the other two. With both virtualbox and qemu/kvm I've had several OS'es not wanting to boot (even a few linux distros), but vmware seems to run everything fine (Linux, Windows, Solaris, BSD's, Syllable ...).

---

### Post by ericy on 2008-04-22
I'm also a kvm lover. vmware is nice, but I grew tired and sick of the constant failed vmtool compilation. I could always use generic drivers, but they weren't very responsive. 

kvm is improving, and has improved quite a bit. At this rate, who knows, (better, maybe?)

---

