---
title: "DHCP clients not changing DNS servers"
date: 2013-11-18
forum: Server Platforms
---

### Post by irontech on 2013-11-18
I'm using isc-dhcp-server 4.1.ESV-R4-0ubuntu5.6 on Ubuntu 12.04LTS (server install) and have an issue with clients not picking up changed DNS server IP's.  Here's the background:

[LIST=1]
[*]Clients started out on network a.b.c.d receiving DHCP from Server A (on network a.b.c.d) pointing to DNS service on the same server, Server A
[*]I received word that we will no longer be able to keep the IP range 'a.b.c.d' and that the range must be given back to whom it was temporarily reassigned from
[*]I built a new DHCP server (the one I'm currently having the issue with), Server B (on new network w.x.y.z, which I obtained direct from an IP registrar so I don't have to give this block of IPs back)
[*]On the new DHCP server, I left the OLD DNS Server A (from a.b.c.d) IP in, so that my clients would still have DNS service while I was building them a new server on the new IP range.
[*]I changed the lease time on the old DHCP (Server A) to 5 minutes so the clients would notice the upcoming changes quickly
[*]I moved all my clients to the new network/vlan and they started getting IPs from the new DHCP server in the new range.
[*]Next, I built a new DNS server, Server C (on new network w.x.y.z)
[*]I changed the DHCP configs on the new DHCP server (Server B) to have the new DNS IP and restarted the dhcpd service
[*]Clients do not seem to pick up the change in DNS addresses UNLESS THEY REBOOT.  It does not seem to be specific to one type of client device (I've seen firewalls, wireless routers, and computers exhibiting the issue) and the clients do not have manual DNS entries.
[/LIST]
I've tried stopping the DHCP service on the old server on the old network (desperately thinking that perhaps there was some type of direct-IP communication from the clients), but that, of course, did not do anything.

Again, if I reboot the client, in my limited tests so far, this seems to remedy it and the client gets the new DNS IP.  **However, I do _not_ actually have access to the clients**, so I need to be able to force the clients to get this DNS change when they check in for their IP.

I know I must be missing something simple, I just don't know what it could be.

Below are selections from the config file:
```
ignore client-updates;

ddns-update-style none;

option domain-name "------------.com";
option domain-name-servers w.x.y.5;

default-lease-time 3600;
max-lease-time 3600;

authoritative;

log-facility local7;

subnet w.x.y.0 netmask 255.255.255.0 {
    dynamic-bootp-lease-length 3600;
    authoritative;
    ddns-updates off;
    range w.x.y.10 w.x.y.254;
    option routers w.x.y.1;
    option subnet-mask 255.255.255.0;
    option domain-name-servers w.x.y.5;
    }

```

---

### Post by SeijiSensei on 2013-11-19
If you had long lease times before, the clients won't see the change until those leases expire or they reboot.

Take a look at the dhcpd.leases file on the old server to see when the leases it gave out expire. 

Can you send all the clients an email asking them to reboot at their earliest convenience?  Sometimes direct communication with users is the best solution.

---

### Post by irontech on 2013-11-20
> **SeijiSensei said:**
> If you had long lease times before, the clients won't see the change until those leases expire or they reboot.
Take a look at the dhcpd.leases file on the old server to see when the leases it gave out expire. 
Can you send all the clients an email asking them to reboot at their earliest convenience?  Sometimes direct communication with users is the best solution.

Thank you for your response, SeijiSensei.

The old lease times on the old DHCP (whose DHCP service is off) were only 4 hours, and the new active DHCP's lease times are 1 hour, and all the clients were already picking up IP's from the new active DHCP server and requesting every 0.5 to 1 hour and using the new assigned client IP's, just not accepting a change on the nameserver IP option apparently.  That's what was so strange to me.

I decided to go in while everyone was asleep last night to try something.  Here was my procedure:
[LIST=1]
[*]On the active DHCP server, changed lease time to 2 minutes max (so I could predict when the majority of clients would be contacting)
[*]Waited for all clients to change their refresh/renew timing to the new 2-minute-max schedule (verified in logs)
[*]Removed IP scope for that network from the configuration on the active DHCP server (and restarted service) so that there was nothing to lease to that network on next renewal
[*]On the old DNS server, which is still running DNS (but not DHCP) until we get everyone weened off it, removed that subnet's ability to recurse by removing it from the recursion ACL and applied the change.
[*]Waited several minutes to make sure that all clients had attempted DHCP renewal multiple times, in hopes of them reverting to link-local or unaddressed states
[*]Restored IP scope and original 1-hour-max schedule on the active DHCP server (and restarted service)
[/LIST]

Now, in watching what IP the client machines are attempting to use for DNS this morning, there are now 73% fewer clients attempting to connect to the old DNS IP as compared with immediately prior to the above procedure.  I don't know for certain if it was the above procedure that helped, or if maybe it is coincidence, or if maybe a lot of clients were rebooted since I came in to do that, but it all made sense at the time.

As mentioned, there is the potential that what I have done is not what resulted in the improvement in my situation.  For instance, it could be that removing the range from the old DNS server's recursion ACL is just causing those clients to shuffle over to secondary DNS, but at least I'm moving in a good direction, I believe.  Plus, I would think that if the removal from the recursion ACL on the old server was just causing clients to change to their secondary, the clients would still be routinely trying the old one to see if they can revert to primary.

So, at this point, I'm thinking this might be solved, at least as much as I need it to be.  I can work with a handful of users directly to clean up the few that are left.  Since I am not certain if the procedure I used is what helped, I cannot recommend it to anyone else in the future for any particular purpose, but I am glad to be to the point at which I have arrived.

---

### Post by Doug S on 2013-11-20
I wonder if some DHCP clients are not asking for the Domain Name Server in their Parameter Request List during the renew cycle. Perhaps I am wrong, but I think asking for what DNS to use is optional.

---

### Post by SeijiSensei on 2013-11-21
I'm pretty sure Windows clients always ask for the DNS servers.

---

