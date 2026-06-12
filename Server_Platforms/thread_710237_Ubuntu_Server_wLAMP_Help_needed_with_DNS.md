---
title: "Ubuntu Server w/LAMP Help needed with DNS"
date: 2008-02-28
forum: Server Platforms
---

### Post by tet3828 on 2008-02-28
I have the latest version ubuntu server with LAMP and Webmin on a box in my office.

Any Windows computer nationwide within our companies network can access the server and the php scripts via firefox/explorer address bar by typing its ip address: 10.0.11.xxx. Perfect!

but I need to be able to access the server files (www folder) using a name like clinical.apps.com. I understand DNS handels linking ips to Names. I tried tooling around with some DNS zones and stuff within Webmin. but no luck. does anyone know of a doc to direct me to or maybe a few simple steps I can take to make this happen?

thanks!

---

### Post by BaseRunner on 2008-02-28
Hi,

maybe I see this too simple; to make any system be able to access your server using a name instead of an IP address you just have to register your server to your company's dns servers. There is nothing you have to change locally.
If you also want to connect to others using names on your system you have to modify two files:
- /etc/resolv.conf where you specify your name servers' addresses and your company's domain name
  sample entries
nameserver 10.1.1.1
nameserver 10.1.1.2
domain mycompany.com
- /etc/nsswitch.conf where you tell the system libraries to use dns resolution
  add dns to the line that defines the hosts resolution:
hosts: files dns

Does that make sense to you?

Cheers
Batta

---

### Post by rapiscan on 2008-02-28
I'm not sure if you already have your answer, but I thought I'd try to explain in a little more detail.

The Domain Name System (DNS) allows for other computers (hosts) to access certain records of information about a domain.  For example, a couple of the most important records that are stored are the mail servers for a given domain, and the IP address for a given domain.  

DNS can get rather complicated.  It's hierarchical system with caching to decentralize the resources need for name resolution.  All of that doesn't really matter to you, but you can read about it more here if you want: [http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)

When you register a domain, you are asked to provide two authoritative nameservers for that domain.  An authoritative nameservers has the right to set the different records for a given domain.  So basically, it's the official source of the records for your domain.   This is where other computers come to figure out the IP address for your server. 

So to get mycompany.com to point to your particular ubuntu server, you first need to have a nameserver.  If you do already have a nameserver at your company and the domain registerd, just use these nameservers for the domain and have your namserver administrator add the necessary records to point to your IP address.

If you don't already have a nameserver accessible, you can use BIND to make your own. Here is a thread with a how to:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

Two nameservers are required for redundancy, in case one of them is down or inaccessible for any reason.  Many people get around this by just using two different IP addresses that point to the same nameserver.

---

### Post by GNUrag on 2008-02-28
To add to rapiscan's message, if you wish to use free third party DNS providers then give  EveryDNS ([www.everydns.org](www.everydns.org)) or Xname ([www.xname.org](www.xname.org)) a try.

---

