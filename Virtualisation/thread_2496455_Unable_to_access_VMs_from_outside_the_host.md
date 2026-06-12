---
title: "Unable to access VMs from outside the host"
date: 2024-03-28
forum: Virtualisation
---

### Post by harshl on 2024-03-28
Hey all,

I have an issue that is driving me nuts and I think I am getting outside of my ability to properly fix it. I have an issue on an Ubuntu 22.04.4 server doing virtualization for a GNS3 environment. I don't believe that it being a GNS3 environment is really relevant except to say their guide is how I arrived where I am at. I did a base install of Ubuntu 22.04.4 and then followed this guide with a couple of modifications along the way:
[https://docs.gns3.com/docs/getting-started/installation/linux/](https://docs.gns3.com/docs/getting-started/installation/linux/) (top Ubuntu section)
The only thing I had to do different from that guide was install the GPG keys a little different since the method they reference has been deprecated, but that all went fine.

So with that context, here is the root issue. I am unable to ping into VMs on the Ubuntu host from anywhere outside of the Ubuntu host itself. I know the issue is on the host itself, because if I add the following to IPTables, it works, but I don't know how to make this stick through a reboot.

Again, in an attempt to provide clarity, the only thing I need to do to obtain my desired outcome is add this one single line below (iptables -I LIBVIRT_FWI 2 -j ACCEPT). Nothing else is broken, and nothing else is needed. I just need to know how to make that entry persist through a reboot.

iptables -I LIBVIRT_FWI 2 -j ACCEPT

According to this: [https://libvirt.org/firewall.html](https://libvirt.org/firewall.html) and this: [https://libvirt.org/formatnwfilter.html](https://libvirt.org/formatnwfilter.html), there are other firewall auto configurations at play here that may be overriding that?

Regarding the two libvirt articles above, I did some looking and it looks like there are already rules to allow this traffic, but it isn't working. I'm stumped.
#virsh nwfilter-list

```
 UUID                                   Name
-----------------------------------------------------------------
 85246ab3-9fb5-4806-a5d9-427a6ce49cbd   allow-arp
 6484405f-6207-463b-a446-17653cab27b1   allow-dhcp
 53f0ebb9-eed3-4d83-aa27-1d968be5ee2a   allow-dhcp-server
 80f3302a-6759-4fdf-a4f7-031f74d4f4a4   allow-dhcpv6
 80953f56-390e-4acf-9ab6-55d59f8ad44c   allow-dhcpv6-server
 cb585ff6-5b65-4e88-82bc-1d0624f9531a   allow-incoming-ipv4
 3f72c727-912d-4d2d-925e-a99bcfd6d388   allow-incoming-ipv6
 037901c9-ec86-4510-b093-7d71cd3c7a39   allow-ipv4
 5109e791-64a9-4fa8-a45a-b80b08b619af   allow-ipv6
 627fd14f-28c0-4748-88f0-29e62b6627b5   clean-traffic
 534467e9-a32c-407b-ae8d-facccaf8866c   clean-traffic-gateway
 c573809e-bb84-4272-b9ff-2cdaaa028a33   no-arp-ip-spoofing
 7b1b5650-c72b-4fc3-a6d6-a883fa98f5ea   no-arp-mac-spoofing
 51966ed9-4e22-4c58-bbce-36756977c779   no-arp-spoofing
 403501b0-2f61-4fa9-807f-79005da9597f   no-ip-multicast
 1898b7ce-5710-41ef-8e22-168fd38e530e   no-ip-spoofing
 0496a176-5f5e-4a84-aa30-fa868029ae7c   no-ipv6-multicast
 37c749c6-8df2-4791-a9e9-eddc17487f1f   no-ipv6-spoofing
 3b75ae93-4192-4ba5-b165-bcee0b2403e6   no-mac-broadcast
 04e72613-0335-4e7c-89bd-f3dbe45c6b46   no-mac-spoofing
 49f53b92-2463-4388-873d-47ed6f575020   no-other-l2-traffic
 654184aa-c9af-4981-ac73-f8641e0b4e24   no-other-rarp-traffic
 9ddff19c-3a88-4676-808d-b623fee24a23   qemu-announce-self
 43f355c1-bda5-4494-b925-1101c02ee636   qemu-announce-self-rarp
```

and 

#cat /etc/libvirt/nwfilter/allow-incoming-ipv4.xml

```
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh nwfilter-edit allow-incoming-ipv4
or other application using the libvirt API.
-->

<filter name='allow-incoming-ipv4' chain='ipv4' priority='-700'>
  <uuid>cb585ff6-5b65-4e88-82bc-1d0624f9531a</uuid>
  <rule action='accept' direction='in' priority='500'/>
</filter>
```

#ufw status

```
Status: inactive
```

Any guidance on how to resolve this sure would be appreciated, thanks!

---

### Post by Tadaen_Sylvermane on 2024-03-28
You can write a script fired by a systemd service to configure iptables on boot. I know there is a better way but this is what I ended up doing. Easier for me to mess with a script than anything else.

My script for reference. [https://gitlab.com/jmgibson1981/homescripts/-/blob/master/router/homerouter.sh?ref_type=heads](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/router/homerouter.sh?ref_type=heads)

This was fired at boot via systemd. I never did mess with the iptables save stuff. Supposedly one should be using nftables instead but I am and was to lazy to change it. As I don't use that script anymore it's on my git just for reference.

---

### Post by TheFu on 2024-03-28
If you want a VM to be on the same subnet as the host, use a network bridge. There are examples for how to set up a bridge on an Ubuntu Server in the netplan.io/examples website.  Inside the VM, networking is all the same, but you'll need to connect the bridge to the VM networking inside libvirt.  I usually do that using virt-manager into the VM-host from my workstation.

I don't know what GNS is.

---

### Post by harshl on 2024-03-29
Thank you, Tadaen_Sylvermane, I think I will likely go that direction for now, the firewalling in libvirt is a mess.

Thank you for the reference, I really appreciate it! My script will be much simpler as I literally just need to add one IPTables line to make it work as desired. :)

---

### Post by harshl on 2024-03-29
> **TheFu said:**
> If you want a VM to be on the same subnet as the host, use a network bridge. There are examples for how to set up a bridge on an Ubuntu Server in the netplan.io/examples website.  Inside the VM, networking is all the same, but you'll need to connect the bridge to the VM networking inside libvirt.  I usually do that using virt-manager into the VM-host from my workstation.

I don't know what GNS is.

Thanks TheFu, but all of that is already working fine. Per my OP, I need only add one IPTables line to get the desired outcome. I just can't figure out how to make that line persist through reboots, so for now, I will just script the entry of the line after bootup.

Thanks.

---

### Post by TheFu on 2024-03-29
> **harshl said:**
> Thanks TheFu, but all of that is already working fine. Per my OP, I need only add one IPTables line to get the desired outcome. I just can't figure out how to make that line persist through reboots, so for now, I will just script the entry of the line after bootup.

Thanks.

I don't have any firewall rules on my VM hosts specific to the VMs.  Any traffic for the IP is sent to the VM IP where any firewalling desired happens, just like with any other physical host.  

But there are 50,000 different solutions.  Perhaps I'm just lazy.  OTOH, I do passthru a NIC to internet-facing VMs, so the host doesn't actually have access to that traffic, unless it is on the LAN with the host, which is what I thought you wanted.

---

### Post by MAFoElffen on 2024-03-31
I do Network bridges on my KVM Hosts. It is not that hard, and it is the accepted answer for that. I find that easier than trying to make IP Tables work. I really can't understand the reasoning of thinking the opposite on that.

There is a third way that most people do not think of:
If your remote KVM host is on the same net as the local machine, and the local machine also has KVM installed with Network Manager, then you can connect to remote KVM host's VM through qemu+ssh://UserName@IP_Address/system...

---

### Post by TheFu on 2024-03-31
> **MAFoElffen said:**
> I do Network bridges on my KVM Hosts. It is not that hard, and it is the accepted answer for that. I find that easier than trying to make IP Tables work. I really can't understand the reasoning of thinking the opposite on that.
Me neither.  Bridges have been the recommended solution since at least 2008.

> **MAFoElffen said:**
> 
There is a third way that most people do not think of:
If your remote LVM host is on the same net as the local machine, and the local machine also has KVM installed with Network Manager, then you can connect to remote KVM host's VM through qemu+ssh://UserName@IP_Address/system...


"LVM?"  Perhaps you mean "VM"?  

I use the qemu+ssh:// method with virt-viewer to connect to my VMs.
```
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system regulus &

```

hadar is the VM host.  
regulus is the guest VM.
```
    /usr/bin/virt-viewer --connect qemu+ssh://istar/system deneb &

```
istar is the VM host.
deneb is the guest VM.

To setup the VM, I use virt-manager, but that isn't the normal way for connections.  There's a **virt-viewer** client for the main 3 platforms.

---

### Post by MAFoElffen on 2024-03-31
@TheFu -- I meant "KVM Host", instead of "LVM Host". Was in a hurry and they  (L & K) are 1 key from each other = typo. Thank you for the catch.

---

### Post by harshl on 2024-04-01
Thanks for the responses guys. Unless I am massively misunderstanding something, I do have a bridge network, and it is working fine accept that one of the firewall technologies, that was present right out of a base install of 22.04.4 server is blocking traffic inbound to VMs on the other side of it.

Interface virbr0 is the main interface that I have attached my VMs to that need to communicate outside of the host. From the outside, production networks, I am routing to it from my production firewall, which is also working fine as I can reach the VMs once I add that IPTables line. Why that line is needed I have no idea and is a part of the mystery here.

Any thoughts on why that line is necessary to make this work? Can I provide any particular output that would help diagnose this?

To be abundantly clear, I have not installed, modified or added any firewalling technologies to this host besides that one line that makes it work. Everything else is as it was from a base install.

---

### Post by aljames2 on 2024-04-01
My guess is you are trying to use firewall rules to force bridge behavior on a NAT configuration.  virb0 is the default interface set up when you first install KVM and Libvirt.  The default is NAT.  It allows your guests to reach the outside world, but they are not seen on the network for inbound traffic. 

I suspect you need an actual bridge, br0.  This is something you have to set up yourself.  Then you attach your VM‘s to that interface.  I use Virt Manager when installing VMs & selecting the interface.  

My hosts use networkd and a netplan (.yaml) file for configuration.  This netplan file is where you define your physical interface and your bridge interface.  Alternatively, If you are using Network Manager instead, there is a way to set up a bridge using nmcli commands but I haven’t done that in a while.

The folks on this thread taught me how to do this when I started so I defer to their many years of expertise.  I am also not familiar with GNS.

---

### Post by harshl on 2024-04-01
> **aljames2 said:**
> My guess is you are trying to use firewall rules to force bridge behavior on a NAT configuration.  virb0 is the default interface set up when you first install KVM and Libvirt.  The default is NAT.  It allows your guests to reach the outside world, but they are not seen on the network for inbound traffic. 

I suspect you need an actual bridge, br0.  This is something you have to set up yourself.  Then you attach your VM‘s to that interface.  I use Virt Manager when installing VMs & selecting the interface.  

My hosts use networkd and a netplan (.yaml) file for configuration.  This netplan file is where you define your physical interface and your bridge interface.  Alternatively, If you are using Network Manager instead, there is a way to set up a bridge using nmcli commands but I haven’t done that in a while.

The folks on this thread taught me how to do this when I started so I defer to their many years of expertise.  I am also not familiar with GNS.

Ok, thank you aljames2, I guess I was making a poor assumption that interface virbr0, which was created by default upon install of the OS, would route, not just NAT, since all of the hosts are on the same subnet. Thank you so much for pointing me in this direction in a clear way. I will start looking at making that route, or create a new bridge interface.

Thanks again!

---

### Post by harshl on 2024-04-01
Between the comments from aljames2 and the article linked below, I am in good shape now.

FYI, I found this document TREMENDOUSLY helpful:
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_virtualization/configuring-virtual-machine-network-connections_configuring-and-managing-virtualization#types-of-virtual-machine-network-connections_configuring-virtual-machine-network-connections](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_virtualization/configuring-virtual-machine-network-connections_configuring-and-managing-virtualization#types-of-virtual-machine-network-connections_configuring-virtual-machine-network-connections)

It points out that the default virbr0 interface provided by libvirt is a NAT interface by default. Which explains why everything could get out, but nothing could get in, even though it was not actually NAT'ing for outbound traffic. The private subnet was seen on my firewall and I had to add a route back to the private subnet via the server host address. {shrug}

For my use case, this lab server sits in an isolated VLAN with the L3 on an NGFW, so I was able to just create a bridge interface, re-IP the management interfaces of my lab into that subnet and I was off to the races. Working great now.

Thanks all.

---

### Post by TheFu on 2024-04-02
Sorry that I wasn't clearer.  I've never used virbr0.  When I first started doing this on Linux, that wasn't automatically setup, so none of the VMs had any networking if we didn't manually add it.  I've seldom had much use for NAT VMs. Makes it hard (impossible) to manage them from my management systems.

The best description I've seen of the possible network configuration options available to a VM is actually in the VirtualBox Networking Chapter (ch 6) of the virtualbox manual.  It is worth reading if you haven't done VMs with different networking before.

"Bridged" is a specific type of network.  The name, virbr0, is just a name. Don't think it is a bridge. It is not.  Bridges connect two sides and are usually invisible.  They don't have/need an IP on the bridge at all.  

It is common to use the head of the bridge as the VM host IP "holder" too, though that isn't necessary for VMs using the bridge from the other side.  Guest VMs don't see or know about the bridge. It is only used in the VM fake/simulated hardware and usually for Linux, we want it to be virtio, not simulate a physical network card like an Intel e1000.  virtio isn't speed limited, has lower latency, and lower RAM/CPU overhead than any of the of the NIC choices.  Within the same VMhost, virtio bandwidth of 45 Gbps is possible, though it varies wildly.  Sometimes I see only 25 Gbps between my VM systems on the same host.

As for firealling, that happens inside the guest VM system, just like it is a physical host.  The ufw rules you showed above were for the virbr0 NAT device to prevent it from being a normal bridge.  I've never looked closely at it.

Anyway, sorry for the complete miscommunication. Glad you figured it out.  Translation isn't always simple.

If I were creating a new VM host today, I'd load 22.04 and setup the bridge on one of the spare NICs in my physical system to be the bridge as outlined at netplan.io/examples   Netplan is still maturing, but it has supported bridges well enough for VMs since the fall of 2020.  Before then, it had issues for me (or I was too stupid to understand it, hard to tell).  24.04 release date is getting close, but I won't consider making it production use until late July/August.  If it was June 2024 and I was forced to bring up a new VM host, I might load 24.04 then.  Other considerations would be important, mainly if my "play" 24.04 systems worked well and how many bugs were being reported/fixed weekly in the first few months after the release.  I don't need "new".  "Stable" is much more important for my needs.  We are all different, of course.

---

