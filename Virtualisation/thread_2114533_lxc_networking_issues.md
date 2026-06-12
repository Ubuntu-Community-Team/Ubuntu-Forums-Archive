---
title: "lxc networking issues"
date: 2013-02-10
forum: Virtualisation
---

### Post by crush_157 on 2013-02-10
Hi All,

Just starting out with lxc containers.

I'm running xubuntu 12.10, and started out by creating a VirtualBox VM also xubuntu 12.10 as a test bed.

I installed lxc, used lxc-create and lxc-start and got a container running within the VM.

I did an ifconfig and the container within the VM had ipv4 and ipv6 addresses.  I then succesfully ssh'd into the container from the VM.  Cool.

So then I did the same on the physical Xubuntu box and found that the container now only has ipv6 address and I can't ping6 to it or connect to it in any other way over the network.

A bit of googling around turned up this [http://s3hh.wordpress.com/2011/05/17/lxc-containers-on-a-host-with-wireless/](http://s3hh.wordpress.com/2011/05/17/lxc-containers-on-a-host-with-wireless/) which was interesting (I've been succesfully connecting VirtualBox VMs using bridged mode on WiFi for years!!!).  I followed the steps described and succeeeded only in disabling both the WiFi and Wired NICs on my PC.

So, I was wondering if anyone could advise me how to set up lxc networking on a physical box with WiFi?

Explanations in words of one syllable much appreciated.

Cheers,

Crush_157

---

