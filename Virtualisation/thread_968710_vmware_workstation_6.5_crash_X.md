---
title: "vmware workstation 6.5 crash X"
date: 2008-11-02
forum: Virtualisation
---

### Post by [Neurotic] on 2008-11-02
Just wondering if this is happening to anyone else.

I'm running workstation 6.5, and Ibex.

Every so often as my mouse control passes between the guest and my Ubuntu desktop, I will get a corrupt view, and X will restart.

This happen to anyone else?

---

### Post by countzyx on 2008-11-11
Someone in the VMWare community site thinks it's a problem with compiz. They provided scripts to kill and restart the offending compiz components. I'm trying it out to see if it works.

[http://communities.vmware.com/thread/177683](http://communities.vmware.com/thread/177683)

Cheers.

---

### Post by sandrea on 2008-11-12
I have been experiencing the same problem since upgrading from Hardy to Intrepid. My X-Server crashes regularly when I am using VMWare Workstation 6.5 or VMWare Server 2.0 Client (with the server running on a different machine).

I do not use compiz, so I can rule that out.

In VMWare Server the problem apparently only arises when using a Virtual Hardware Version 7 VM (Windows XP, created in Workstation 6.5), but not when using a Hardware Version 4 VM (also with XP in it).

---

### Post by [Neurotic] on 2008-11-13
I have found that by turning off the 'grab mouse' when entering and exiting the VM, the crashed happen FAR less frequently (only happened once).

I have also gotten into the habit of reinstalling the vmware .bundle whenever the kernel changes, which seems to have helped.

---

### Post by sandrea on 2008-11-14
I have also deactivated all advanced cursor features (grab when cursor enters window, ungrab when cursor leaves window, hide cursor on ungrab). I haven't hat a crash since, but I haven't been using it very long.

---

### Post by countzyx on 2008-11-19
Having an NVidia card in a laptop, I changed the drivers from the 177 release to the 173 release. I have not had the problem since, even while running compiz. So I guess the video driver choking is what's killing X...

---

