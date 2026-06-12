---
title: "Network auto-configuration failing using virtmanager"
date: 2011-02-24
forum: Virtualisation
---

### Post by bonzi on 2011-02-24
I'm virt-manager (kvm) to install Ubuntu. But I'm getting error message (during ubuntu installation) "Network autoconfiguration failed". Your network is probably not using DHCP protocol. Alternatively, the DHCP server maybe slow or some network hardware is not working properly.

This is the default network configuration

<network>
  <name>default</name>
  <uuid>819998eb-2892-fa3d-c6bc-b737948da18c</uuid>
  <forward mode='nat'/>
  <bridge name='virbr0' stp='on' delay='0' />
  <ip address='192.168.122.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.122.2' end='192.168.122.254' />
    </dhcp>
  </ip>
</network>


How can I fix it?

---

### Post by bonzi on 2011-02-24
Sorry it was a basic mistake. I had to add this in /etc/network/interfaces

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

---

