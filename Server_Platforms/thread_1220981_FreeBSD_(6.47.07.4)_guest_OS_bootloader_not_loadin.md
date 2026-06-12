---
title: "FreeBSD (6.4/7.0/7.4) guest OS bootloader not loading in KVM."
date: 2009-07-23
forum: Server Platforms
---

### Post by Daniel Franke on 2009-07-23
Hey all,

I've been tasked with installing a KVM machine for a customer. As this is the first time I've worked with KVM I'm very impressed with the ease of use.

My problem comes with me wanting to install FreeBSD as a guest in KVM. The installer works fine but as soon as I start the VM after the installation, the bootloader hangs, sometimes showing one character and other times it doesn't show anything. Is this a known problem? Are there any workarounds. Is there any place I can check for debug logs.

I use libvert to install and manage my VMs and I installed my VM like this:
```

# virt-install --connect qemu:///system -n freebsd64test -r 1024 -f /data/virtual_machines/freebsd64test.qcow2 -s 10 -c 6.4-RELEASE-amd64-disc1.iso --vnc --noautoconsole --os-type=unix --os-variant=freebsd6 --network=bridge:br0  --hvm

```I also tried without the --hvm flag.

The Ubuntu server is a fully up-to-date 9.04 machine.
```

Linux xen01 2.6.28-13-server #45-Ubuntu SMP Tue Jun 30 22:56:18 UTC 2009 x86_64 GNU/Linux

```Any pointers you can give me are very appreciated.

Thanks in advance,

Daniel

---

### Post by Daniel Franke on 2009-07-27
I just noticed that I forgot to add the architecture of the FreeBSD install. It's x86_64.

---

