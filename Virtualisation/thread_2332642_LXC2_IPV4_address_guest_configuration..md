---
title: "LXC2 IPV4 address guest configuration."
date: 2016-08-02
forum: Virtualisation
---

### Post by mccalleyt on 2016-08-02
I have been trying to create a Ubuntu 16.04 amd64 LXC2 Operating System Container that is being used for a file server (using SSH and Unison). I need the machine to get an IPv4 address from my local subnet so I can access an NFS share for the LXC2 container. The documentation that I can find for it doesn't tell me what I need to know to do this. Also how can I use Virt-manager to handle LXC thru libvirt?

---

### Post by MAFoElffen on 2016-08-03
Sidenote- What do you mean by LXC2? Do you mean LXD? Does not matter? But thought to ask, as to be clear.

For the static IPv4 address to live on the same Network ID (NID) as your host, you would need an additional NIC on your host to bridge to your host NID. (Just like you would for KVM or Xen. You could also route between the native lxbro NID and your host NID.

The third option is something I do for network file storage- I let my managed network file storage be on it's own net, that way the net traffic of files storage between my servers and my managed storage does not affect the net traffic of the rest of my network (segregation). What that means for my virt servers, it that I bridge them to that managed storage net. I let that net be on it's own NIC, just for that managed storage net. Additionally, I Then route that net to my host network for client access to file shares.

Bridging = install bridge-utils, setup /etc/network/interfaces to configure the bridge. Have more details, if needed.

---

### Post by mccalleyt on 2016-08-03
I am using LXD. I am trying to setup a bridge for Internal routing only to use for NFS between host and guest. Then I need an additional macvlan bridge to have communication with local machines. The OS container will run a sftp/scp server with unison for a backup server. I would also like to find a way to manage my LXD with Virt-manager or some way to have a graphical manager.

---

### Post by mccalleyt on 2016-08-03
I think I have it figured out the networking from here. I found [this article]("https://insights.ubuntu.com/2015/11/10/converting-eth0-to-br0-and-getting-all-your-lxc-or-lxd-onto-your-lan/"). I then looked up profiles and how to configure profiles. I am still faced with the challenge of using _***virt-manager***_ to manage my LXD/LXC server.

---

### Post by MAFoElffen on 2016-08-05
That is the same for most virtual networking in Linux and you can find details in the Ubuntu Wiki in Bridging.

That is not macvlan or macvtap. What doing that will do... let me try to explain how that works on my KVM /LXD servers. I have at least 2 NIC's on each. # on my primary, 2 on my secondary).

One NIc is host, but shares bandwidth on lxbr0, virbr0, dockerbr0 and the defualt KVM NAT... and macvtap. Each of those is on it's awn Network ID, except macvtap. If I use macvtap on my first interface, it shares the inerface with the host and ends up on the host network. 

Just as shown in your post, by that link, br0 is on the same Network ID as the host, but that kind of bridge is static and does not share the NIC. It is bonded to the device. When you bond the bridge to the device, it is no longer usable by the host itself. Therefore the need for a dedicated NIC for that kind of bridge.

Not sure if that happens on how he set that up in his interfaces file, but it does happen with this:
```

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
address 192.168.2.15
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
dns-search xxxxxxxxxx.com

auto eth3
iface eth3 iface manual

auto eth4
iface eth4 iface manual

auto bond0
iface bond0 inet manual
bond-miimon 100
bond-lacp rate1
post-up
ifenslave bond0 eth3 eth4
bond-slaves none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1

auto br0
iface br0 inet static
address 192.168.2.17
netmask 255.255.255.0
broadcast 192.68.2.255
network 192.168.2.0
gateway 192.168.2.1
dns-search xxxxxxxxxx.com
dns-nameserver 192.168.2.15 192.168.2.16
bridge_ports bond0
bridge_stp off
bridge_fd 9
bridge_hello 2
bridge_maxage 12

```
On that eth 2 is host, lxbr0, virbr0, dockerbr0. Both eth3 & eth4 are bonded as one device, then bonded to the bridge... That way I have more throughput to the many VM Guests going through that bridge... that are also providing Host Network services.

EDIT-- Note to others, this server started out life with eth0, eth 1 and eth2. After a release update from 14.04 to 16.04, all of a sudden, the first 2 llogical ports "disappeared" and the physical ports shifted/changed device names to eth2, eth3 & eth4. Took a bit to figure out that the devices names had changed. That personal experience is why I now ask users to verify their machine network device names when having problems with 16.04. But this is 1 of 3 identical servers, whereas the other 2 are fine and did not change.

---

### Post by mccalleyt on 2016-08-07
I only have one interface to use. I have another machine that does need help with this issue. I have it running ubuntu server 16.04.1 with a few KVM machines. I tried the adding br0 like I did with the other one but it tells me that enp2s0f2 is already a member of a bridge. I need my LXC2 (LXD) to run on my main subnet.

---

### Post by mccalleyt on 2016-08-07
I tried using the bond0 like yours shows bu to no avail.

---

### Post by MAFoElffen on 2016-08-08
You cannot do a bridge like mine, with only one NIC. Takes at least 1 for the host and one for the bridge.

To have only one NIC have it sahred between the host (admin net), and t o have the LXD container also have Host NID connectivity, then you would do macvtap.

---

