---
title: "USB Devices in VMWare"
date: 2008-12-19
forum: Virtualisation
---

### Post by kobusven on 2008-12-19
Hi

I am using Ubuntu 8.10, and VM Ware 1.0.7 build-108231. It does give me the option in the VMWare management console, to enable USB devices, but NOTHING shows up as available devices to add it to the VM session. As there is some critical USB devices which I should be able to access (as it does not work in Linux (Sunix USB - Serial adapter)) I have to get this going, in order for me to get rid of dual boot.

Kobus

---

### Post by Dedoimedo on 2008-12-19
If I'm not mistaken, Server v2 supposts USB 2.0 and so does Workstation. Server v1.x supports only USB 1.1. So this might be part of the problem.

BTW, what filesystem are the devices formatted with? What guest OS? Did you install VMware Tools in the guest OS?

Dedoimedo

---

### Post by dcstar on 2008-12-19
> **kobusven said:**
> Hi

I am using Ubuntu 8.10, and VM Ware 1.0.7 build-108231. It does give me the option in the VMWare management console, to enable USB devices, but NOTHING shows up as available devices to add it to the VM session. As there is some critical USB devices which I should be able to access (as it does not work in Linux (Sunix USB - Serial adapter)) I have to get this going, in order for me to get rid of dual boot.

Kobus

See the FAQ at the top of this forum on setting up USB for VMWare.

---

### Post by kobusven on 2008-12-23
1. filesystem are the devices formatted with? - I am not sure but it works in Windowz.
2. What guest OS? = Windows XP 32 bit
3. Did you install VMware Tools in the guest OS? - Yes

---

