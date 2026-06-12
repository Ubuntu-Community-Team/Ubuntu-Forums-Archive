---
title: "samba, winbind, dhcp"
date: 2010-07-23
forum: Server Platforms
---

### Post by xardoz on 2010-07-23
I've had samba working on a number of servers (8.04) within an active directory domain for years but I've been struggling with a problem that has been happening for a few months now.  I also have the problems on 10.04.

Essentially, after a certain number of users have logged in, winbind falls over and has to be restarted before the latest users can access shares.  I'm certain it has something to do with dhcp leases but that could be a red herring.

I don't know what could have changed, config wise, to cause this.  I use pfsense to hand out ip addresses and act as dns server.  DNS resolution works.  Reverting back to using the dns and dhcp on the Win2k3 server doesn't help.

A typical log entry is...


[2010/07/23 07:25:55, 1] nsswitch/winbindd_ads.c:ads_cached_connection(128)
  ads_connect for domain <MYDOMAIN> failed: No logon servers

but I also get entries like...

[2010/07/20 08:17:09, 1] nsswitch/winbindd_group.c:fill_grent_mem(365)
  could not lookup membership for group sid S-1-5-21-2000478354-527237240-1801674531-512 in domain <MYDOMAIN> (error: NT_STATUS_UNSUCCESSFUL)

This is frustrating because I'm getting phone calls in the evenings and on weekends to restart the winbind daemons.  A cron job to restart them every hour or so doesn't help because the problem manifests during a logon when the drives are mapped.

Can anyone offer any suggestions?  I'd be most grateful.

---

### Post by clrg on 2010-07-23
You don't use DHCP for the servers, don't you?

Also, what is your DHCP lease for clients? Try increasing it to say, two weeks. That might slow down the problem.

I guess the service has a problem when the client's IP changes.

---

### Post by xardoz on 2010-07-23
Static IP for servers although I have also tried DHCP but with the DHCP server handing out fixed IPs based on mac address.

Lease time is 7200 seconds (default).  I've tried it up to 24 hours but AFAIK the DHCP lease is re-negotiated when the machine is booted.  This problem mostly happens in the morning as people arrive for work and turn their machines on.

---

### Post by xardoz on 2010-07-26
Any samba devs watching these forums?

---

### Post by clrg on 2010-07-26
I don't think so. Try the official Samba forum.

---

