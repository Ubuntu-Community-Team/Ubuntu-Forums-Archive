---
title: "Bind9 advice required"
date: 2006-08-11
forum: Server Platforms
---

### Post by caffine_fizz on 2006-08-11
Hi,
    I've recently jumped into linux from windows and must say it rips the arse out of it once you start to get up in the learing curve.

At the start of the week i installed 6.06 LAMP server installation on an old machine i had lying around to play around with, since then i also installed samber and now have it linked to 3 windows machines; then yesterday i started on bind9 installation configuration.

the network configuration i have goes something like this:

Static IP on net
|
|_Router1/modem 192.168.1.1
  ||
  ||_Linux Server Box external eth0 192.168.1.2
  |
  |_Router2 192.168.70.1
    ||||
    ||||_Windows machine 1
    |||
    |||_Windows machine 2
    ||
    ||_Windows machine 3
    |
    |_Linux Server Box internal eth1 192.168.70.3

i have set bind up to have configuration records for internal and external connections per domain, and can ping the windows machines by suffix.domainname.com

could some one advice me on the following:

1. How do i display the web page set up for a domain entered in bind through a browser on one of the windows machines?

2. Should my Static IP address, router address or linux nic address be used in my primary external a record for the domain

> ; example.com
$TTL    604800
@       IN      SOA     ns1.somedomain.com. root.somedomain.com. (
                     2006020201 ; Serial
                         604800 ; Refresh
                          86400 ; Retry
                        2419200 ; Expire
                         604800); Negative Cache TTL
;
@       IN      NS      ns1
        IN      MX      10 mail
        IN      A       192.168.1.1
ns1     IN      A       192.168.1.1
www     IN      A       192.168.1.1
**Note: I currently have it set to the router which seems to be getting picked up from my secondary name server(using the service provided by [www.xname.org]("http://www.xname.org") **


I have a registered domain (say somedomain.com), but when i try to enter my nameserver as ns1.somedomain.com it won't allow me to specify an ip adddress to point to it, but it will allow me to add the name servers where my secondary record resides at ns0.xname.org and ns1.xname.org again though without specifying     
an ip address.

3. This is the first time i've registered a domain, is this a normal process whereby i can't specify an ip to point to my nameserver?

4. The domain name provider has happly accepted the nameservers of ns1.xname.org and ns0.xname.org where my secondary record resides, but as mentioned not accepted my primary; can this configuration be left as is letting the secondary point to the primary?

5. What exactly should be in my /etc/resolv.conf file with this sort of set up? 

currently contains localhost and isp:
> nameserver 127.0.0.1
nameserver 220.233.0.4
nameserver 220.233.0.3

6. Is it better to port forward through the router or dmz, i thought port forward be better providing better protection, if this is correct should i worry about iptables configuration when its all up and going.

7. What happens if i power down and add another hard dive to the system, on a server dist, am i prompted in some manner at start up or is it just a case using a partitioning program and reconfiguring (assuming the last)?

If any one could help me in regards to any of the following i'd apreciate it.

caffine_fizz (starting out in linux)

---

### Post by chrisfay on 2006-08-11
> 4. The domain name provider has happly accepted the nameservers of ns1.xname.org and ns0.xname.org where my secondary record resides, but as mentioned not accepted my primary

You can't add your newly created nameservers to your domain until you have your registrar submit them to the root servers. 

Steps are similar to this: (Godaddy)

1.add ns1 and ns2 to the root servers through the registrar

2.add ns1 and ns2 to your domain pointing to your Ip

I know GoDaddy allows you to create subdomains of your registered domain and update them as name servers with the root servers. You can use the web-domain management area to do this. All you have to do next is actually add them to your domain you registered. 

Bluehost does not support subdomain creation for name server perposes...guh...I have to have a seperate domain registered at GoDaddy just to use for my name servers.

> 6. Is it better to port forward through the router or dmz, i thought port forward be better providing better protection, if this is correct should i worry about iptables configuration when its all up and going.

I have been using my Linksys Wrt54G to portforward while IPcop or Smoothwall may be an alternative as well if you prefer more control over your configuration. 

Depending on your router I think you are pretty safe utilizing the firewall features within it and just portforwarding. The only drawback is that you can run out of port slots (my router only has 10) and then you have to start opening ranges to a certain IP which is obviously unsafe.

If you have a decent firewall setup on your server machines you could utilize the DMZ option and manage your ports that way. I think it just depends on how you have your firewalls configured and which way your more comfortable with.

---

