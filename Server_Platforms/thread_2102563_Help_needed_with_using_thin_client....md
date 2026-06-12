---
title: "Help needed with using thin client..."
date: 2013-01-07
forum: Server Platforms
---

### Post by lestertorres on 2013-01-07
Hello everyone, I want to thank you all that help me out on this in advance!

Here we go...

I have a proxy server with 2 NIC's

eth0 <--to internet
eth1 <--to switch

squid3 proxy w/ dansguradian
{authentication (ncsa users) & whitelist}

LTSP server using ubuntu 11
eth0 
eth1
eth2
eth3
eth4
{thin clients (disklessworkstations.com [& no i am not promoting them])} 

Being that my proxy has an authentication and block range for ip addresses, I can block any pc from the internet without a problem and if the address is not in the range the proxy will need the username and password in order for the internet to work. However, what do I do for the thin clients that do need access to the internet without the whitelist? Thin clients do not have an ip address because they use the address of the server (in this case eth2 [comes from the ltsp server]) 

Here is my goal...

I want to make a group in the squid.conf or dansguardian, so that certain users from the thin client can have full internet access and not sit behind the proxy. Is there a way to do this? Due to the thin clients not having an independent ip address this seems like it might not work but how can i get this to work? 

Please help me everything,
thank you all again and have a great day.:popcorn:

---

### Post by lestertorres on 2013-01-08
To simplify my thread...

I want to use squid proxy on thin clients using their user names instead of ip address because the address comes from the ltsp server and that would conflict with the proxy server.

---

