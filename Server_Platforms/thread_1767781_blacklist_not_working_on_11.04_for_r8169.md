---
title: "blacklist not working on 11.04 for r8169"
date: 2011-05-26
forum: Server Platforms
---

### Post by pootle42 on 2011-05-26
Trying to stop drivers for realtek nic being picked up so I can do pci passtrhough for these devices to kvm vms later.

in 10.04 and 10.10 I did this by appending to blacklist.conf as below, but in 11.04 the drivers are still being loaded.

Should I be doing this a different way?  or is blacklist misbehaving?

here's end of blacklist.conf:
<pre>
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#and the realtek nic drivers so they can be passed to pfsense
blacklist r8169
</pre>

and here's output from dmesg | grep r8169
<pre>
[    3.020900] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.020918] r8169 0000:07:00.0: PCI INT A -> GSI 46 (level, low) -> IRQ 46
[    3.020957] r8169 0000:07:00.0: setting latency timer to 64
[    3.020992] r8169 0000:07:00.0: irq 74 for MSI/MSI-X
[    3.021338] r8169 0000:07:00.0: eth0: RTL8168d/8111d at 0xffffc90000676000, 6c:62:6d:38:32:79, XID 081000c0 IRQ 74
[    3.080237] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.080263] r8169 0000:06:00.0: PCI INT A -> GSI 51 (level, low) -> IRQ 51
[    3.080301] r8169 0000:06:00.0: setting latency timer to 64
[    3.080337] r8169 0000:06:00.0: irq 76 for MSI/MSI-X
[    3.080722] r8169 0000:06:00.0: eth1: RTL8168d/8111d at 0xffffc9000067a000, 6c:62:6d:38:32:78, XID 081000c0 IRQ 76

</pre>

---

### Post by pbeesley on 2011-08-05
i'm getting this exact same thing, did you ever find a fix?

---

### Post by gustavosf on 2011-08-31
hello

i'd the same problem, but this solved:
[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

basically, you have to update driver cache after blacklisting (see '#13')

```
~$ update-initramfs -u
```

[]'s

---

