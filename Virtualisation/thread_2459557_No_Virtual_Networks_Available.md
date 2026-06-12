---
title: "No Virtual Networks Available"
date: 2021-03-21
forum: Virtualisation
---

### Post by Quarkrad on 2021-03-21
I tried using a Bridge Connection for my kvm machines but that did not work out so I want to go back to having a NAT connection for the VMs.  Problem is my virbr0 interface seems to have disappeared.  I have spent the last two days searching how to get this back, and tried reinstalling, but virbr0 is not available through virt manager. Any advice appreciated.

---

### Post by DuckHook on 2021-03-21
Try following these instructions: [https://fabianlee.org/2019/05/26/kvm-creating-a-guest-vm-on-a-nat-network/](https://fabianlee.org/2019/05/26/kvm-creating-a-guest-vm-on-a-nat-network/)

Warning: I have not tried these out. They were found via websearch and just look reasonable to me. Please take this into account when attempting your fix.

---

### Post by Quarkrad on 2021-03-22
Thank you - no luck at my level of competence unfortunately.  I have read a number of posts recently and things change, in detail,  as ubuntu moves from release to release, so it is difficult without detailed knowledge.  As this is my main machine it will be much quicker, for me, to reinstall.

---

