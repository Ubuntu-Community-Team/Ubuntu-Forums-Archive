---
title: "Resolution"
date: 2020-02-05
forum: System76 Support
---

### Post by capemayal on 2020-02-05
Pop-OS 19.10.  Lemur 6 - as with other distro's releases, display resolution is not remembered. Is there a solution to this?

---

### Post by CelticWarrior on 2020-02-05
Yes, there is a solution: Install the proper drivers as mentioned everywhere in System76 documentation.

You can use their PPA for that: [https://launchpad.net/~system76-dev/+archive/ubuntu/stable](https://launchpad.net/~system76-dev/+archive/ubuntu/stable)
Follow the instructions in that page especially the part about NVIDIA.

---

### Post by capemayal on 2020-02-05
> **CelticWarrior said:**
> Yes, there is a solution: Install the proper drivers as mentioned everywhere in System76 documentation.

You can use their PPA for that: [https://launchpad.net/~system76-dev/+archive/ubuntu/stable](https://launchpad.net/~system76-dev/+archive/ubuntu/stable)
Follow the instructions in that page especially the part about NVIDIA.

Already installed.

---

### Post by CelticWarrior on 2020-02-05
Please check your UEFI settings and disable Secure Boot in cased it has been enabled inadvertently like what happens when users try to install Windows in those laptops.

If already disabled then please boot Pop and open Additional Drivers. Which Nvidia driver is selected there?

---

