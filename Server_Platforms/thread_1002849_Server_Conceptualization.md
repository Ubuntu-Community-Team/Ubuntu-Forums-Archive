---
title: "Server Conceptualization"
date: 2008-12-05
forum: Server Platforms
---

### Post by ayoung on 2008-12-05
Hi all,

I have a Dapper server installed on a 10-yo G3 (Old World) Mac (powerpc). The installation was a hoot, but it's now up and running, and I'm contemplating configuration.

Basically, I want to host a personal/family website with the machine (through Django w/ Apache, mod_python, & Lighttpd, but no matter), largely for personal education reasons.  I've been through the standard setup tutorials: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) and [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/networking.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/networking.html), but I haven't been able to extract the broader picture from the details.

My primary clarification regards nameservers.  I don't _even_ want to fool with my ISP, so I intend to provide my own two nameservers: 1) with DynDNS (via communication with my router) and 2) through a DNS server running on the Mac (presumably, Bind9).  My router provides static local IP addresses, so this is not a requirement.

I've got all the port-forwarding set up (80, 443, 53 udp and tcp, ssh, etc.) but I'm a bit foggy on the details.  I feel like I keep chasing my tail with regard to /etc/hosts, /etc/hostname, /etc/networking/interfaces, and /etc/resolv.conf.

So, on to the Q's:

1) Are the 'nameserver' and 'search' domains specified in resolv.conf inbound or outbound?  My understanding is these are for the machine to resolve external IP's, not the other way around.

2) Is the name of my Bind-provided nameserver the same as the host machine?  Iow, can my hostname be 'thoreau.example.com' while my nameserver is 'ns1.example.com'?

3) In which configuration file would the URL provided by DynDNS live?

Many thanks in advance for any/all pointers, suggestions, slaps on the back of the head, etc.

---

### Post by hictio on 2008-12-05
1- Those are local only for the same server that the definitions are wrtitten.

2- I don't fully understand the question. But, yes, the hostname of the "ns1.xxx.xxxx" of your domain doesn't have to be "ns1.xxxx.xxx" (But it certainly makes things simpler on a grand scale)

3- What you mean? You mean the client that you install to keep track of the changes to your IP address? Didn't you said that the task was relegated to you router?
IIRC, the client, the Perl script goes to: '/usr/sbin/', the config file to '/etc/ddclient'.

---

### Post by koenn on 2008-12-06
2- in your dns zone file, you create an alias (aka a CNAME record) 'ns1' for 'thoreau.'. That allows you to state that the nameserver for whateverdomain.xx is ns1.whateverdomain.xx, and dnsqueries will go to (the address of) thoreau.

---

### Post by koenn on 2008-12-06
3- what URL ?
how are you planning to use dyndns ?

---

### Post by koenn on 2008-12-06
1- /etc/resolve.conf is relevant to the host ware the file resides and nothing else.
If the host in question needs to resolve a name to an address, it will use the nameserver(s) stated.
If the name to be resolved is not fully qualified (i.e. lacks a domain portion), the values of 'search' or 'domain' will be used (iirc)

inbound and outbound have no meaning in this.
one thing to consider is : will the name server stated in resolv.conf have knowledge of any host/adres (both on your LAN and outside it, i.e. internet hosts) ? If not, can it forward to another DNS server for those cases it can't handle itself ?

---

### Post by ayoung on 2008-12-06
Thanks for the feedback!  Follow-ups:

1) Okay, so it seems needless to edit resolv.conf in my situation.  Since the nameserver defaults to the IP's, I don't think I can improve on that.  Also, I've got all my local machines (four!) in my /etc/hosts file since my router assigns them static IP addresses, so I don't think I'll need a 'search' or 'domain' either.

2) Ah, the CNAME record is exactly what I was looking for!

A bind zone-related question: I've got the reverse lookup hardcoded into the "rev.xx.xxx.xx.in-addr.arpa" filename.  Is there a way to make this dynamic?  Via dhcp maybe?  Or maybe I can count on the ISP to only change the last IP bit.

3) My router ships with a feature to update DynDNS.org about any changes to the ISP-assigned IP address.  And the DynDNS service provides a URL which maps the address, although it's a subdomain of a preexisting domain.  So, since I have my own primary domain, which requires a primary and secondary nameserver, I was thinking the server itself could provide one (via CNAME!), and I could somehow tweak DynDNS to provide the other.  (Sorry if this is getting OT.)

---

