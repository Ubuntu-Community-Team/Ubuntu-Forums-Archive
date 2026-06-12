---
title: "ubuntu headless server &amp; cli firewall question"
date: 2009-01-07
forum: Server Platforms
---

### Post by django_sr on 2009-01-07
Hi Ubuntu peeps,

I've downloaded and installed Ubuntu 8.10 server edition on my via c3 CPU system, which I will use as a headless file and print server.

I've chosen to install cups, nfs and samba because other *nix clients should have their home directory the same on all pc's on my network. I'll be expecting some windows clients as well and would like them to be able to browse files on my network and be able to print from their windows pc's to the print server.

Because I'm rather paranoia, I would like to lock down the machine with a good firewall application. I'm from the BSD world and am used to PF but here I'm presented with UFW.

Every time my server boots I would like it to read my firewall configuration file and make sure that:

1) everything is blocked in both directions
2) only port 631 is open for cups
3) only the relevant ports are open for NFS and Samba
4) allow ssh

How do I accomplish this?

I guess my question boils down to this:

If I enable SSH like this:

sudo ufw allow 22

Will it still be enabled after a reboot or do I have to re enable it once more?

Thanks in advanced

---

### Post by cdenley on 2009-01-07
UFW configuration is persistent. It does not filter outbound traffic, only inbound. On the rare occasion I need to use iptables, I setup my rules manually, then create my own script to load those rules.

---

### Post by django_sr on 2009-01-08
Perfect!
Thanks, I will try working with ufw then.

I'm a little reluctant to learn iptables as I'm happy with PF, but upgradability, CUPS and hardware support have convinced me to sacrifice some functionality in the security area (would have installed opensd on this machine). Hope I don't regret it, but would love to have a install and kind of forget file & print server.

Thanks again.

---

### Post by kamaji792 on 2009-01-08
I appreciate this is not much help but there is a way of setting iptables rules that are run before UFW comes up (and I think the same can be done for after).

Look in the /etc/ufw directory where the ufw configuration files are stored.

ATB

---

