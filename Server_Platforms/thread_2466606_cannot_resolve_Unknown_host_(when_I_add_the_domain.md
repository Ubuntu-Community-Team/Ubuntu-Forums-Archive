---
title: "cannot resolve Unknown host (when I add the domain to the hostname)"
date: 2021-08-31
forum: Server Platforms
---

### Post by rdcence on 2021-08-31
I'm under the assumption that my Ubuntu 20.04 internal server without a FQDN would have a default domain name of .lan  _My server in question does not have it and I'd like to correct it_.  I must have overwritten something (or did something wrong).  This server does not have a fixed ip address; it's set up for DHCP and ideally, I'd like to keep it that way. I'm looking for any and all ideas short of writing a script to fix it. 
  
When I use the commands:[INDENT]hostname
plex

hostname -d
lan

dnsdomainname
lan

sudo dnsdomainname --nis
dnsdomainname: Local domain name not set
[/INDENT]

If I ping it inside the server, it works:[INDENT]ping plex.lan
PING plex.lan (127.0.1.1) 56(84) bytes of data.
64 bytes from HOSTNAME (127.0.1.1): icmp_seq=1 ttl=64 time=0.053 ms
64 bytes from HOSTNAME (127.0.1.1): icmp_seq=2 ttl=64 time=0.068 ms
64 bytes from HOSTNAME (127.0.1.1): icmp_seq=3 ttl=64 time=0.067 ms
[/INDENT]

HOWEVER, If I ping it from outside the server (but inside the lan) I get:[INDENT]ping plex.lan
ping: cannot resolve plex.lan: Unknown host
[/INDENT]

AND if I ping the hostname, it works:[INDENT]ping plex
PING plex.localdomain (192.168.1.21): 56 data bytes
64 bytes from 192.168.1.21: icmp_seq=0 ttl=64 time=0.588 ms
64 bytes from 192.168.1.21: icmp_seq=1 ttl=64 time=0.783 ms
64 bytes from 192.168.1.21: icmp_seq=2 ttl=64 time=0.798 ms
[/INDENT]

My hosts file is:[INDENT]cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 HOSTNAME
127.0.1.1 plex.lan plex

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
[/INDENT]

My hostname file is:[INDENT]cat /etc/hostname
plex
[/INDENT]

Thanks for looking at this.

---

### Post by LHammonds on 2021-09-01
If you want machines other than the server to recognize it, you will need to look at your local DNS server.  For home environments, this is usually the Internet router which typically serves as the DHCP server as well...unless you are using a custom solution such as a Windows domain server or Linux.

But before you get into how your DHCP and DNS servers communicate to each other, make sure your clients are not just stale to the new information.  Release and renew the DHCP/DNS and test again.

LHammonds

---

### Post by rdcence on 2021-09-01
Thanks for the reply!  

When I read your post, I said to myself,  "I F!@#ing reset my router a dozen times!" plus, I've released and  renewed the IP address on the client machine as many times as well!  

However,  since I didn't put that info into my original post, I thought I owed it  to the forum to completely clear the cache on the router (in this case,  an UniFi USG). Unfortunately, clearing the DNS cache didn't help. 

BUT,  I went one step further and replaced the router with a different one  (to assign completely new IP addresses to everything within the  network).  *_With that, I humbly say you were right_*.  

Thank you for forcing me to do the extra due diligence.

---

