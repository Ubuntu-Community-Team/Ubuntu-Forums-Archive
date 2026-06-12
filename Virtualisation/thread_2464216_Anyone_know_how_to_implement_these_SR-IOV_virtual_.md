---
title: "Anyone know how to implement these SR-IOV virtual function options into NetPlan"
date: 2021-06-26
forum: Virtualisation
---

### Post by paullautier on 2021-06-26
I am running KVM on Ubuntu 20.04 & using SR-IOV for an Intel x520, does anyone know how to implement these SR-IOV virtual function options into NetPlan

ip link set **enp7s0f0** vf 0 trust on
ip link set **enp7s0f0** vf 0 spoofchk off
ip link set **enp7s0f0** vf 0 vlan 3

My NetPlan config is below

[B]enp7s0f0: {}
  addresses: []
  virtual-function-count: 63
vf1:
  match:
    name: enp7s0f0v[0-62]

enp7s0f1: {}
  addresses: []
  virtual-function-count: 63
vf2:
  match:
    name: enp7s0f1v[0-62][/B]

---

### Post by MAFoElffen on 2021-06-26
> **paullautier said:**
> I am running KVM on Ubuntu 20.04 & using SR-IOV for an Intel x520, does anyone know how to implement these SR-IOV virtual function options into NetPlan

ip link set **enp7s0f0** vf 0 trust on
ip link set **enp7s0f0** vf 0 spoofchk off
ip link set **enp7s0f0** vf 0 vlan 3

My NetPlan config is below

[B]enp7s0f0: {}
  addresses: []
  virtual-function-count: 63
vf1:
  match:
    name: enp7s0f0v[0-62]

enp7s0f1: {}
  addresses: []
  virtual-function-count: 63
vf2:
  match:
    name: enp7s0f1v[0-62][/B]
 
[SIZE=2]Using these for reference, 
 - [Canonical Netplan Reference]("https://netplan.io/reference/#properties-for-device-type-ethernets%3A")
 - [Canonical Netplan Examples]("https://netplan.io/examples/")
 
Not saying this is 100%, because I see conflicts in their own examples(?), But, this "looks" right logically.
```

network:
    version: 2
    ethernets:
        eno1:
            mtu: 9000
        enp7s0f0:
            virtual-function-count  63
            link: vf1
        vf1:
            match:
                name: enp7s0f0[0-62]
            link: eno1
        enp7s0f1v:
            virtual-function-count: 63
            link: vf2
        vf2:
            match:
                name: enp7s0f1v[0-62]
            link: eno1
    vlans:
[SIZE=2]        vlan3:
            accept-ra: no
            id: 3
            link: enp7s0f0
[/SIZE]

```
I don't see anything in the NetPlan Doc's that would integrate spoofchk or trust yet... IP Link is new, so isn't going away soon. Not sure... Still looking though the docs and blueprints...[/SIZE]

EDIT: That's still the recommended way to do spoofchk and trust that I can see so far. And that to add them as persistent, is adding the ip link commands to the /etc/bash.bashrc file. That seems to be the current.

But at least in the case of "trusted" in VF's, it is being considered as a future add upstream as a proposed attribute: "vf_trusted: fields.BooleanField(default=False)"
 - [Trusted Virtual Functions]("https://specs.openstack.org/openstack/nova-specs/specs/rocky/implemented/sriov-trusted-vfs.html")
And look under "Alternatives" in:
 - [Enable spoofchk control for SR-IOV ports]("https://specs.openstack.org/openstack/nova-specs/specs/rocky/implemented/sriov-trusted-vfs.html") 

They seem to be aware of the need and talking about it, but not there yet.

---

### Post by paullautier on 2021-06-27
@MAFoElffen, Thanks for the great information, for now I will stick with using /etc/bash.bashrc file to make the options persistant. But it's good to hear there is discusssion around getting this feature added.
Thanks Again.

---

### Post by MAFoElffen on 2021-06-27
You are very welcome.

---

