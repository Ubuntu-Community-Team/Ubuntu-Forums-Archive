---
title: "NIS client will not work through firewall, help please"
date: 2011-09-10
forum: Security
---

### Post by trevor_obba on 2011-09-10
I have an Ubuntu lucid 10.4 running as NIS client, the machine was working fine as a NIS client until i move the machine to a DMZ firewall.

I tried to get NIS client working through the firewall by I fixing ypbind port to a static port by modifying the file “/etc/default/nis”
YPBINDARGS="-p 835”

The above fixed ypbind port on 835, I then opened port 835 (ypbind) and port 111 portmapper on the firewall.

   rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100007    2   udp    835  ypbind
    100007    1   udp    835  ypbind
    100007    2   tcp    835  ypbind
    100007    1   tcp    835  ypbind

However when i try to start ypbind daemon, ypbind fail to bind to ypserver

“ypcat passwd” show the following error message

YPBINDPROC_DOMAIN: Domain not bound
No such map passwd.byname. Reason: Can't bind to server which serves this domain

Because I could not ping the NIS server i modified “/etc/default/nis” to

YPBINDARGS="-no-dbus -p 835 -no-ping"

But this did not fix the problem, NIS client is still not binding to ypserver through the firewall.

What other port do i need to open on the firewall?

What am i doing rough? Can you help please?

---

### Post by HermanAB on 2011-09-11
Hmmm...  NIS uses RPC, so to go through NAT, you need a tracking filter.  

However, NIS is insecure and should NEVER be used outside a LAN, so you are probably trying to do something that is ill advised and you should probably set up a VPN first.

---

### Post by trevor_obba on 2011-09-11
Thanks for your responses but the NIS server is in one DMZ (**De Militarized Zone)** and NIS client is another DMZ.


  ypbind on the NIS client is fixed on port 835 



  Firewall port is open on port 835 and RPC 111 port.


  However NIS client is failing to bind to ypserver


  tcpdump on the server could not capture any packet from NIS client, which indicate the firewall is blocking network traffic from NIS client.


  What port do i need to open on the firewall? 



  Can you help please?

---

### Post by HermanAB on 2011-09-14
So, what is between the two DMZ, the public internet???  If so, set up a VPN.  If it is a LAN between the two, then remove the firewall, since it is doing nothing anyway.

So, in short, use the NIS system on the LAN, inside the firewall, not outside the firewall.

---

