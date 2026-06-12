---
title: "Should I install VirtualBox guest additions?"
date: 2012-04-17
forum: Security
---

### Post by aligator12 on 2012-04-17
Hi, I have virtualbox installed and inside it I have Windows XP running which I kind of use as a guinea pig to try out potential infected programs, and I was wondering, if I install guest additions, would this somehow make my virtual box less "contained" and more likely to spread malware? Or does installing it cause no extra risk?

---

### Post by haqking on 2012-04-17
no extra risk.

Whether you need it it is upto you, its more of a want than anything.

Extra graphics related support,shared folders etc etc.

Besides if a VM is on a network or using shared folders then it is no more contained than any other node on the network.

Peace

---

### Post by Ms. Daisy on 2012-04-17
Haqking kind of alluded to this, but the XP VM isn't contained if it's networked with your LAN. What network option are you using on the guest, NAT, bridged, etc? (if you didn't know there were options, read [this]("http://www.virtualbox.org/manual/ch06.html"))

---

### Post by aligator12 on 2012-04-17
> **Ms. Daisy said:**
> Haqking kind of alluded to this, but the XP VM isn't contained if it's networked with your LAN. What network option are you using on the guest, NAT, bridged, etc? (if you didn't know there were options, read [this]("http://www.virtualbox.org/manual/ch06.html"))
I have the network connection disabled.

---

### Post by Ravi5kumar on 2012-04-19
Hey, you will get no risk unless you connect your virtual xp to the network........

---

### Post by aligator12 on 2012-04-19
Also, I have another question, I allowed it to have 3d acceleration and gave it access to the 3d graphics capability of the host, does this any less "contain" it?

Sorry about my stupidness about this stuff. :D

---

### Post by CharlesA on 2012-04-19
> **aligator12 said:**
> Also, I have another question, I allowed it to have 3d acceleration and gave it access to the 3d graphics capability of the host, does this any less "contain" it?

Sorry about my stupidness about this stuff. :D
No, it does not. If the VM doesn't have network access, it cannot be access from the network and as such effectively contained on the host.

---

