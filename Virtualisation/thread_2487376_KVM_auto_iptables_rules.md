---
title: "KVM auto iptables rules"
date: 2023-06-02
forum: Virtualisation
---

### Post by tmg2 on 2023-06-02
Hello

I have virtual machines running on Ubuntu 22.04. I suddenly saw the default iptables rules arrive this morning. These rules cut off all internet access.


How can I turn off these firewall rules? I don't know why it came on automatically. I'm not running anything like Hooks. I already have my own iptables rules. I have more NAT rules. I don't have any filter rules.


How can I prevent firewall rules from coming automatically?

Thanks.

---

### Post by TheFu on 2023-06-02
I haven't seen this.  What rules, specifically?

---

### Post by Doug S on 2023-06-02
Disclaimer: I am not an expert.

As far as I know, the automatic iptables rules are a function of xml files used in "/etc/libvirt/qemu/networks". The default file:

```
doug@s19:~/config/etc/libvirt/qemu/networks$ [COLOR="#FF0000"]sudo cat /etc/libvirt/qemu/networks/default.xml.original[/COLOR]
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh net-edit default
or other application using the libvirt API.
-->

<network>
  <name>default</name>
  <uuid>63eac749-c8fb-4998-8519-a86b31d7f576</uuid>
  <forward mode='nat'/>
  <bridge name='virbr0' stp='on' delay='0'/>
  <mac address='52:54:00:1a:fc:0a'/>
  <ip address='192.168.122.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.122.2' end='192.168.122.254'/>
    </dhcp>
  </ip>
</network>
```Would result in the required related iptables rules on the host.

My VM's are always on my main LAN and so I never create any virtual bridge and never have any default iptables rules.

```
doug@s19:~/config/etc/libvirt/qemu/networks$ [COLOR="#FF0000"]sudo cat /etc/libvirt/qemu/networks/host-bridge.xml[/COLOR]
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh net-edit host-bridge
or other application using the libvirt API.
-->

<network>
  <name>host-bridge</name>
  <uuid>d474d859-8448-4055-9fc0-bb0b6cb83c34</uuid>
  <forward mode='bridge'/>
  <bridge name='br0'/>
</network>
```

I do not understand the "suddenly appeared" part.

---

### Post by TheFu on 2023-06-02
> **Doug S said:**
>  

I do not understand the "suddenly appeared" part.

I'm thinking that someone is patching their production systems outside of maintenance windows.  Not everyone has IT operations experience and knows better than to patch when a system is needed.

---

### Post by tmg2 on 2023-06-03
This situation appeared on Ubuntu 22.04. I'm working this way on more than 5 servers and they were all installed recently. All of them had the same problem on the same day or the next day.

   - Automatically incoming iptables rules.
[https://pasteboard.co/1Rp5cJtQCi9V.png](https://pasteboard.co/1Rp5cJtQCi9V.png)

---

### Post by Doug S on 2023-06-04
Well, those are the default rules for a default installation of the programs. If I do a standard installation of the programs using:

```
$ sudo apt install qemu-kvm libvirt-daemon-system
```as per [the Ubuntu Serverguide instructions]("https://ubuntu.com/server/docs/virtualization-libvirt"), after re-boot I get:

```
doug@serv-jj:~$ sudo iptables -xvnL

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   17002 65073278 LIBVIRT_INP  all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 LIBVIRT_FWX  all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LIBVIRT_FWI  all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LIBVIRT_FWO  all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    5514   412548 LIBVIRT_OUT  all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain LIBVIRT_FWI (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  *      virbr0  0.0.0.0/0            192.168.122.0/24     ctstate RELATED,ESTABLISHED
       0        0 REJECT     all  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain LIBVIRT_FWO (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  virbr0 *       192.168.122.0/24     0.0.0.0/0
       0        0 REJECT     all  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain LIBVIRT_FWX (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  virbr0 virbr0  0.0.0.0/0            0.0.0.0/0

Chain LIBVIRT_INP (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:53
       0        0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:53
       0        0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
       0        0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:67

Chain LIBVIRT_OUT (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     udp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            udp dpt:53
       0        0 ACCEPT     tcp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            tcp dpt:53
       0        0 ACCEPT     udp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            udp dpt:68
       0        0 ACCEPT     tcp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            tcp dpt:68
```

EDIT: By the way, and based on the packet counters from your screen shot post, it seems you have one or more VM's on the 192.168.122.0/24 subnet using virbr0.

---

