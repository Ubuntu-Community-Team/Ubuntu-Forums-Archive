---
title: "Ubuntu 8.04 + VMware Server 2.0  + VLANs."
date: 2008-10-07
forum: Virtualisation
---

### Post by barnys on 2008-10-07
Has anyone had luck with Ubuntu 8.04 and Vmware Server 2.0 using vlans?

I am running vmware server fine, but I had a need of enabling VLANs and bridging virtual machine NICs to VLAN interfaces.  I receive no error messages or anything at all, but the setup simply doesn't work. 

When I tcpdump the physical interface and/or VLAN interfaces (eth1 and eth1.10) I see no traffic coming from the virtual machine at all. 

I have also attempted to enable promiscuous mode in the NIC to test, but I experience the same. 

I know that the VLAN interface(s) created work, because I can send receive traffic via the host OS vlan interface.

Any ideas or pointers?

---

### Post by HermanAB on 2008-10-07
Nope, but I'd love to know what you did once you get it working...

Cheers,

Herman

---

### Post by barnys on 2008-10-07
I certainly will post my findings.  I have been trying now for days.  
It works with no problems whatsoever in CentOS, RedHat, Suse... however I haven't tried Debian to see if it happens like in Ubuntu.

---

### Post by pogenstad on 2008-10-13
I found this thread while troubleshooting this myself. You might have solved it already but if not I found a solution which worked for me.

After doing a Google search on the errors from dmesg (can't bridge with vlan40, bad header length 18 ) I found a post over at Vmware:

[http://communities.vmware.com/thread/112709?tstart=449](http://communities.vmware.com/thread/112709?tstart=449)

I edited the file as 'eot' described in his third post, only changing the line number. In the file on my system it was on line 969. After saving and recreating vmnet.tar I ran vmware-config.pl. However this didn't recompile the modules, I think this was default in Vmware Server 1.0. I noticed that vmware-config.pl has a -compile switch. So now all my VLANs work again. :)

Good luck!

---

### Post by barnys on 2008-10-17
pogenstad:  thanks so much for posting this entry. 

As a matter of fact I had been waiting a few days before going at it again.  I followed these steps and everything works. 

Now I didn't experienced this problem with CentOS 5.2 host server, the bridged-VLANs worked perfect there.

Cheers,

/Barny

---

### Post by angus.hendrick on 2008-12-04
I'm running vmware-server under Ubuntu 8.04 and trying to bridge to my wireless card, configured as ath0, from a 32-bit XP Pro guest.  I tried the fix linked in the above post and after the rebuild, it still doesn't work.

The system summary tab says that the supposedly bridged interface has an ip, and running ipconfig in a prompt confirms it, but the ip is not a good one from my router and ping [www.google.com](www.google.com) fails.  

There is also an error in the events page saying that the vm could not connect to the vlan that bridges to the card, which explains the fact its not working, but where's the ip coming from?

Any thoughts/suggestions for solving/troubleshooting this beast?  I need a kick to get moving in the right direction.

---

### Post by lightenup on 2010-04-04
Perfect!! Thanks for the post, I almost gave up on tagged interfaces for VMware Server 2.0!! I just want to post this info here as the original post on the VMware forum was from 2007 and it does not refer to either Vmware 2.0 or Ubuntu 8.04:


Symptom: 

You have created your vlan tagged interfaces as per [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan) but when you start vmware server you see the following errors messages in dmesg:

[  641.756857] /dev/vmnet: port on hub 2 successfully opened
[  641.756868] bridge-eth1.20: can't bridge with eth1.20, bad header length 18
[  641.756873] bridge-eth1.20: enabling the bridge
[  641.756874] bridge-eth1.20: can't bridge with eth1.20, bad header length 18
[  641.756877] bridge-eth1.20: interface eth1.20 is not a valid Ethernet interface
[  641.756879] bridge-eth1.20: attached

Workaround:

This needs to be fixed by vmware, but the following will resolve this:

unpack /usr/lib/vmware/modules/source/vmnet.tar to a working directory
in vmnet-only edit bridge.c
on or around line 900 change line:

if (bridge->dev->hard_header_len != ETH_HLEN) {

to:

if (bridge->dev->hard_header_len != ETH_HLEN && bridge->dev->hard_header_len != ETH_HLEN +4) {

save, pack vmnet-only to vmnet.tar and put back in /usr/lib/vmware/modules/source

re-run vmware-config.pl to rebuild the kernel modules.



LiGHT

---

