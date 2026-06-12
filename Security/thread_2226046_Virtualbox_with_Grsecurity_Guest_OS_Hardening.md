---
title: "Virtualbox with Grsecurity Guest OS Hardening"
date: 2014-05-24
forum: Security
---

### Post by HardTrickySecurity on 2014-05-24
My topolgy:

My HP Desktop <----> CISCO PIX 515E Firewall <-----> Motorola cable modem <-----> ISP

What I am trying to do with Virtualbox is this:

1) Host:

-Lubuntu 14.04 (64 bit) installed with default kernel.
-I am going tu use this one for everything I do. (Internet, installing programs, study, os updates, etc)

2) Guest:

-Lubuntu 14.04 (64 bit) installed with Grsecurity Kernel (test) and all security options enable, trying to get the highest hardening kernel security I can get.
-I am not going to use this one at all, just for Grsecurity and OS updates.

What I am trying to do is to force all internet traffic go through VBox guest first and through grsecurity. Then it will go to VBox host, where I should be able to access internet normally. Making VBox guest kinda like a firewall. So if a hacker wants to hack the VBox host it would have do defeat or bypass first the VBox guest with grsecurity. I know I can use pfSense or IPFire etc. But in this case and for educational purposes I want to do it through Lubuntu 14.04 (64 bit) with grsecurity.

At this point I only need help with the VBox configuration. Wich adapters should I use? Bridge, NAT, Host-Only a combination. The configurations of gateways and IPs.
I found someone trying to do something similar, and I almost succed, I am able to have internet in guest but not in host when I use the command described there.

[https://bbs.archlinux.org/viewtopic.php?id=178057](https://bbs.archlinux.org/viewtopic.php?id=178057)

---

### Post by Chayak on 2014-05-25
I've not done it in virtual box but I've done networks in VMware to test that had virtualized routers and firewalls.  One interface needs to be host networking, and the other needs to be bridged.  Then it's setting up the host machine so the VM is the gateway on the host network, and configuring the bridged interface as normal.  I've used Vyatta and Mikrotik as the routers/firewall though.

---

### Post by HardTrickySecurity on 2014-05-25
> **Chayak said:**
> I've not done it in virtual box but I've done networks in VMware to test that had virtualized routers and firewalls.  One interface needs to be host networking, and the other needs to be bridged.  Then it's setting up the host machine so the VM is the gateway on the host network, and configuring the bridged interface as normal.  I've used Vyatta and Mikrotik as the routers/firewall though.


I havent tried this configuration with VMware. I will give it a try.

---

### Post by HardTrickySecurity on 2014-05-25
I asked in VBox forum and some one reply to me:

[https://forums.virtualbox.org/viewtopic.php?f=7&t=61875](https://forums.virtualbox.org/viewtopic.php?f=7&t=61875)

I'll admit I know little about networking. However, a guest can only  connect to the internet through the host. So I'm not sure how it could  go to the guest first.  [IMG]https://forums.virtualbox.org/images/smilies/icon_confused.gif[/IMG]
edit:  perhaps there is a way to create a filter that a guest can capture for a  USB to Ethernet adapter that is plugged into the host. I have no idea.


So I try to explain more in detail what I am doing:

1) I was able to use internet in guest using bridge mode, I put my PIX firewall gateway ip, in the guest OS network connections and they see each other without problems. I can do exactly the same thing with the Host. 
      
VB Host <-----> VB Guest <----> PIX Firewall = They all can see each other, and both host and guest have internet at the same time.

But the problem is when I enable gufw firewall in Guest and I block outgoing and incoming traffic, it only blocks internet traffic in guest but not in host. 

What I need is that when I block traffic in guest using gufw firewall, that automatically also blocks traffic in host. This way I am shure that internet traffic is going to be route or go first through the guest (gufw and grsecurity), and then through Host.

2) Then I a use bridge with Host-only and I use this command: 

sudo ip route change default via 192.168.0.1 #Change default route to vbox nic

After putting the command and configure IPs properly, I had internet in guest but not in host. Well, at least it makes internet traffic go first through guest.

I dont know if what I am trying to do is even possible with VBox. Its the first time I try this, but if is possible I am almost there.

---

### Post by Chayak on 2014-05-25
Host only network

Host: IP 10.255.255.10/24  <----->  VM Host only Int: IP 10.255.255.1/24  VM Host ext int: IP DHCP <----> PIX <----> Internet
         GW 10.255.255.1

You need something like that where the host interface is configured to use the VM as the gateway.  The VM will pick up it's gateway from DHCP.  The host interface itself should be on a separate network than the internal network otherwise there's no point in the setup as anyone coming into the network can go right to the host rather than through the routing/firewall in the VM.

---

