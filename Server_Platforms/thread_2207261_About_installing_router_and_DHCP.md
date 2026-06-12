---
title: "About installing router and DHCP"
date: 2014-02-22
forum: Server Platforms
---

### Post by satimis on 2014-02-22
Hi all,

Host - Ubuntu 12.04
VM - Ubuntu 12.04
Virtualizer - Oracle VirtualBox

I'm prepared installing router and DHCP server.  Can I install them on a VM instead on the Host?  I expect keeping the Host clean only for running Oracle VirtualBox.

Tutorial:-

Router
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)


DHCP server:
Dynamic Host Configuration Protocol (DHCP)
[https://help.ubuntu.com/12.04/serverguide/dhcp.html](https://help.ubuntu.com/12.04/serverguide/dhcp.html)

Setting up a DHCP server on Ubuntu 12.04 (Precise Pangolin) server
[http://lani78.com/2012/07/23/setting-up-a-dhcp-server-on-ubuntu-12-04-precise-pangolin-server/](http://lani78.com/2012/07/23/setting-up-a-dhcp-server-on-ubuntu-12-04-precise-pangolin-server/)

Please advise.  Thanks

Rgds
satimis

---

### Post by CharlesA on 2014-02-22
You could, but if you are going to have it exposed to the internet, I wouldn't virtualize it.

Is this going to be your gateway to the internet or server another purpose?

---

### Post by satimis on 2014-02-22
> **CharlesA said:**
> You could, but if you are going to have it exposed to the internet, I wouldn't virtualize it.

Is this going to be your gateway to the internet or server another purpose?
Hi,

Thanks for your advice.

I'm going to subscribe FTTH (Fibre-to-the-home) fibre optic broadband.
100M/100M up/down
Static IP

The new ISP shall not provide router.  I have only 2 PCs, both running virtualization and each with 10 VMs installed.  The local websites are only mirror of the websites hosted on Godaddy.

I'm going to install a router and DHCP server on a VM, if it is possible.  I expect to learn how to build them.  If failure I'll buy a gigabit router, 1 WAN and 4-ports

satimis

---

### Post by CharlesA on 2014-02-23
Just buy a gigabit router and save yourself the headache.

Otherwise get a dedicated box and run something like [pfSense]("http://www.pfsense.org/"), or [Untangle]("https://www.untangle.com/") or one of the other *BSD based firewalll/router distros.

I've used pfSense.

---

### Post by sandyd on 2014-02-23
> **CharlesA said:**
> Just buy a gigabit router and save yourself the headache.

Otherwise get a dedicated box and run something like [pfSense]("http://www.pfsense.org/"), or [Untangle]("https://www.untangle.com/") or one of the other *BSD based firewalll/router distros.

I've used pfSense.

side note: _test_ with pfSense carefully on KVM (download at full speed for a while),and check its cpu usage. In some computers, pfSense has a CPU Usage issue where network traffic is causing heavy cpu usage, which makes it basically useless because there is a correlation between download speed and cpu usage

---

### Post by CharlesA on 2014-02-23
> **sandyd said:**
> side note: _test_ with pfSense carefully on KVM (download at full speed for a while),and check its cpu usage. In some computers, pfSense has a CPU Usage issue where network traffic is causing heavy cpu usage

Agreed. I'd rather run it on a dedicated box than virtualized tbh.

There are some hardware vendors listed on their site.
[http://www.pfsense.org/hardware/index.html](http://www.pfsense.org/hardware/index.html)

---

### Post by satimis on 2014-02-25
Hi all,

I found following documents which are quite interesting to me:

1)
Notes/Virtual Linux Router with VirtualBox
[http://wiki.smalleycreative.com/Notes/Virtual_Linux_Router_with_VirtualBox](http://wiki.smalleycreative.com/Notes/Virtual_Linux_Router_with_VirtualBox)

2)
Tutorials:Using Linux Virtual Machine instead of router for VPN
[http://wiki.hidemyass.com/Tutorials:Using_Linux_Virtual_Machine_instead_of_router_for_VPN](http://wiki.hidemyass.com/Tutorials:Using_Linux_Virtual_Machine_instead_of_router_for_VPN)

3)
Creating a Virtual Network of Linux Guests using VirtualBox
[http://sandilands.info/sgordon/creating-a-virtual-network-of-linux-guests-using-virtualbox](http://sandilands.info/sgordon/creating-a-virtual-network-of-linux-guests-using-virtualbox)

I haven't gone through all of them deeply.  On 3) it seems needing 3 NICs?

satimis

---

### Post by SeijiSensei on 2014-02-25
Personally I'd just dig up some junky machine, add a network interface and Linux, and use iptables and isc-dhcp-server.  I've run such routers on i386 machines with as little as 64 MB of RAM.

---

### Post by satimis on 2014-02-25
> **SeijiSensei said:**
> Personally I'd just dig up some junky machine, add a network interface and Linux, and use iptables and isc-dhcp-server.  I've run such routers on i386 machines with as little as 64 MB of RAM.
Hi,

I don't expect running too many PCs at home.  I only have 2 PCs, a daily working PC and a spare/backup PC, each running VirtualBox with 10 VMs installed.  The spare/backup PC is NOT running all the day.

If I can install a router on a VM of the working PC then I don't need to have a physical router running all the day.  When I need to run the spare/backup PC I just turn it on.  Then it can access Internet via the routing on pfSense on the VM of the working PC. (pfSense can run on VM of VirtualBox.  I have made some search on their forum.  pfSense is BSD base.  I have spare Gigabit NIC resting on shelves)

I still have time to explore before purchasing a physical router.  The new contract for Fibre Optic network connection will start on the coming April 8.  I have made search on router.  My 1st selection will be;
NetGear N600 Wireless Dual Band Router WNDR3400 specs 
[http://reviews.cnet.com/routers/netgear-n600-wireless-dual/4507-3319_7-34169558.html](http://reviews.cnet.com/routers/netgear-n600-wireless-dual/4507-3319_7-34169558.html)

Cable router is phasing out, difficult to find a cable router with openwrt support

Rgds
satimis

---

