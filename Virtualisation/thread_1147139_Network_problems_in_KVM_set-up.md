---
title: "Network problems in KVM set-up"
date: 2009-05-03
forum: Virtualisation
---

### Post by The Foz on 2009-05-03
I am having trouble with the network set-up, using KVM & Qemu under Ubuntu 9.04 (Jaunty).

**_My system:_**

I have a Quad-Core Xeon processor, 5 GB RAM, 10GB swap, an ethernet card (eth0) connected to a 1Gb home LAN and a UMTS USB stick (ppp0) for internet access.

I am running the 64 bit desktop version of 9.04.

I am using Firestarter for fire-walling and for internet connection sharing, and dnsmasq for dns masquerading (not for DHCP).

The computer is used as printer and file server for the home network. All internet access goes via the "server". All of this works fine (it should do - I have been running this same set-up under 8.04 for 6 months).

_**My problem:**_

I have Qemu & KVM installed. I successfully installed Windows-XP in a virtual machine without problems. 

I then tried following the instructions on the KVM site ([http://www.linux-kvm.org/page/Networking]("http://www.linux-kvm.org/page/Networking")) to set up a public network bridge.

The instructions for "Solution 1: using distro sysconfig script" are not up to date, so I tried making the same changes in /etc/network/interfaces, but the bridge br0 could never be brought up (generated errors). I tried all sorts of modifications, including alternatives from various form posts, to no avail.

I then tried the "Solution 2: manual". I am able to create the bridge, using brctl. As soon as I add the eth0 interface ("brctl addif br0 eth0"), my internet connection sharing stops working. I am still able to access the internet from the server, but other machines can no longer even access the server (cannot ping, print, access shared files, etc.). If I remove the interface from the bridge, everything is fine again.

I tried the same method using pan0 (which seems to be a predefined bridge). The results are the same.

In all cases, when I start the XP VM, I have no internet connection. I know that ping will probably not work, but I am not able to access any web-sites, nor even to get DNS name resolution.

I then decided that I could probably live with user networking, so I started my VM with "qemu-system-x86_64 -hda /media/Spare/vdiskXP.img -net nic -net user -m 1000". At least this method doesn't disable my internet connection sharing, but I still have no internet access from the VM. I have of course tried changing various settings in the Windows network settings, but no luck there.

I would really like to be able to get the public bridge working (I will need it for other VMs that I plan to use), but for the moment I would be fairly happy just to get the XP VM working with user networking.

Anyone have any ideas?

---

### Post by wickerman1413 on 2009-05-03
I'm not sure about your firestarter/firewall setup or internet connection sharing but I had a few issues with networking on my fresh jaunty install. I had previously been using 8.10 with one Windows and one Ubuntu Server KVM. After some fiddling I ended up with a /etc/network/interfaces file that looks like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.1.220
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

The main stumbling block I had was that the network device type presented by KVm seems to be of a different type, which meant that when my VMs booted neither had the network interfaces (and related IP addresses) that they expected.

---

### Post by The Foz on 2009-05-04
Hi wickerman1413,

Thanks for your input. 

Your interfaces file may contain the key. I notice that your eth0 has no IP address assigned, but your bridge br0 does. I read in the KVM site that the bridge is supposed to "get the IP address".

I will try this out.

---

### Post by The Foz on 2009-05-05
I just tried out the suggestion from wickerman1413, and I now have everything working.

For anyone also using Firestarter for Internet Connection Sharing, please note that you will need to change the Firestarter preferences to use br0 as the local network connected device, instead of eth0 (which Firestarter reports as not ready).

---

### Post by wickerman1413 on 2009-05-06
Glad to hear you are all sorted Foz.

---

