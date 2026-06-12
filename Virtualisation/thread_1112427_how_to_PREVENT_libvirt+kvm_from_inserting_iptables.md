---
title: "how to PREVENT libvirt+kvm from inserting iptables rules?"
date: 2009-03-31
forum: Virtualisation
---

### Post by el_baby on 2009-03-31
I'm using libvirt and kvm in intrepid with "vmbuilder".

I'm creating a couple of VMs inside a host that is directly connected to internet with a public routeable address. Since I only have one public address, I won't use bridging.

I'm using shorewall ([www.shorewall.net](www.shorewall.net)) to configure my iptables rules.

I intend to use DNAT to route specific ports in the host to one or other VM.

With standard masquerading, I give the VMs access to the outside world.

At first I used the 'default' network (with a different rfc1918 network)... everything was kinda working until I rebooted the host... at that point I lost connectivity between the outside world and the VMs. From inside the host I had no trouble connecting to the VMs.

If I restarted shorewall (which actually cleans all iptables rules and regenerate them according to its configuration) everything works fine. After sending a report and some debugging in the shorewall mailing list, it was clear that libvirt was adding rules to iptables.

After reading a bit ([http://libvirt.org/formatnetwork.html#examplesPrivate](http://libvirt.org/formatnetwork.html#examplesPrivate)) I created a new network called "isolated". I stopped default (and disabled its autostart), and defined and started isolated.

This is the content of isolated.xml:
```

<network>
 <name>isolated</name>
 <uuid>51cffbcc-88f5-4edc-a81c-1765c1045691</uuid>
 <bridge name='virbr%d' stp='on' forwardDelay='0' />
 <ip address='10.3.14.1' netmask='255.255.255.0'>
  <dhcp>
    <range start='10.3.14.128' end='10.3.14.254' />
  </dhcp>
 </ip>
</network>


```
I modified my VMs to use isolated rather than default, but rules keep being added to iptables when libvirt-bin is started.

Is there a way to convince libvirt not to add these rules?

TIA.

---

### Post by freemant on 2011-10-19
For the moment, there is no way to prevent libvirtd from adding those silly iptables rules (see [https://bugzilla.redhat.com/show_bug.cgi?id=433484](https://bugzilla.redhat.com/show_bug.cgi?id=433484)).

As a poor man's workaround, I've created a simple upstart config (/etc/init/fix-kvm-iptables.conf):
```

description     "Fix KVM iptables"

start on started libvirt-bin
stop on runlevel [!2345]

# delete the rule that prevents forwarding to the VM
post-start script
  # it still takes a few seconds for libvirtd to start the virtual
  # networks and make its (bad) changes to iptables, so wait.
  sleep 5s
  logger "Fixing iptables"
  iptables -D FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable
end script

```

Hope this may help some poor souls out there.

---

