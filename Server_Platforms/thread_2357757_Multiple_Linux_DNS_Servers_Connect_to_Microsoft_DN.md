---
title: "Multiple Linux DNS Servers Connect to Microsoft DNS Server"
date: 2017-04-05
forum: Server Platforms
---

### Post by rickinfl on 2017-04-05
Hi,

I have 5 Linux Servers at 5 different locations and a main Microsoft AD Server at 1 location. I want to install DNS on each server and sync to the main Microsoft AD DNS server. I would like for each location to download DNS records so that if my connection from a branch location breaks from the Microsoft AD DNS server that branch can still resolve DNS.




Thanks,

---

### Post by wildmanne39 on 2017-04-05
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-04-05
> **rickinfl said:**
> 
I have 5 Linux Servers at 5 different locations and a main Microsoft AD Server at 1 location. I want to install DNS on each server and sync to the main Microsoft AD DNS server. I would like for each location to download DNS records so that if my connection from a branch location breaks from the Microsoft AD DNS server that branch can still resolve DNS.
Make all the branch location servers secondaries to the primary AD server.  When the AD's records change, it will notify the branch servers which will download and update their records.

I have no clue how to configure the primary with Microsoft DNS.  With BIND9 on Linux, the secondaries will have entries like this in their named.conf files:
```
zone "example.com" {
     type slave;
     masters { 10.10.10.10; };
     file "example.com";
};

```
The file name is up to you.  I name the local zone files with the same name as the domain for easy reference.

You may, or may not, need to tell the Microsoft server that the remotes can transfer domain records. On Linux, in named.conf, you'd have a line like
```

     allow-transfer  { 
          10.10.10.11; 
          10.10.10.12;
          etc.
     };

```
that would let 10.10.10.11, 10.10.10.12, etc., download the records from the Microsoft server.  I presume the AD server has a similar setting.

In the zone file for "example.com," make sure that all the secondaries are listed with NS records:
```

@    IN     SOA    etc.

     IN     NS     10.10.10.11
     IN     NS     10.10.10.12
     etc.

```

---

