---
title: "Nessus: OShare and DNS"
date: 2007-11-22
forum: Server Platforms
---

### Post by kooseefoo on 2007-11-22
Okay, I just ran a nessus scan on my network. Note that ths scan was done through my domain name, so it should have been from a perspective outside my network.

Here's the basic setup: I have a linksys WRT54G router running DD-WRT (3rd party software). Behind that, and with a few ports forwarded through the router too it like 21, 22, 80, 443, etc... I have my ubuntu server. There are two things in the nessus security report that I could use a little help understanding:

The first is a mention of a vulnerability to an oshare attack. I have searched around on these forums and on google, and all I can find out is that it's a DoS attack that I'm vulnerable to. How can I fix that?

The second is this:
```

(53/udp)|10539|Security Warning|
Synopsis :

The remote name server allows recursive queries to be performed
by the host running nessusd.


Description :

It is possible to query the remote name server for third party names.

If this is your internal nameserver, then forget this warning.

If you are probing a remote nameserver, then it allows anyone
to use it to resolve third parties names (such as www.nessus.org).
This allows hackers to do cache poisoning attacks against this
nameserver.

If the host allows these recursive queries via UDP,
then the host can be used to 'bounce' Denial of Service attacks
against another network or system.

See also : 

http://www.cert.org/advisories/CA-1997-22.html

Solution : 

Restrict recursive queries to the hosts that should
use this nameserver (such as those of the LAN connected to it).

If you are using bind 8, you can do this by using the instruction
'allow-recursion' in the 'options' section of your named.conf

If you are using bind 9, you can define a grouping of internal addresses
using the 'acl' command

Then, within the options block, you can explicitly state:
'allow-recursion { hosts_defined_in_acl }'

For more info on Bind 9 administration (to include recursion), see: 
http://www.nominum.com/content/documents/bind9arm.pdf

If you are using another name server, consult its documentation.

Risk factor :

Medium / CVSS Base Score : 5.0
(CVSS2#AV:N/AC:L/Au:N/C:N/I:P/A:N)
CVE : CVE-1999-0024
BID : 136, 678


```
Yea. I have no idea what it's talking about. The only thing that could be responding to port 53 requests would be my router. I am inside the network, but I ran nessus on my outside IP, so that shouldn't matter, should it? There is no DNS server running on my server inside my network.

---

### Post by koenn on 2007-11-23
DNS cache poisoning is a trick to make DNS servers give wrong addresses - eg your browser requests the address of google.com but it receives the address of badserver.net, so your browser goes to badserver.net, where possibly a web page with some malicious javascript is waiting, or a fake login page to find out what your google account credentials are, etc ... 

If you're using a DNS server that you don't control yourself (eg your ISP, ...) it's not a problem you can fix.you might consider an alternative DNS server, eg  OpenDNS.

---

