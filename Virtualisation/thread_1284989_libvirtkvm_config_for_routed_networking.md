---
title: "libvirt/kvm config for routed networking"
date: 2009-10-07
forum: Virtualisation
---

### Post by willwagner on 2009-10-07
Hello,

I am trying to setup a kvm/libvirt VM on my host. My host has a public static IP and my VM also has a public static IP. Unfortunately I can not use bridged networking as the hosting provider has configured their switch to only accept packets from the MAC address of the host.

I want to be able to setup my VM so it has the public static IP and it appears to be directly connected to the net. I believe I can do this with routed networking.

I have created a new routed network:
<network>
  <name>routed-net</name>
  <bridge name="routed%d" />
  <forward mode="route" dev="eth0"/>
  <ip address="10.255.255.2" netmask="255.255.255.255">
  </ip>
</network>

and in my vm's config I have:
    <interface type='user'>
      <source network='routed-net'/>
      <mac address='54:52:00:47:a8:38'/>
      <model type='virtio'/>
    </interface>

Will this mean that the VM is placed on the routed network?

Then I just need to add suitable routing rules on the host and everything should work?

Is there a way to get libvirt to add the rules automatically when the VM starts. i have previously used Xen where you are able to specify what the IP address of the VM is and entries are automatically added to iptables. Is there similar syntax for libvirt and if so what is it? If not how do you recommend adding the routing rules?

Thanks.

Will.

---

