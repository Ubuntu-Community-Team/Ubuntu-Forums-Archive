---
title: "virt-manager networking without iptables binary?"
date: 2024-02-24
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2024-02-24
Need to migrate from VirtualBox to virt-manager/KVM.  Was able to install virt-manager, convert and boot some VDIs, but have been unable to make networking work in the VM.

Many of the network types available in virt-manager seem to require [FONT=Courier New]iptables[/FONT] (despite documentation saying it can also work with firewalld and firewalld being installed and active).  However, this system intentionally does not have any iptables binary installed, because my nftables-based firewall contains some rules that are incompatible with iptables.  (If I understand correctly, firewalld sets up nftables rules that work alongside and after my main nftables firewall.)

Host system is Xubuntu 22.04.  Several guest types are involved, but at the moment I'm trying to make networking work on a Xubuntu 22.04 guest.

With Bridge or Macvtap, the VM at least boots, but in neither case can I get networking working - NetworkManager in the guest just continuously tries and fails to connect.

For Bridge I'm using nm-connection-editor to set up the bridge interface, and tried several different configurations.  In case it's relevant, the host gets networking via Wi-Fi.

Would like to achieve the effects of 3 networking types from VirtualBox:
[LIST]
[*]NAT: for Internet access with traffic to/from the VM filtered by the host's firewall,
[*]Bridged: for when the VM should act as another physical machine on the same network as the host, without the host's firewall applying to the VM's traffic,
[*]Host-only networking: for cases where networking is needed to connect to something on the host or another VM, but where allowing Internet access would be unsafe.
[/LIST]

How to get these types of networking in virt-manager without having any iptables binary present on the system?

Thanks for any help.

---

