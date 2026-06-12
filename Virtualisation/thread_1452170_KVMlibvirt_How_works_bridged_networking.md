---
title: "KVM/libvirt: How works bridged networking?"
date: 2010-04-11
forum: Virtualisation
---

### Post by Toastie0815 on 2010-04-11
Hi!

I've successfully installed a *kvm* host on *Ubuntu 9.1* managed by *libvirt*. Network is bridged using *br0*. *eth0* is part of the bridge as physical network interface. My guest network configuration looks like follow:

```

    <interface type='bridge'>
      <mac address='52:54:00:86:3f:64'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='pcnet'/>
    </interface>

```When starting the guest (with virsh) a new network interface *vnet0* appears and gets attached to the bridge *br0*.

Unfortunately the whole setup is not 100% clear to me. May someone can explain or reference documentation answering following questions?

[LIST=1]
[*]How is the vnet0 interface created and how is it connected to the virtual interface within the guest? (vnet0 and the guest interface have different mac addresses. There is no /dev/tun0 or dev/tap0)
[*]Is there a bullet-proof way to identify packages from a specific guest with iptabes running on the host machine. (MAC and IP can be manipulated in the guest :evil:.)
[/LIST]

Thanks in advance for your help!

---

