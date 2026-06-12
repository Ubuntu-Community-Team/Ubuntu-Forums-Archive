---
title: "NAT networking woes"
date: 2010-01-11
forum: Virtualisation
---

### Post by mtbighorn on 2010-01-11
First and foremost this may not the "best" venue to post this question but I am at about wits end.

Here is my current physical network topology.

10.1.0.0 Network
255.255.0.0 Subnet
10.1.0.1 DG

I have vmware server running on my machine and the bridged networking works like a champ, however I do not want (read cannot) to run my virtuals are a member of my physical network.

This is where I begin to have some troubles ... I want my virtual to reside in an isolated network inside my physical machine.  I do not really care what the ip/subnet are as for this situation there will be only 1 virtual on this physical.  However, I want my virtual to be able to talk to both my 10.1.0.0 physical network, and the internet beyond my edge router.  

Is this possible?

---

### Post by herda05 on 2010-01-26
It should be. Works fine in ubuntu 8.1

I just installed Vmware Server 2 on Ubuntu 9.1 and my host can't ping any of my guests. Something seems to be wrong with Vmware Server in ubuntu 9.1 that has broken networking.

---

### Post by flushmylog on 2010-02-22
> **herda05 said:**
> It should be. Works fine in ubuntu 8.1

I just installed Vmware Server 2 on Ubuntu 9.1 and my host can't ping any of my guests. Something seems to be wrong with Vmware Server in ubuntu 9.1 that has broken networking.

I have a similar problem:
Ubuntu 9.1 (2.6.31-19-generic), vmware server 2.0.2.

Ubuntu Host cannot ping vmware guest (XP)
No matter which network the guest is set to use, Bridged, HostOnly or NAT.
The guest can however ping the host just fine...

Also cannot copy paste between host and guest.

XP's firewall is disabled, as well as the AV.

I know vmware server 2.0.2 on 9.1 has several issues, but I've followed this link to get the install sorted.
[http://risesecurity.org/2010/01/10/vmware-server-2-0-2-update-patch/]("http://risesecurity.org/2010/01/10/vmware-server-2-0-2-update-patch/")

Doing a 
/etc/init.d/vmware status 
shows Host network detection is not running.
Not certain if this is the root of my problem.
Don't have a working system to compare to.

Anybody else out there suffering the same problem?

~$ /etc/init.d/vmware status
At least one instance of VMware Server is still running.

Bridged networking on /dev/vmnet0 is running
[COLOR="Red"]Host network detection is not running[/COLOR]
Host-only networking on /dev/vmnet1 is running
DHCP server on /dev/vmnet1 is not running
Host-only networking on /dev/vmnet2 is running
DHCP server on /dev/vmnet2 is not running
NAT networking on /dev/vmnet2 is running
Host-only networking on /dev/vmnet8 is running
DHCP server on /dev/vmnet8 is not running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded

---

