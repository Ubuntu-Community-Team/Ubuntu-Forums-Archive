---
title: "Local DNS pulled from KVM?  And maybe real hosts?"
date: 2013-10-06
forum: Virtualisation
---

### Post by 1clue on 2013-10-06
Hi,

This is the landscape at my home office:
[LIST=1]
[*]Cisco wireless AC router.
[*]Windows 8

[*]Windows Vista

[*]Mac OS X with Parallels VMs:

[LIST=1]
[*]Windows

[*]Linux, about 6 copies.
[*]Mostly NAT, two bridged.
[/LIST]

[*]Linux with KVM VMs:

[LIST=1]
[*]FreeNAS

[*]12 machines and counting of various Linux distros, some of which are for testing and only come up occasionally and others of which are up continuously for services.
[/LIST]

[*]Android phones.
[*]A couple BluRays and one smart TV.
[/LIST]


Characteristics right now:

[LIST=1]
[*]On the KVM host, I can reference the guests by the name in /etc/hostname on the guest.  For example, I can **ssh buildbox** and it knows where buildbox is, even though everything is working by dhcp.  I'm using bridged networking mostly.
[*]I have a pretty good Cisco router, and it sees the names of real PCs but it's not picking up the VMs.
[*]I have the VMs all configured by dhcp, and want to keep it that way so when I clone one or move to another network (with the Mac laptop for example) I don't run into problems.
[/LIST]

Here's what I would like advice on:
[LIST=1]
[*]I want to be able to have a local-only DHCP+DNS, and I want it to see virtual machines which use bridged mode networking from any device on the network.
[*]I would like the DNS to get the name in /etc/hostname (or the cpu-supplied computer name for non-Linux systems) automatically applied.
[/LIST]

I have experience with dhcpd and with named, but I never got DNS entries to follow the DHCP allocation, and I don't know how to make it be local network only.

A HOWTO would be fine, if somebody knows something.

Thanks.

---

### Post by CharlesA on 2013-10-07
I don't have a Cisco router, but I've always had to do dhcp reservations in order to get DNS to resolve correctly.

---

### Post by 1clue on 2013-10-07
Hmm.

I'm torn between typing in reservations on that router, or on setting up my own dhcp and dns.  I'd like to be able to hit all the hosts by name without a fuss, but it seems I can't do it.

Still hoping somebody will step in and give me a dhcp+dns solution for a local network that's easy to use.  I've tried a bunch of things out and am sick of it.  The only thing I was ever happy with was the full-blown office setup, and I don't want to have it propagate.

Thanks for the response.

---

### Post by CharlesA on 2013-10-07
I am using DNSMasq on my router (DD-WRT) for DNS and DHCP and it seems to work well, but it's still a lot of typing to do.

---

### Post by 1clue on 2013-10-07
I used DD-WRT at one point, but it was buggy for my router.  After waiting over a year, they never came up with a new build for it, so I moved on.

My current external router does what I need it to do, and I don't really see a reason to install DD-WRT on it.  Maybe if I start going nuts with accessing internal devices from outside I might go with dd-wrt again, or more likely I'd just put a host behind it that and have that do the complicated stuff.

---

### Post by btindie on 2013-10-10
Take a look at [http://blog.bigdinosaur.org/running-bind9-and-isc-dhcp/](http://blog.bigdinosaur.org/running-bind9-and-isc-dhcp/) which seems to be quite detailed.

Note on RHEL, you need to specify "DHCP_HOSTNAME=" in /etc/sysconfig/network-scripts/ifcfg-eth0 to get it to register it's hostname. See /usr/share/doc/initscripts-*/sysconfig.txt

---

