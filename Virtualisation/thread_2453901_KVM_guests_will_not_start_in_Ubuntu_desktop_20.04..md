---
title: "KVM guests will not start in Ubuntu desktop 20.04.1 LTS after upgrade from 18.04 LTS"
date: 2020-11-18
forum: Virtualisation
---

### Post by call-922 on 2020-11-18
I have a Ubuntu desktop that was running 18.04 LTS up until last week when I upgraded to 20.04.1 LTS. As of the upgrade, neither of the two KVM guests that I created under 18.04 will start. One is a Windows 10 guest with spice and virtio drivers - up to the current Windows updates. The other is a CentOS 7 guest created by Red Hat Code Ready Containers that I used for Kubernetes development. The windows guest displays a GUI with a sad face saying the "device needs to restart". The CentOS guest stops with a kernel panic. I've applied all the Ubuntu updates. I'm not really even sure how to begin diagnosing this. Is it possible that VMs created by KVM on 18.04 simply aren't compatible with KVM on 20.04?

---

### Post by TheFu on 2020-11-18
Check the system log files.

---

