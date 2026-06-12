---
title: "network setup for firewall iptables and DMZ with 2 nic cards"
date: 2008-07-02
forum: Server Platforms
---

### Post by twistedtwig on 2008-07-02
Hi all,

OK so I have a network at home and want to know if it is possible to setup a DMZ and how exactly I could do it.

My currect setup is as follows (excuse the terrible drawing please):

[IMG]http://www.houseofhawkins.com/network.jpg[/IMG]

I have a sky broadband modem and router (it is a netgear router).  This has the external IP and runs a DHCP Server.  I have port 80 forwarded to the ubuntu server

this connects straight into my ubuntu box (eth0) that I have always set to 192.168.0.2.  this box runs my web server, firewall, my internal dhcp and dns server and samba share.

eth1 on the ubuntu server goes out into a netgear router that shares out the ubuntu's dhcp network for the PC's and the wireless (wpa).

I also have a windows 2003 server inside the network connected to the internal netgear router (uses ubuntu dhcp server, static ip).

I use apache proxypassreverse to share parts of the windows 2003 servers website.  this seems to be having some issues with web services.

Anyway, I would like setup a DMZ so that the apache web server can be contacted (have that at the moment).  I would also like the windows server to be directly contact able.

I don't know if this is possible with the hardware configuration I have.

Also I do not know how I would deal with requests for different websites.  Say ubunutu server is site1 and site2, and windows is site3 and site4.  Can i get it to forward the right requests the same right place?

Sorry if this is a lot of questions.

Thank you for any and all advise

---

### Post by slackjawed on 2009-10-05
Hi

I too have a similar issue.

I have Ubuntu server with 2 NIC connecting to a sky router. I also am using webmin and netgear 12 port. Wanted to set up to share internet. Have port forward 80 on the sky router.

My problem is simple to say but less easy to explain! It don't work! I can't setup the safe NIC with a static IP when i do it just get switched off and affects internet NIC and stops it from getting an internet connection. I tried swapping them over and everything. If you don't give safe NIC a static IP is on but just gets switched off by the machine (but with this configuration it can get internet but is not sharing it!).

Think I may have to try another re-install and select the manual configuration option for the network and try that instead.

Going to have to try a different version of Linux at this rate.    :confused:       ](*,)      :-({|=

Cheers

Slackjaw

---

### Post by Lars Noodén on 2009-10-05
```

      Internet
         |
      skymodem (external IP)
       dhcpd (192.168.0.0/24)
         |
        eth0
       Apache
        dns
    dhcpd+samba
        eth1                  +- 
         |                    | 
      netgear-----------wifi--+-
         |                    |
    +----+----+----+          +-
    |    |    |    |
   PC   PC   PC   LegacyPC

```

Is the Netgear switch a layer2 or layer3 switch?

Are you using dnsmasq for the dhcpserver on the ubuntu machine?

When you write, "Say ubunutu server is site1 and site2, and windows is site3 and site4", do you mean web site?  If so, then name-based virtual hosts on Apache on the ubuntu machine are the solution, with the two for the legacy system being forwarded using mod_rewrite.  If not, then which specific ports does the legacy system need to have accessible to the outside world?

Is the dns service on your ubuntu machine serving the world or just your LAN?

---

