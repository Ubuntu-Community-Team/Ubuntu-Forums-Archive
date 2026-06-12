---
title: "Is it possible to access Ubuntu from Windows 10 running in Virtualbox"
date: 2021-12-05
forum: Security
---

### Post by thumper76 on 2021-12-05
I have Ubuntu 20.04 set up as my operating system and I'm running Windows 10 in Virtualbox primarily as a bait machine for scammers. I let them access Windows 10 with Teamviewer or Anydesk, etc. and enjoy watch the scams they try to pull. Most of the spammers have limited IT skills and are not a problem. However some of them seem knowledgeable. I do turn off guest additions. So is it possible that someone could access my real underlying operation system  from Windows 10 in Virtualbox?

---

### Post by TheFu on 2021-12-06
Yes.
Breaking out of a VM is a test every hypervisor has failed.  Why use a desktop tool like virtualbox when you have KVM - an enterprise tool?

---

### Post by thumper76 on 2021-12-06
So KVM is more secure than Virtualbox. Good to know. I've used both. I'm not sure if I understand the difference between a desktop tool and an enterprise one.

---

### Post by TheFu on 2021-12-06
> **thumper76 said:**
> So KVM is more secure than Virtualbox. Good to know. I've used both. I'm not sure if I understand the difference between a desktop tool and an enterprise one.

No. Did I say that?

There's no PROOF that any hypervisor is more secure than any other to my knowledge, but KVM is what all the VPS providers in the world use, it is part of the core Linux kernel and maintained by that team. It is used by enterprises like RH and Google and the best VPS providers like Linode and AWS.  Anything that any other hypervisor can do, KVM/qemu can accomplish too. I honestly believe it is the fastest hypervisor in the world today - commercial or not.  It competes with VMware's ESXi + vSphere products.

As with all things, there are trade-offs with every choice.  Virtualbox is good when ease of use without care of the license for desktop-on-desktop situations.  Virtualbox competes with the free version of VMware Player and it is good at what it does within those limitations.  Inside a business, most people like testing groups would choose VMware Workstation over virtualbox or the free "Player" offer.

Oh .. and I hear the MSFT makes some hypervisor too. Don't know much about it and I've never seen anyone actually use it in a corporate environment outside a lab deployment. It isn't free and requires using that-other-OS.

When something is broken, especially security, in virtualbox, who fixes it and make the changes available?  Hint: Oracle.
When that happens in KVM, it is the world-wide kernel development team. 

Have you read the Oracle Guest-Additions license?  KVM is GPL.

---

### Post by thumper76 on 2021-12-06
OK TheFu, I always appreciate you knowledgeable and through responses. Thanks.

---

