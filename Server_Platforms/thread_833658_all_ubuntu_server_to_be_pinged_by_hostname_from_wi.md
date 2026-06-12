---
title: "all ubuntu server to be pinged by hostname from windows clients"
date: 2008-06-18
forum: Server Platforms
---

### Post by tr333 on 2008-06-18
How can I setup my ubuntu server to be pinged from Windows clients, without having to add the server hostname to the hosts file of each Windows computer?

---

### Post by artesvida on 2008-06-19
Do you have a server doing DNS?  Does your Ubuntu server have a statically assigned IP address?

---

### Post by gtdaqua on 2008-06-19
Create "A" records for your Linux hosts (or any hosts) on your Windows DNS server. Your clients must use this Windows DNS server for name resolution. 

Usually in a Active Directory environment, if you have a domain called example.com and your Linux hostname is "dapper", then your "A" record you have to create will automatically be "dapper.example.com" -> this also becomes the the FQDN of the dapper host. Your XP clients should be able to ping just by "dapper" or "dapper.example.com".

Then subsequently you can create "CNAME" records if you want aliases for the "dapper" host.

---

### Post by tr333 on 2008-06-19
Thanks.  Need to talk to the admin of the DNS server now :)

---

### Post by artesvida on 2008-06-19
> **tr333 said:**
> Thanks.  Need to talk to the admin of the DNS server now :)

Not necessarily.  If your Ubuntu server is using DHCP to get it's IP address, you can include the following lines in your /etc/dhcp3/dhclient.conf file:

```
send fqdn.fqdn "hostname.domain.com";
send fqdn.encoded off;
send fqdn.server-update off;
```

Thes are the options I'm using for my Windows DHCP/DNS server.  They may need to be a little different for a Linux/Unix DHCP/DNS setup.

---

### Post by tr333 on 2008-06-21
> **artesvida said:**
> Not necessarily.  If your Ubuntu server is using DHCP to get it's IP address, you can include the following lines in your /etc/dhcp3/dhclient.conf file:

```
send fqdn.fqdn "hostname.domain.com";
send fqdn.encoded off;
send fqdn.server-update off;
```

Thes are the options I'm using for my Windows DHCP/DNS server.  They may need to be a little different for a Linux/Unix DHCP/DNS setup.

The server is running on a static IP.

---

