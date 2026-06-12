---
title: "No Network after install of vmware"
date: 2008-07-08
forum: Virtualisation
---

### Post by mustava on 2008-07-08
Hi, Ubuntu 8.04 running and all ok, wired network eth0.
Installed vmware and installed xp as virtual machine.

Now ubuntu doesn't seem to have a network, but the ip address etc; is ok, but can't browse local network nor the internet.
Pings all fail

If I run vmware and xp, network ok and internet ok.
pings work ok

Help please.

---

### Post by fjgaude on 2008-07-08
In vmware do you have the net connection set to NAT?

---

### Post by mustava on 2008-07-08
No, its set to bridged.

---

### Post by 4Play on 2008-08-01
I have the exact same problem...was running ubuntu 8.04 fine, with wireless and wired internet. Installed VMWare Workstation 6.0.4, and Installed XP Pro (SP2), now I cant open any sites in ubuntu (or xp)...it says it's connected to the networks, acquires a IP, and I can ping the router (192.168.1.1), however, all other pings fail and sites don't even "try" to load, they fail as if I did not have a DNS..

have tried setting the VMWare network settings to NAT, Bridged, even private network...nothing worked...

I *think* the problem is that VMWare created a virtual network adapter in linux (as it does on its windows counterpart) and for some odd reason, Ubuntu is using this adapter to try to open sites..however, I do not know how to verify my suspicion...

Any help here would be greatly appreciated

---

### Post by 4Play on 2008-08-01
Problem solved!!:):)

I read some of the VMWare manual (helps sometimes..) and ran sudo vmware-config.pl

this reconfigured the whole VM, and apparently something went wrong in the initial configuration (during the installation) and messed up my internet, i simply followed most of the default steps, and got my connection back, it's working in the virtualized XP as well, so this is a nifty tool for reconfiguring your VM in case something went wrong the first time...

update: even after doing this, after a reboot, I would loose internet connectivity. To resolve this, I ran vmware-config.pl again, and got my connection back, then I ran it *again*, without restarting, because in order for it to configure the NAT virtual adapter correctly, it seems it needs a functional internet connection to be present (so it can probe for an available subnet)

anyway, that's it...i hope this may help somebody who is experiencing similar issues.

---

