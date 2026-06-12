---
title: "bridge interface, kvm client not getting DHCP offer"
date: 2017-01-03
forum: Virtualisation
---

### Post by jjgrinwis on 2017-01-03
Hi,

I'm playing around with some KVM setup using ubuntu 14.04.5. I've created a bridge with just one physical interface attached to it.
When I bring up a cirros kvm image attach the the bridge, it tries to get a DHCP address and an reply is entering my ethernet interface.

~$ sudo tcpdump -i eth1 | grep -i dhcp
15:28:15.708218 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 52:54:00:cf:dd:39 (oui Unknown), length 290
15:28:18.122965 IP 10.0.0.2.bootps > 10.0.0.3.bootpc: BOOTP/DHCP, Reply, length 300

But the reply never makes it to the cirros client. When we filter the vnet0, only the request is seen, no reply.
~$ sudo tcpdump -i vnet0 | grep -i dhcp
15:29:20.642181 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 52:54:00:cf:dd:39 (oui Unknown), length 290

But when we attach a static IP to the cirros eth0 interface, we can ping the DHCP server.

Is there some filtering going on somewhere that's dropping the DHCP offer?

---

### Post by ads3 on 2017-01-03
I'm not sure of any filtering, but a few questions come to mind. 
Could we see the output of "cat /etc/network/interfaces"?
Also, where are you expecting the DHCP offer to come from? Is a server also attached to the bridge? I'd like to gain a clearer understanding of your network topology.

---

### Post by jjgrinwis on 2017-01-03
The DHCP server is some external server attached to same L2 segment as eth1/br1.
br0 is receiving dhcp from some other DHCP server in separate L2 segment.

[FONT=courier new]# The primary network interface[/FONT]
[FONT=courier new]auto br0[/FONT]
[FONT=courier new]iface br0 inet dhcp[/FONT]
[FONT=courier new]   bridge_ports eth0[/FONT]
[FONT=courier new]   bridge_stp off[/FONT]
[FONT=courier new]   bridge_fd 0[/FONT]
[FONT=courier new]   bridge_maxwait 0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]auto br1[/FONT]
[FONT=courier new]iface br1 inet manual[/FONT]
[FONT=courier new]  bridge_ports eth1[/FONT]
[FONT=courier new]   bridge_stp off[/FONT]
[FONT=courier new]   bridge_fd 0[/FONT]
[FONT=courier new]   bridge_maxwait 0[/FONT]

[FONT=courier new]# brctl show[/FONT]
[FONT=courier new]bridge name     bridge id               STP enabled     interfaces[/FONT]
[FONT=courier new]br0             8000.00505684428c       no              eth0[/FONT]
[FONT=courier new]br1             8000.00505684a65c       no              eth1[/FONT]
[FONT=courier new]                                                        vnet0[/FONT]
[FONT=courier new]virbr0          8000.000000000000       yes[/FONT]



So there is nothing fancy going on here, just a one-2-one mapping between eth1 <-> br1 <-> vnet0
We're seeing DHCP responses flowing back into eth1 but they never seem to make it into vnet0.

---

### Post by Doug S on 2017-01-03
> **jjgrinwis said:**
> So there is nothing fancy going on here, just a one-2-one mapping between eth1 <-> br1 <-> vnet0
We're seeing DHCP responses flowing back into eth1 but they never seem to make it into vnet0.Perhaps I am not understanding something, but...
I would not expect to see anything on vnet0, since you are asking the vm to use the same sub-net that eth1 is on instead, via br1.

---

### Post by jjgrinwis on 2017-01-03
yes, but I'm expecting a DHCP reply. All interface are showing the DHCP request (eth1/br1/vnet0) on my KVM host via tcpdump.
Shouldn't there be a DHCP offer flowing back via vnet0 into my VM on the KVM host?

When I assign a static IP to my VM and start sending ICMP traffic from this VM, vnet0 on the KVM host is showing the ICMP traffic between the VM and some external host, that's all fine:

# tcpdump -i vnet0 | grep -i 10.0.0.5
18:09:10.381190 IP 10.0.0.2 > 10.0.0.5: ICMP echo reply, id 51459, seq 112, length 64
18:09:11.381611 IP 10.0.0.5 > 10.0.0.2: ICMP echo request, id 51459, seq 113, length 64
18:09:11.381877 IP 10.0.0.2 > 10.0.0.5: ICMP echo reply, id 51459, seq 113, length 64
18:09:12.382085 IP 10.0.0.5 > 10.0.0.2: ICMP echo request, id 51459, seq 114, length 64

It's only the external DHCP offer that's reaching the KVM host but not making it into the VM.

---

### Post by KillerKelvUK on 2017-01-03
Have you tried tcpdump from within the guest on the interface their?  I get your logic and I've no expertise to confirm or deny but looking within the guest would remove any remaining doubt about what the vnetx interfaces actually carry?

