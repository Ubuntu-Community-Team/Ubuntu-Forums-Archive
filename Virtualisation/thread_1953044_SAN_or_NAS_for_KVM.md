---
title: "SAN or NAS for KVM"
date: 2012-04-05
forum: Virtualisation
---

### Post by alfredo.marchini on 2012-04-05
Hi all,
there are some days I'm studying for a virtualization solution for about 20 guest (windows and linux).
My idea is to have 2 KVM Host and 2 HA Storage Server.

Every KVM Host with this hardware:
- 2x XEON E55* HT
- 32GB RAM

Everyone should run 10 guest machine.
Every Storage with 6TB at 6gbit/s (6TB is sufficient for all 20 guests). 
I would like to use ubuntu server for storages, as kvm hosts.

Now the problems:

1) I'm poor, so I have few money. If I have money I'll buy 2 fc or fcoe san and goodbye everyone.

2) Communication between kvms and storages: I read in many sites that many use nfs or iscsi on dual/quad port gbit ethernet card. If I use quad port with bonding in load-balancing, I reach about 1.2-1.5gbit/s, so far from 6gbit/s. And If I buy an FC card at 8gbit/s, can I configure it as a network card or can I configure my ubuntu server as a SAN (blockdevice instead a filesystem)?

3) Which filesystem can I use in my storage to replicate and share my storages (ocfs2?)

As you can see how you can see I'm a bit confusing. So any idea would be very appreciated.
Thank you very much.
Bye

---

### Post by TheR on 2012-04-06
This is by far the cheapest 8-port > 10Gb switch you can buy. [http://www.colfaxdirect.com/store/pc/viewCategories.asp?pageStyle=m&idcategory=7&SFID=5&SFNAME=Fabric&SFVID=23&SFVALUE=Infiniband+QDR&SFCount=0](http://www.colfaxdirect.com/store/pc/viewCategories.asp?pageStyle=m&idcategory=7&SFID=5&SFNAME=Fabric&SFVID=23&SFVALUE=Infiniband+QDR&SFCount=0)

Althow I heard infiniband is kinda tricky to work with. I have 6 port HP 10Gb Ethernet, which is twice expensive and it works like charm.

I am using iscsi with LVM as SAN, but don't have second (redundand) iscsi server.

by
TheR

---

### Post by alfredo.marchini on 2012-04-07
Hi,
searching for the web I never found a switch so cheap. Very Good.
But I have other news about my project:

1) I prefer a filesystem storage and not a blockdevice storage.
I know that block device is faster, but is more dangerous: with a filesystem storage I can move inside a filesystem for many purposes. I want to use Lucid or Pargolin to make storage so I prefer to have a filesystem which I can navigate.

2) In my office, for other purposes, I have a server with the same hardware that I want to use for my 2 storages, except for the network cards (2x integrated broadcom 1gbit) and the raid-5 disk size (1TB not 2Tb and I think worse disk quality). I tested nic and raid controller:

- RAID-Controller (6gbit/s) read 273,14 MBytes/s - (with hdparm -tT) so about 2.1Gbit/s.

- 1x BroadCom 1Gbit about 75Mbytes/s (not remember the test I made). So 600Mbit/s.

So 4x Broadcom with native teaming, If the teaming is packet based and not session based (I don't know it), It should be sufficient for this raid controller speed.

But I want to be prepared for the next future so If my customer after 2 years want to buy SSD SATA III disk the controller can be acceptable but the network would be the bottleneck.
So I started searching new NIC 10GbE and I found 2 models of Intel:

[http://ark.intel.com/products/60020/Intel-Ethernet-Controller-X540-AT2](http://ark.intel.com/products/60020/Intel-Ethernet-Controller-X540-AT2)

and this:

[http://ark.intel.com/products/58954/Intel-Ethernet-Converged-Network-Adapter-X540-T2](http://ark.intel.com/products/58954/Intel-Ethernet-Converged-Network-Adapter-X540-T2)

The price is different (the first Intel says 125$, the second I find in other sites about 600$).
The difference I think is the CNA and FCoE that the first don't support. But If the first is so cheap and every port gives me about 3Gbit/s and I make teaming I have at least 6Gbit/s.


But now I have another question:
This slot PCIe v2.1 (5.0GT/s) will support this speed?
And can I use these cards as normal network card with ip address and network file system?

Thank you very much
Bye

---

