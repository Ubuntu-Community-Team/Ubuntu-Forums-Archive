---
title: "Could not reliably determine the server's fully qualified domain name"
date: 2011-06-22
forum: Server Platforms
---

### Post by DeMartini on 2011-06-22
How do I put the FQDN in the etc/hosts file, 
server ip is 192.168.2.101
hostname - promisedland
fqdn - promisedland.dyndns.org

I just want to set up a web based file server, thanks....

Here is what i put in hosts (/etc)-gedit

127.0.0.1	promisedland
192.168.2.101   promisedland

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by BkkBonanza on 2011-06-22
If you are using a domain name on dyndns.org then I assume you want to use it's dynamic IP ability and in that case you should not add the name to your hosts file. Adding it their will prevent the name from being useful when it's IP changes (which is the whole purpose of dyndns.org).

In other words, the hosts file is only useful for names where the IP will never change. When the IP can change (typical ISP connection) you need to rely on a DNS server not the hosts file.

Also, you do not want to add a name twice as in your example above. If you do have a fixed IP for that name then your second line is more correct (well, it needs to have the full name not just the domain, and it should have the public IP not the local network IP). The one with the 127.0.0.1 should be removed.

Your hostname is different from the domain name that public users can use to access your server. If you use DHCP on your LAN then your router will usually take care of resolving local names and is a better idea than using your hosts file. Sometimes you need to enable a DNS (relay) on your router for that to work.

---

### Post by bab1 on 2011-06-23
> **DeMartini said:**
> How do I put the FQDN in the etc/hosts file, 
server ip is 192.168.2.101
hostname - promisedland
fqdn - promisedland.dyndns.org

the /etc/hosts file is for local (to this host) dns lookups only.  The FQDN of the host is not relevant in this case.  You can add it as an alias AFTER the hostname listing in the /etc/host file I suppose.  Why do you think you need it.

The /etc/host file would look like this
```

127.0.0.1 localhost
192.168.2.101 promisedland promisedland.dyndns.org

```
More to the point you need to have dyndns.com point to your WAN side address.  Then you need to configure your router to port forward the requests to your server.
> 
I just want to set up a web based file server, thanks....

Here is what i put in hosts (/etc)-gedit

127.0.0.1	promisedland
192.168.2.101   promisedland

As BkkBonanza has said: You should not map the hostname to 2 IP addresses.  The 127.0.0.1 address is local loopback anyway.

---

### Post by DeMartini on 2011-06-23
I appreciate your help, i have been running linux for the past several years & just trying to go to the next level.

I am going to reinstall Server 11.04, include all the bells & whistles i.e. apache,php etc.. I WILL NOT add hostname to etc/hosts file (thanks again)

My goal is to have a web server that links to my second hdd that has a ton of media I want to share

If anyone has done this can you please point me in the right direction, I have done it w/ Windows and i really don't wanna go back..

---