### Post by The Cog on 2024-02-24
I don't know how virt-manager configures firewall rules it needs, but I am sure that a recent virt-manager would be able to cope with a system using nftables. I suspect you are reading outdated descriptions of using virt-manager. 
This doc might prove informative: [https://www.redhat.com/en/blog/using-iptables-nft-hybrid-linux-firewall](https://www.redhat.com/en/blog/using-iptables-nft-hybrid-linux-firewall)

---

### Post by &amp;KyT$0P# on 2024-02-24
Sorry, should have specified that errors when using iptables-nft and iptables-translate are how I determined there is incompatibility and why need to keep this system pure-nftables-only.

* For example:
```
$ sudo iptables -L -v
iptables v1.8.7 (nf_tables): table `filter' is incompatible, use 'nft' tool.
```

---

### Post by The Cog on 2024-02-24
So there is already an nft rule configured that cannot be back-translated to iptables. I guess the answer to that is to use nftables rather than iptables - don't try to back-translate. If you are trying to follow guides that want you to user iptables commands, you will need to work out the equivalent nftables command to use.

---

### Post by &amp;KyT$0P# on 2024-02-24
The apparent iptables requirement is that virt-manager throws this error dialog when creating a virtual network, regardless of whether firewalld is installed and active -
```
Error creating virtual network: internal error: Failed to apply firewall rules /usr/sbin/iptables -w --table filter --list-rules: libvirt:  error : cannot execute binary /usr/sbin/iptables: No such file or directory


Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 72, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/createnet.py", line 428, in _async_net_create
    netobj.create()
  File "/usr/lib/python3/dist-packages/libvirt.py", line 3470, in create
    raise libvirtError('virNetworkCreate() failed')
libvirt.libvirtError: internal error: Failed to apply firewall rules /usr/sbin/iptables -w --table filter --list-rules: libvirt:  error : cannot execute binary /usr/sbin/iptables: No such file or directory
```

Could have sworn this was happening on all virtual network types, but checking again now, the "Open" mode virtual network is now working without an iptables binary.  And using the Open network allows me to ping the guest from the host.

This has me wondering if the problem maybe that my nftables firewall rules are dropping too much for any type of virt-manager networking to function, i.e. there is no virt-manager network type where the VM networking is like just another application on the host, and I'm not yet familiar enough with virt-manager/libvirt to know what needs to be allowed? :-k Think I need to do some experimenting with the host firewall to see to what extent it's interfering here.

---

### Post by &amp;KyT$0P# on 2024-02-24
Ok, with host firewall completely disabled, the Open network appears to be working as host-only networking, solving one of the 3 issues.  How can I prove this network is really isolated to host-only, and not just not configured for available Internet or LAN access?

---

### Post by The Cog on 2024-02-25
I grabbed a look at a machine at work, running Ubuntu 22.04. It had multiple VMs configured, each with a NIC in Isolated mode (and one with multiple NICs all in isolated mode). But I know these VMs are all able to communicate with each other and with the host. It seems that each isolated NIC is connected to one of several Virtual Bridges, so Isolated doesn't necessarily mean totally isolated.

The host is running Ubuntu 22.04 and has iptables installed. iptables-save and iptables -nvL both work, so there are no nft-only rules in there. Interestingly, both iptables-save and nft list ruleset show  rules, and I *think* they both show *all* the rules. It seems that iptables is installed, not any of the iptables-nftables hybrid packages. So is ufw. I think UFW is creating the nft rules.

It may be that installing iptables would do it for you, even if you can only list the rules with nft. But I would suggest using the iptables-nft converter version. Your last post shows that virt-manager is using /usr/sbin/iptables to manipulate the rules, so I guess it won't mind using the iptables-nft version.

---

### Post by &amp;KyT$0P# on 2024-02-25
> **The Cog said:**
> It may be that installing iptables would do it for you, even if you can only list the rules with nft. But I would suggest using the iptables-nft converter version. Your last post shows that virt-manager is using /usr/sbin/iptables to manipulate the rules, so I guess it won't mind using the iptables-nft version.

Unfortunately this doesn't work, virt-manager throws this error dialog -
```
Error creating virtual network: internal error: Failed to apply firewall rules /usr/sbin/iptables -w --table filter --list-rules: iptables v1.8.7 (nf_tables): table `filter' is incompatible, use 'nft' tool.



Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 72, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/createnet.py", line 428, in _async_net_create
    netobj.create()
  File "/usr/lib/python3/dist-packages/libvirt.py", line 3470, in create
    raise libvirtError('virNetworkCreate() failed')
libvirt.libvirtError: internal error: Failed to apply firewall rules /usr/sbin/iptables -w --table filter --list-rules: iptables v1.8.7 (nf_tables): table `filter' is incompatible, use 'nft' tool.
```

I was able to work around the error with [FONT=Courier New]sudo iptables -L -v[/FONT] by renaming my firewall table to something other than [FONT=Courier New]filter[/FONT] , which causes [FONT=Courier New]iptables[/FONT] to report an empty firewall ([FONT=Courier New]nft[/FONT] still reports all rules).  However, virt-manager continues to throw this same error dialog even after the rename and [FONT=Courier New]sudo iptables -L -v[/FONT] is working.

Was hoping that if any additional firewall rules are needed, they could be manually added using [FONT=Courier New]nft[/FONT] tool.  Is there no way to get working networking in virt-manager without any [FONT=Courier New]iptables[/FONT] binary?

---

### Post by TheFu on 2024-02-25
I don't remember ever touching firewall rules to get KVM/QEMU VMs working.  

However, I always, ALWAYS, manually setup a bridge on the host OS and completely ignore all the other network options inside virt-manager.

For example, 
```
network:
  version: 2
  renderer: networkd
  ethernets:
    [COLOR="#FF0000"]enp3s0[/COLOR]:
      optional: true
      dhcp4: false
      dhcp6: false
  bridges:
    [COLOR="#FF0000"]br0[/COLOR]:
      dhcp4: false
      dhcp6: false
      interfaces: [[COLOR="#FF0000"]enp3s0[/COLOR]]
      addresses:
      - [COLOR="#FF0000"]172.22.22.6[/COLOR]/24
      gateway4: [COLOR="#FF0000"]172.22.22.1[/COLOR]
      nameservers:
        addresses:
        - [COLOR="#FF0000"]172.22.22.81[/COLOR]
        - [COLOR="#FF0000"]172.22.22.80[/COLOR]
```

Think I made everything red that you definitely need to change for your network.

Then I specify br0 in the VM settings for each VM and setup static IPs after the first boot which uses a DHCP from my limited range of DHCP IPs.  Additionally, I'll set the MAC inside the VM to end with the same last 1 digits that the static, assigned, IP for the VM gets.   then I go and up date my 2 internal DNS servers with that IP so every system on that subnet can find the VM.

No IP tables anything involved ... er ... unless you want to add them inside the VM or for the hostOS, but those have nothing to due with each other. Those rules are just for the OS they are set inside.

**Don't use wifi for the host. Most wifi chips don't support bridging.**  And definitely don't use DHCP for the host either.  That's just asking for trouble.

---

### Post by &amp;KyT$0P# on 2024-02-25
> **TheFu said:**
> **Don't use wifi for the host. Most wifi chips don't support bridging.**

Ugh #-o That explains it, thanks.  Unfortunately neither the test host nor the future production host are physically located where a wired Internet connection is available, and changing this isn't feasible :(

In trying to dig into what firewall rules virt-manager sets, in case manually creating them using [FONT=Courier New]nft[/FONT] might work, I noticed a critical sentence in [libvirt documentation about firewalld]("https://libvirt.org/firewall.html#firewalld-and-the-virtual-network-driver") that I had completely missed -
> libvirt's own rules outlined above will *always* be iptables rules regardless of which backend is in use by firewalld.

So what is written [here]("https://forums.debian.net/viewtopic.php?t=152650") is unavoidable: the "[iptables OR firewalld]("https://packages.ubuntu.com/jammy-updates/libvirt-daemon-system")" dependency specification is incorrect, libvirt/virt-manager only works with iptables, it just happens to have some firewalld integration that has nothing to do with why it uses iptables.  (Although since not every networking type requires iptables, maybe iptables should just be a Recommends, seems most virt-manager functionality works without it.)

---

### Post by #&amp;thj^% on 2024-02-25
> firewalld and the virtual network driver

If firewalld is active on the host, libvirt will attempt to place the bridge interface of a libvirt virtual network into the firewalld zone named "libvirt" (thus making all guest->host traffic on that network subject to the rules of the "libvirt" zone). This is done because, if firewalld is using its nftables backend (available since firewalld 0.6.0) the default firewalld zone (which would be used if libvirt didn't explicitly set the zone) prevents forwarding traffic from guests through the bridge, as well as preventing DHCP, DNS, and most other traffic from guests to host. The zone named "libvirt" is installed into the firewalld configuration by libvirt (not by firewalld), and allows forwarded traffic through the bridge as well as DHCP, DNS, TFTP, and SSH traffic to the host - depending on firewalld's backend this will be implemented via either iptables or nftables rules. libvirt's own rules outlined above will *always* be iptables rules regardless of which backend is in use by firewalld.
Source: [https://libvirt.org/firewall.html#firewalld-and-the-virtual-network-driver](https://libvirt.org/firewall.html#firewalld-and-the-virtual-network-driver)

Mine are very basic on this set-up:
```
virsh nwfilter-list
 UUID                                   Name
-----------------------------------------------------------------
 606d786b-10b0-4b1b-98f5-5dea9326ae97   allow-arp
 a7746631-2e20-46b3-86bc-b4c5fe4a1208   allow-dhcp
 d6588fc2-7874-4fb1-9ffd-17f94237e344   allow-dhcp-server
 7bb6a34e-6bb1-49e1-9f41-3adb75c2fb00   allow-dhcpv6
 e94b5dba-bff1-404b-9170-0631d5d84739   allow-dhcpv6-server
 9f479bf2-a47e-43cd-a784-870d202809c1   allow-incoming-ipv4
 43a2ca94-f098-472e-9a33-051e225bd885   allow-incoming-ipv6
 6aff8004-39c2-4205-a159-8f002484cff1   allow-ipv4
 fe48d5f0-07eb-4e98-bfb6-2985489b7ace   allow-ipv6
 4847be07-2989-4eaa-90e8-51cc39c66c17   clean-traffic
 75d7b236-d527-45fd-9413-977f8e242bf6   clean-traffic-gateway
 a4a834c7-a867-4473-a517-bc6e77897c7a   no-arp-ip-spoofing
 8bb99a08-63e1-4b48-b999-32ba9844f642   no-arp-mac-spoofing
 efeed4c9-0534-4c86-b428-b94b7d4e8b88   no-arp-spoofing
 0f98375e-de17-4c97-a0ad-daf79837aa1a   no-ip-multicast
 d51bb497-5596-41f8-b5ef-cafc740a14b9   no-ip-spoofing
 3c5f7c58-7e35-4c37-b943-02e7fd9102f0   no-ipv6-multicast
 a65c5c5a-6364-4935-b9fa-94415e9995eb   no-ipv6-spoofing
 3daac86c-d45b-4583-a670-a4932d8711ca   no-mac-broadcast
 111a1ae2-2e2d-4696-970c-cb675198d3ee   no-mac-spoofing
 f2a7c870-2c7d-4f46-ad37-d83308af4f44   no-other-l2-traffic
 62e36467-17c3-4b1f-809f-89a361842d27   no-other-rarp-traffic
 dab30a8f-4ad2-4784-8f47-70dc5f6a25a0   qemu-announce-self
 b96ed81f-117a-430d-9181-ac33b7c3a70f   qemu-announce-self-rarp

```
From the host.

---

### Post by TheFu on 2024-02-26
> **halogen2 said:**
> Ugh #-o That explains it, thanks.  Unfortunately neither the test host nor the future production host are physically located where a wired Internet connection is available, and changing this isn't feasible :(

[LIST]
[*]Powerline Networking
[*]MoCA Networking
[/LIST]

I use PowerLine to connect different floors, but if I were doing it today, I'd go with 2.5Gbps MoCA instead.  MoCA gets the rated bandwidth if it works.  PowerLinux for me was 1/10th the advertised speed on the box.  I did lots of tests around the house to see it degrade.  [https://blog.jdpfu.com/2015/08/27/powerline-ethernet-adapters](https://blog.jdpfu.com/2015/08/27/powerline-ethernet-adapters) Nobody even gets 50% of the marketing number on the box.  That's fine.  It is still better than wifi, since almost anything is better than any RF signaling.

Actually, I could use a MoCA setup with 3 nodes to replace the powerline setup that is almost 10 yrs old now.  Too many hobbies being worked right now, so it will need to wait for a trial. MoCA has lots of little issues, so be certain to read up on those in general and for the specific models you consider.  Read that 1 of the sets didn't have a factory reset button and certain settings were stuck due to that. That was a few years ago. It should be long fixed.  Powerline has issues too, but if it works, it is basically like a slow ethernet bridge and devices don't see it besides the slower connection.

It should be obvious, but we are using existing house wiring for both these non-CAT5e+ connections. If your house isn't wired with COAX or electrical plugs in the desired locations, then that would make using one or both less than useful. My house has COAX to almost every room that isn't a bathroom or closet. Not all the COAX is connected anywhere. The terminal is outside in the demarcation used by the cable company, so I'd need to ensure the different COAX lines for my network are connected to the distribution switch there.

---

### Post by &amp;KyT$0P# on 2024-02-26
> **halogen2 said:**
> I was able to work around the error with [FONT=Courier New]sudo iptables -L -v[/FONT] by renaming my firewall table to something other than [FONT=Courier New]filter[/FONT] , which causes [FONT=Courier New]iptables[/FONT] to report an empty firewall ([FONT=Courier New]nft[/FONT] still reports all rules).  However, virt-manager continues to throw this same error dialog even after the rename and [FONT=Courier New]sudo iptables -L -v[/FONT] is working.

Well that was strange.  Setting this up on the production host, the nftables table rename does completely solve the problem there, virt-manager is able to use iptables-nft no problem, and the VM can get internet access with NAT network.  Thanks The Cog for your advice! :KS

Still wondering about this though? -
> **halogen2 said:**
> the Open network appears to be working as host-only networking, solving one of the 3 issues.  How can I prove this network is really isolated to host-only, and not just not configured for available Internet or LAN access?
How does this differ from [Isolated network]("https://wiki.libvirt.org/VirtualNetworking.html#isolated-mode"), which description matches the way the Open network appears to function?

> **TheFu said:**
> [LIST]
[*]Powerline Networking
[*]MoCA Networking
[/LIST]
...
If your house isn't wired with COAX or electrical plugs in the desired locations, then that would make using one or both less than useful. 

No accessible coax cables or extra plugs in this location, but good to know about those options, I was not aware of them.  Thanks for the info.

---

### Post by TheFu on 2024-02-26
I'm struggling to understand what the difference is between NAT and bridged if you are going to open ports to the guest.  Firewalls can run inside the VM and do any firewalling like a physical host provides.  I run my VPN server inside a VM guest to take advantage of this.

If you just want to run 1 network service inside a protected area, perhaps a Linux Container would be a better choice?  Containers use 1/10th (or less) the overhead that a  full VM uses.  If you use Docker, forwarding 1 port into the container is normal.  If you use LXC/LXD, you can treat it like a VM, just without a firewall.  Containers shouldn't be run with elevated privileges, so they shouldn't be able to run a firewall unless someone screwed up (cough docker). Running a container with privilege sorta defeats 99% of the security that Linux Containers provide by running as nobody users.

---

### Post by &amp;KyT$0P# on 2024-02-27
> **TheFu said:**
> I'm struggling to understand what the difference is between NAT and bridged if you are going to open ports to the guest.

99% of the time I use a guest with open ports, I only want the host and/or specific other guests to be able to access the open ports.  It's simpler, and potentially less attack surface, to use a networking setup that "just has" this isolation than to effect it using guest firewall rules.

---

### Post by &amp;KyT$0P# on 2024-03-02
If I manually create a bridge interface in [FONT=Courier New]nm-connection-editor[/FONT], don't add any other interfaces to it, and set up VMs with Bridge networking to this interface, can I be sure this is a host-only network?  With such bridge, traffic between host and guests is working, as is guest-to-guest traffic, and on the host [FONT=Courier New]ip link show master [COLOR="#FF0000"]<bridge_interface_name>[/COLOR][/FONT] shows only the vnet interfaces for the VMs.

---

### Post by TheFu on 2024-03-02
I purge network-manager from all my systems, since the bad times around 2012.  NM is one of the tools I have no time to bother using.

Bridges aren't for host-only networks.

---

### Post by &amp;KyT$0P# on 2024-03-02
> **TheFu said:**
> Bridges aren't for host-only networks.

:confused:
Could you please elaborate on this?

Based on attempting to read [this]("https://developers.redhat.com/articles/2022/04/06/introduction-linux-bridging-commands-and-features") (but don't currently have enough networking knowledge to get my head around everything written there), I thought bridges are basically virtual network switches, which could be configured for use for anything a physical network switch could be used for?

What would be the correct/best way to create a host-only network between virt-manager VMs which doesn't need firewall rules to enforce and where libvirt doesn't start a dnsmasq instance?

---

### Post by TheFu on 2024-03-02
Sorry, I don't do host-only networking.  I use normal linux bridges which connect bi-directionally A <-----> B.  That's what a bridge does.  It connects two things usually over a canyon or some sort of water. It is bi-directional.  Of course, you can setup blocks on the inbound side, if you like. That would be a firewall, separate from the bridge.

The virtualbox manual, chapter 6 has a good explanation.

---

### Post by volkswagner on 2024-03-02
It seems like running from Wi-Fi card is not contributing to the issue. I’ll add to the other suggestions in case using the LAN port would be better. There are Wi-Fi routers or access points that can bridge the house/company Wi-Fi and provide wired LAN to the laptop’s NIC. 


For private/host only networks, can’t you create a virtual bridge per VM to keep networking between host & vm? This may complicate your NAT rules to provide Internet to the VM.

---

### Post by &amp;KyT$0P# on 2024-03-03
Thanks all for the clarifications :KS So a bridge will only forward packets between the interfaces that are explicitly connected to the bridge, so passing anything else to the bridge and its network would require a specific effort, e.g. firewall rules to specifically perform NAT - so in the absence of such firewall rules, if only VMs' interfaces are connected to the bridge, it's a host-only network.

After looking through the [VirtualBox manual chapter]("https://www.virtualbox.org/manual/ch06.html") TheFu suggested, I'm re-evaluating this goal -
> **halogen2 said:**
> Bridged: for when the VM should act as another physical machine on the same network as the host, without the host's firewall applying to the VM's traffic,

Think I might be better off doing NAT port forwarding and temporarily opening the forwarded port in the host firewall.  Need to experiment with port forwarding to see if it would work to the desired effect.

> **volkswagner said:**
> There are Wi-Fi routers or access points that can bridge the house/company Wi-Fi and provide wired LAN 

This could work, thanks for the suggestion.  Have done it before once, and still have that extra router, but at this point that router is years EOL so would need to get another router to do this safely.

---

### Post by TheFu on 2024-03-03
> **halogen2 said:**
>  
Think I might be better off doing NAT port forwarding and temporarily opening the forwarded port in the host firewall.  Need to experiment with port forwarding to see if it would work to the desired effect.

I fail to see how the added complexity helps when you could just do a simple bridge, then setup a firewall on the guest that blocks all inbound ports, except ssh and the specific service ports you want open.  OTOH, sometimes people like to do things the hard way, which is fine too.


> **halogen2 said:**
>  
This could work, thanks for the suggestion.  Have done it before once, and still have that extra router, but at this point that router is years EOL so would need to get another router to do this safely.

All wifi routers aren't safe currently.  Even the wifi-6 standard has known, working, attacks today.  Since the early 2000s, I've always used a full VPN with any Wifi connection, even inside my house.  All my computers and most IoT devices are wired ethernet connected, but 1 attic video camera, some tablets and phones only support wifi, so those all connect between the ISP router and my router, then use wireguard if they want access inside any specific subnets.  Some people say I'm paranoid.  When someone hacks your network and the only way that is possible is through wifi, you'd be paranoid too.

OTOH, I use powerline networking to get wired networks to rooms that don't have any ethernet connections. If I need to upgrade, I'll probably switch to 2.5Gbps MoAC for greater bus bandwidth. I have COAX to most rooms already.

BTW, I just got an Asus wifi-6 router ($38 used) to replace an older wifi-n router.  Both were/are used to bridge wifi devices to the ISP's router. The wifi is mostly for house guests, though we do use the tablet to control media playback in the projector room.  Setup was less than 5 minutes. Asus does the best job of security patching, thanks to an FTC lawsuit and outside mandated audits for another 10+ yrs.  If you don't go with a pure AP from a reputable brand, Asus is the next best choice, IMHO - of course, all wifi needs a VPN to be secure. No getting around that that.  All RF needs a full VPN.

---

### Post by aljames2 on 2024-03-03
+1 TheFu

> **halogen2 said:**
> Thanks all for the clarifications :KS So a bridge will only forward packets between the interfaces that are explicitly connected to the bridge, so passing anything else to the bridge and its network would require a specific effort, e.g. firewall rules to specifically perform NAT - so in the absence of such firewall rules, if only VMs' interfaces are connected to the bridge, it's a host-only network.

Not sure I agree with this statement. The point of a bridge is to allow VMs to appear as just another host on the network. They can communicate with, and are reachable by other hosts on the network (subnet) because they are on a bridge.  As mentioned, it's the firewall rules on each host that allow or deny traffic according to your needs.  The KVM "default" network upon installation is NAT which hides VMs behind the host with only outboud internet traffic, perhaps good for a testing environment. So we can create a bridge, or other virtual network device to configure how our VMs participate on the network.

---

### Post by volkswagner on 2024-03-03
> **aljames2 said:**
> 



Not sure I agree with this statement. The point of a bridge is to allow VMs to appear as just another host on the network. They can communicate with, and are reachable by other hosts on the network (subnet) because they are on a bridge.  As mentioned, it's the firewall rules on each host that allow or deny traffic according to your needs.  The KVM "default" network upon installation is NAT which hides VMs behind the host with only outboud internet traffic, perhaps good for a testing environment. So we can create a bridge, or other virtual network device to configure how our VMs participate on the network.

The function of the bridge is dependent upon which interfaces are included (plus firewall and routing). If a bridge is created without including the local LAN interface, how does that help your argument? I think you are only considering a limited number of bridge configurations. If I bridge my loopback interface, that won't inherently help me connect to my LAN. Consider this, you can create a bridge without any ports.

---

### Post by aljames2 on 2024-03-03
> **volkswagner said:**
> I think you are only considering a limited number of bridge configurations. If I bridge my loopback interface, that won't inherently help me connect to my LAN. Consider this, you can create a bridge without any ports.

It sounds like it. I probably don't know enough to carry on further here. I had not experienced these more advanced networking possibilities, so apologies to the OP.  And thanks @volkswagner for giving me more learning rabbit holes to run down :)

---

### Post by &amp;KyT$0P# on 2024-03-16
Thanks again to all for the help and info! :KS Think this is finally good to go.

To summarize the solution:

> **halogen2 said:**
> NAT: for Internet access with traffic to/from the VM filtered by the host's firewall

Using the libvirt NAT network type worked after installing [FONT=Courier New]iptables-nft[/FONT] (from [FONT=Courier New]iptables[/FONT] package).  To make it work despite the iptables-incompatibility of my nftables rules, had to install [FONT=Courier New]iptables-nft[/FONT] and rename my nftables firewall table **before** installing libvirt and virt-manager.

> Bridged: for when the VM should act as another physical machine on the same network as the host, without the host's firewall applying to the VM's traffic

Decided to go with NAT port forwarding instead, which I got working based on [nftables wiki on Destination NAT]("https://wiki.nftables.org/wiki-nftables/index.php/Performing_Network_Address_Translation_(NAT)#Destination_NAT") and [libvirt info explaining that a firewall rule must be added to allow the forwarded traffic]("https://wiki.libvirt.org/Networking.html#forwarding-incoming-connections").  Since I don't always want the port accessible from outside, didn't set this up as a QEMU hook, instead I manually run the commands to modify the firewall.

And to answer TheFu:
> **TheFu said:**
> I fail to see how the added complexity helps when you could just do a simple bridge, then setup a firewall on the guest that blocks all inbound ports, except ssh and the specific service ports you want open.  OTOH, sometimes people like to do things the hard way, which is fine too.

Partially for fun :mrgreen: , partially out of curiosity to see if I *could* do it and if I could set up to connect to a KVM guest from outside without using additional hardware.

The particular case here only requires one port.  Now knowing what's involved in NAT port forwarding, I see why this would be "the hard way" and "added complexity" for anything beyond single-port cases.  If something more complex comes up, would definitely try bridging ethernet through an Asus router.

> **halogen2 said:**
> Host-only networking: for cases where networking is needed to connect to something on the host or another VM, but where allowing Internet access would be unsafe.

Was achieved by creating a bridge interface in NetworkManager, **not** adding any other interfaces to the bridge, then setting the VM's NIC to Bridge to that interface.

---

### Post by MAFoElffen on 2024-03-17
I see the need to add a caveat, for the just in case another factor is added to this discussion... (becaseu you entioned wifi rotuers)

Network Bridges work at Network Level 3 (IP), whereas Wireless AP's work at Level2 (MAC address authentication). Just keep that in the back of your thoughts...

+1 along with TheFu --- I also gave up on Network Manager years ago. For Sys Admins that review their logs (as they should), you will soon see why Network Manger is not stable, and causes a lot of it's own problems.

---

