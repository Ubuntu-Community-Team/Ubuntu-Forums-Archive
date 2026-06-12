---
title: "Difference between DNS and /etc/hosts"
date: 2008-12-17
forum: Server Platforms
---

### Post by Yardarm on 2008-12-17
I'm setting up kerberos authentication on my 8.04 server and have a fully functional DNS server, but in order to run kinit with my created administrator account I need to add a non-loopback IP (i.e. 192.168.0.2 instead of 127.0.1.1) to my server in /etc/hosts.  Otherwise I get an error along the lines of: cannot find a valid KDC on realm 'EXAMPLE.COM'

I can't wrap my head around why /etc/hosts is involved here instead of DNS.  I figure it's because I don't understand some fundamental difference between the two.  Can anyone explain?

---

### Post by lensman3 on 2008-12-18
Before there was DNS there was /etc/hosts.  When hosts was conceived there was no Internet and most networks were 5 MHz Coax.  It was simple enough to enter all the networks hosts (and aliases) into one file per machine and keep everything updated.

Take a look at /etc/ethers.  When the networks were simple the NIC numbers were entered into /etc/ethers with the IP number. Do a "man ethers".

About the same time the "resolver" was introduced to get a hostname from an IP address. It uses "/etc/host.conf" to determine how domain names are added to a host name and where to look up DNS servers.  The host.conf on my system has "order hosts,bind".  This tells the resolvers to look in /etc/host and then bind (the traditional name for DNS and named) to find the IP address.

Hope this helps a little.  This was all cobbled together in the early networking days without much foresight.

---

### Post by Yardarm on 2008-12-18
Thanks.  Yeah that does help. So DNS *is* supposed to be a complete replacement for /etc/hosts.  I've read that kerberos is supposed to have some extra DNS lines of the SRV and TXT variety in order to resolve the KDC service.  Although to this point I haven't gotten those to actually work, it does explain why the /etc/hosts line worked while DNS didn't.  Thanks.

---

### Post by gpredrag on 2008-12-18
both /etc/hosts and dns are involved in name to address or address to name resolving.
You can check /etc/nsswitch.conf, there you can see (probably) something like:

hosts: files dns


wich means that hostname resolution will be tried with /etc/hosts and then with dns.

on workstations name resolving also includes multicast dns, so one can resolve somehost.local by name with no fuss in small networks.

Putting entries in hosts files still makes sense for very important hosts that should be resolvable even if DNS is temporarily down.

Also, Linux determines it's own DNS domain by resolving its address into name, and starts by looking in /etc/hosts/ first.

Kerberos can work without specific SVR entries in DNS (will use them if avaliable for locating KDC), but it is, in my experience, much more important to have proper A records for forward zones, and PTR records in reverse lookup zones for all kerberos enabled servers.
I guess that you actually solved reverse lookup problem by putting that entry in hosts file.

---

