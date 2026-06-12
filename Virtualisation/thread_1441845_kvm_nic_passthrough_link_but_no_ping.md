---
title: "kvm nic passthrough: link but no ping"
date: 2010-03-29
forum: Virtualisation
---

### Post by benderisgreat on 2010-03-29
Hi,

im migrating from a paravirtual xen guest with a passed through nic to kvm. I have vt-d capable hardware (q6600 on GA-EQ45M-S2 mobo)..

The nic works fine in the kvm host. I've unbound it with:
```
echo 0000:02:00.0 > /sys/bus/pci/drivers/8139too/unbind
```

i then virtualize the guest through virsh with this in the xml:
```
<hostdev mode='subsystem' type='pci' managed='yes'>
  <source>
    <address bus='0x02' slot='0x00' function='0x0' />
  <source>
</hostdev>
```

the guest sees the nic and configures fine, ethtool says link detected: yes, but ping gets no response. there seems to nothing going in or out of the nic.

If anyone has any relevant experience that would be greatly appreciated.

---

### Post by benderisgreat on 2010-04-17
it turns out that the kernel that comes with ubuntu Karmic (2.6.31-20-server) isn't configured correctly for pci-passthrough. (even though ubuntu advertises with kvm passthrough since Jaunty).

the kernel needs to be compiled with the options:

CONFIG_DMAR=y
CONFIG_INTR_REMAP=y

recompiling solved the problem.
when all is configured correctly

```
dmesg | grep -e DMAR -e IOMMU
```

should return results for both DMAR and IOMMU.
You might also need to pass intel_iommu=igfx_off as a kernel boot option if you see errors here.

sidenote:
ubuntu karmic as a guest did then pick up the nic correctly but after sometime the link died with 

"NETDEV WATCHDOG: eth0 transmit queue 0 timed out" 

error messages.
A fedora 12 guest works fine. Perhaps due to 2.6.32 kernel.
this linked helped: [http://www.mail-archive.com/kvm@vger.kernel.org/msg25120.html](http://www.mail-archive.com/kvm@vger.kernel.org/msg25120.html)

For people with the same motherboard: you need to press ctrl-F1 in the bios to access an advanced menu to allow you to enable VT-d.

---

### Post by Badmaster on 2010-09-03
```
Unable to assign device: PCI region 0 at address 0xfbefe000 has size 0x800,  which is not a multiple of 4K

```
:-(
any help?

---

