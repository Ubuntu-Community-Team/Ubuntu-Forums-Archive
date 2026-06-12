---
title: "Error while Creating shared folders metadata via vagrant in ubuntu"
date: 2018-05-14
forum: Virtualisation
---

### Post by alnaifm on 2018-05-14
**The following error occurred while bringing the machine up:**


tuiv@ASAlnaif:~/dornet-master$ vagrant up --provider=libvirt oob-mgmt-server
Bringing machine 'oob-mgmt-server' up with 'libvirt' provider...
==> oob-mgmt-server: Uploading base box image as volume into libvirt storage...
==> oob-mgmt-server: Creating image (snapshot of base box volume).
==> oob-mgmt-server: Creating domain with the following settings...
==> oob-mgmt-server:  -- Name:              dornet-master_oob-mgmt-server
==> oob-mgmt-server:  -- Domain type:       kvm
==> oob-mgmt-server:  -- Cpus:              1
==> oob-mgmt-server:
==> oob-mgmt-server:  -- Feature:           acpi
==> oob-mgmt-server:  -- Feature:           apic
==> oob-mgmt-server:  -- Feature:           pae
==> oob-mgmt-server:  -- Memory:            512M
==> oob-mgmt-server:  -- Management MAC:
==> oob-mgmt-server:  -- Loader:
==> oob-mgmt-server:  -- Base box:          cumulus-VAGRANTSLASH-ts
==> oob-mgmt-server:  -- Storage pool:      default
==> oob-mgmt-server:  -- Image:             /var/lib/libvirt/images/dornet-master_oob-mgmt-server.img (256G)
==> oob-mgmt-server:  -- Volume Cache:      default
==> oob-mgmt-server:  -- Kernel:
==> oob-mgmt-server:  -- Initrd:
==> oob-mgmt-server:  -- Graphics Type:     vnc
==> oob-mgmt-server:  -- Graphics Port:     -1
==> oob-mgmt-server:  -- Graphics IP:       127.0.0.1
==> oob-mgmt-server:  -- Graphics Password: Not defined
==> oob-mgmt-server:  -- Video Type:        cirrus
==> oob-mgmt-server:  -- Video VRAM:        9216
==> oob-mgmt-server:  -- Sound Type:
==> oob-mgmt-server:  -- Keymap:            en-us
==> oob-mgmt-server:  -- TPM Path:
==> oob-mgmt-server:  -- INPUT:             type=mouse, bus=ps2
==> oob-mgmt-server: Creating shared folders metadata...
Error occurred while creating new network: {:iface_type=>:private_network, :netmask=>"255.255.255.0", :dhcp_enabled=>true, :forward_mode=>"nat", :virtualbox__intnet=>"1525842573_net20", :auto_config=>false, :mac=>"44:38:39:00:00:21", :protocol=>"tcp", :id=>"06ddbc42-060a-43ac-bd5c-cca38615b547"}.

---

### Post by TheFu on 2018-05-14
Using NAT and DHCP seems like a really bad idea for a system trying to allow network access to other systems.
I don't use vagrant, but I'd set a static IP and use a bridge if I were determined to do something like this inside a VM. Actually, shared storage is one of the few things I'd never use a VM to accomplish.

---

