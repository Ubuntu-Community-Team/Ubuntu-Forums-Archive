---
title: "What is the difference between cloning and snapshots if any?"
date: 2014-11-26
forum: Virtualisation
---

### Post by seabird22 on 2014-11-26
Hello to all,I am using qemu/kvm with virtual machine manager 0.95.0  powered by libvirt on Ubuntu 14.04LTS to host OpenBSD 5.6. Virtual machine has an option for cloning, however, not for taking snapshots. I have another pack age 'virsh' installed that, according to the man page, it can take snapshots. I want to know what the difference is between cloning and taking snapshots if any? thank-you

---

### Post by haqking on 2014-11-26
This is Vmware specific but explains it just the same.

[https://www.packtpub.com/books/content/cloning-and-snapshots-vmware-workstation](https://www.packtpub.com/books/content/cloning-and-snapshots-vmware-workstation)

Basically you would snapshot say before or after an update or change and is useful for a specific machine or state.

A clone can be used to quickly create a copy of that machine that you could then alter slightly such as interfaces, IP addresses, MAC addresses etc without having to re-install from scratch for a number of machines.

---

### Post by seabird22 on 2014-11-26
> **haqking said:**
> This is Vmware specific but explains it just the same.[https://www.packtpub.com/books/content/cloning-and-snapshots-vmware-workstation](https://www.packtpub.com/books/content/cloning-and-snapshots-vmware-workstation)Basically you would snapshot say before or after an update or change and is useful for a specific machine or state.A clone can be used to quickly create a copy of that machine that you could then alter slightly such as interfaces, IP addresses, MAC addresses etc without having to re-install from scratch for a number of machines.Thank-You!

---

### Post by haqking on 2014-11-26
No problem, very welcome.

Remember to mark thread as solved if the answer is sufficient though others will probably post too.

---

### Post by seabird22 on 2014-11-26
One more thing, do you know if their is a virtual machine manager that supports snapshots? The version I am using which I mention in my initial post does not support it. thanks again...

UPDATE

Don't need a reply to this since I switched to vmware.

---

