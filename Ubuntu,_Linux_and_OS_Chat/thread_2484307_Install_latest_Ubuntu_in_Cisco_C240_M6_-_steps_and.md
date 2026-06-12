---
title: "Install latest Ubuntu in Cisco C240 M6 - steps and documentation"
date: 2023-02-22
forum: Ubuntu, Linux and OS Chat
---

### Post by araczek2 on 2023-02-22
Hi,
As the Subject says I am looking to install Ubuntu in a Cisco C240 M6 server and I am looking for steps and or documentation that would help me. This server
is standalone, unmanaged. I looked on the Cisco site and could only find info on installing ESXi. Can someone help me? Ty.

..Alan

---

### Post by him610 on 2023-02-24
Specifications of Cisco C240 M6?

---

### Post by grahammechanical on 2023-02-26
Have you seen the standard Ubuntu installation guide for Ubuntu Server?

[https://ubuntu.com/tutorials/install-ubuntu-server#1-overview](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)

Regards

---

### Post by TheFu on 2023-02-26
> **him610 said:**
> Specifications of Cisco C240 M6?

These are enterprise rack, networking and storage systems, all built for extremely high density deployments as part of UCS.  Basically, a 42U rack can support hundreds of virtual machines all with 10Gbps (or better) interconnections.  These systems have upto 80 cores in 2U, without all the UCS stuff.

This is not a typical server nor is it a home system.

The best answer I have is to contact your Cisco Support team for their instructions. You'll likely need a Cisco SE to help.  My training on UCS is extremely dated. We never deployed Ubuntu on it. You may be able to contact Canonical corporate for support.  These forums are mostly for home users of Ubuntu Desktop and nobody here works for Canonical.

---

