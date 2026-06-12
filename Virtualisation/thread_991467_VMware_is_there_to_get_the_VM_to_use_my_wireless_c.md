---
title: "VMware: is there to get the VM to use my wireless connection as eth0?"
date: 2008-11-23
forum: Virtualisation
---

### Post by Pitt Stains on 2008-11-23
Hello,

I have a VM that runs Ubuntu Server, which previously sat on a server that was connected to the network via ethernet.  I made a copy of that VM and put it on my laptop, which makes connects to the network wirelessly.

When hosted on the server, the VM would get its own static IP address.  On my laptop, the VM doesn't get any connection, or any IP address for that matter.  I suspect this is because it is looking at the host machine's eth0 for its connection.

Can anyone suggest a way to get the VM to look to wlan0 instead?  Or suggest a better solution?

Thanks,
- Pitt

---

### Post by bodhi.zazen on 2008-11-23
What version of Ubuntu ? What version of VMWare ? How did you install VMWare ?

More important, did you use the "any-any" update ?

VMware will use wireless cards, so my initial guess would be your VMWare install or configuration.

---

### Post by Pitt Stains on 2008-11-23
> **bodhi.zazen said:**
> What version of Ubuntu ? What version of VMWare ? How did you install VMWare ?

More important, did you use the "any-any" update ?

VMware will use wireless cards, so my initial guess would be your VMWare install or configuration.

The host is running Ubuntu Desktop 8.10.  The VM is running Ubuntu Server 7.10.  VMware is ver 1.0.8.  I installed normally, except that I answered "no" when asked to run vmware-config.pl.  Then I ran this patch ([http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627)), which patches and runs vmware-config.pl.

If it's just a config issue (which I hope is the case), then I guess I've missed the config option that allows me to set it this way.  Could you please point me in the right direction?

---

### Post by lkness on 2008-11-24
VM Server doesn't support the use of wireless connections with bridged network adapters. You will need to use the NAT adapter. 

This has to do with how the wireless protocol is laid out for security reasons. I do believe that VM Workstation might support bridged to a wireless adapter.

---

### Post by lkness on 2008-11-24
I should add one thing else. I am running VM server 1.07, but according to the docs on VM Server 2.0, you are suppose to be able to use the wireless for bridged. But i've not tried it (2.0).

---

### Post by Pitt Stains on 2008-11-26
Thanks, lkness.  Hmmm, I tried the NAT setting but when I do:

```
sudo ifup eth0
```

... I get this:

```
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit, http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

```
In any case, I think I need a separate IP for the VM anyway, as I'm using it to develop code and have, until now, been typing its IP address into Firefox to check for errors, etc.

I guess I'll try VMware v2, though I really didn't like the interface the last time I test drove it.

---