---

### Post by Doug S on 2017-01-03
O.K., I stand corrected. I do see the dhcp traffic on my vlan0.
My normal dhcp server (192.168.111.1) lease time is quite long, but for an experiment I made it 5 minutes. So, on my host i am seeing:
```
doug@s15:~$ sudo tcpdump -n -tttt -i vnet0 | grep -i dhcp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on vnet0, link-type EN10MB (Ethernet), capture size 262144 bytes
2017-01-03 10:46:26.002722 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:46:26.051795 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300
2017-01-03 10:48:44.484753 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:48:44.524467 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300

```and on the guest (192.168.111.12) I am seeing:```
doug@serv-dev:~$ sudo tcpdump -n -tttt -i ens3 | grep -i dhcp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ens3, link-type EN10MB (Ethernet), capture size 262144 bytes
2017-01-03 10:46:26.003814 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:46:26.053028 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300
2017-01-03 10:48:44.487534 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:48:44.527378 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300

```EDIT: By the way, and for unknown reasons, the above commands to not always print, so I am now using these commands instead:
```
doug@serv-dev:~$ [COLOR="#FF0000"]sudo tcpdump -n -tttt -i ens3 port 67[/COLOR]
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ens3, link-type EN10MB (Ethernet), capture size 262144 bytes
2017-01-03 10:55:51.565876 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:55:51.660766 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300
2017-01-03 10:56:57.762629 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 08:74:02:af:56:58, length 300
2017-01-03 10:58:18.780723 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:58:18.829051 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300

```
```
doug@s15:~$ [COLOR="#FF0000"]sudo tcpdump -n -tttt -i vnet0 port 67[/COLOR]
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on vnet0, link-type EN10MB (Ethernet), capture size 262144 bytes
2017-01-03 10:55:51.558225 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:55:51.652891 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300
2017-01-03 10:56:57.754013 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 08:74:02:af:56:58, length 300
2017-01-03 10:58:18.771370 IP 192.168.111.12.68 > 192.168.111.1.67: BOOTP/DHCP, Request from 52:54:00:27:1b:9e, length 300
2017-01-03 10:58:18.819519 IP 192.168.111.1.67 > 192.168.111.12.68: BOOTP/DHCP, Reply, length 300

```And this is the relevant part of the leases file:```
lease {
  interface "ens3";
  fixed-address 192.168.111.12;
  option subnet-mask 255.255.255.0;
  option routers 192.168.111.1;
  option dhcp-lease-time 300;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.111.1;
  option dhcp-server-identifier 192.168.111.1;
  option broadcast-address 192.168.111.255;
  option domain-name "smythies.com";
  renew 2 2017/01/03 19:00:31;
  rebind 2 2017/01/03 19:02:40;
  expire 2 2017/01/03 19:03:18;
}

```And this is the relevant portion of the xml vm definition file:```
    <interface type='bridge'>
      <mac address='52:54:00:27:1b:9e'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

```

---

### Post by jjgrinwis on 2017-01-03
We're running this KVM host on a vSphere test environment and I just remembered that I've seen some strange stuff before with the VMware DVS switch when testing with KVM.
Installed a new KVM host on other vSphere cluster using Cisco 1000v, all fine now. My cirros VM on (virtual) KVM server receiving DHCP offer. :)

# virt-install --name=cirros --ram=512 --vcpus=1 --disk path=/var/lib/libvirt/images/cirros-0.3.4-x86_64-disk.img,format=qcow2 --import &#8212;network bridge:br1 [FONT=Consolas]--graphics vnc,listen=0.0.0.0[/FONT]

# tcpdump -i vnet0
listening on vnet0, link-type EN10MB (Ethernet), capture size 65535 bytes
20:17:47.765197 IP 10.0.0.3.bootpc > 10.0.0.2.bootps: BOOTP/DHCP, Request from 52:54:00:9e:fd:3b (oui Unknown), length 259
20:17:47.890721 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 52:54:00:9e:fd:3b (oui Unknown), length 290
20:17:47.891291 IP 10.0.0.2 > 10.0.0.3: ICMP echo request, id 16392, seq 0, length 28
20:17:50.144367 IP 10.0.0.2.bootps > 10.0.0.3.bootpc: BOOTP/DHCP, Reply, length 300
20:17:50.147442 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 52:54:00:9e:fd:3b (oui Unknown), length 302
20:17:50.151010 IP 10.0.0.2.bootps > 10.0.0.3.bootpc: BOOTP/DHCP, Reply, length 307
20:17:55.153374 ARP, Reply 10.0.0.3 is-at 52:54:00:9e:fd:3b (oui Unknown), length 28

No idea why, but looks like the DVS is messing up the program, 1000v to the rescue. ;)

---

