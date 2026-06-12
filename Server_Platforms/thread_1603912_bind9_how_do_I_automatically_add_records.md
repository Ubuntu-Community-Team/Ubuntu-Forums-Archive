---
title: "bind9 how do I automatically add records"
date: 2010-10-23
forum: Server Platforms
---

### Post by ant2ne on 2010-10-23
Goal: My end goal for this server is DHCP, DNS, and LDAP hosting my Linux and Windows mixed home network. (around 10 devices) So far DHCP is working flawlessly and DNS is working, mostly.

I set up my first bind9 server using ubuntu server 10.4 and configuring it mostly via webmin. (honestly it took me hours of internet scouring and using cli as well as webmin before I finally got it working, thus, 'mostly' webmin) regardless it is now working. *appplause*

It attempts to resolve names and failing that it passes the querry to a higher server, I use opendns for this. opendns is fast, and it has pretty neat filtering capabilities. But the only local addresses that it can resolve are ones that I enter records for. [webmin -> bind -> myzone -> address]

On a windows (domain) network, the a new windows machine would connect to the network, request IP from DHCP and get a DNS address. I could then resolve this new device by name without any additional work from me. I could also roam around in the DNS mmc and see the various clients and their records. This is what I want for my linux network. How do I configure this?

---

### Post by ant2ne on 2010-10-25
*crickets chirping*

---

### Post by BobVila on 2010-10-25
Might take some command-fu, as I'm not sure that you can accomplish the config file edits through webmin, but here's a walkthrough.

[http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable]("http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable")

---

### Post by HermanAB on 2010-10-25
Howdy,

The auto DNS security hole was added by Microsoft to their ancient version of BIND8 used on Windows 2003 Server.

The official versions of BIND doesn't do that for reasons that I'll leave as a network security exercise to the reader.

---

### Post by ant2ne on 2010-12-01
Security hole or not, I don't see how active directory (and probably ldap) could function without this dns feature. 

And I pitty the tech who has to support a few thousand of computers on a network when the tech can't access the computers with a good naming convention. For example; naming the computers based on building number, room number, and computer number the hostname might be bldg8-rm302-04. So the tech can ask the user on the phone where the computer is and what computer has the problem and then rdp or ssh into the device to fix it. The IT department could also label the computer with the same naming convention (in case it gets moved) or something different like 'hercules-108" and then ask the user on the phone what the computer sticker says on the case. DNS can be a wonderful thing!! Asking the user what the IP address of the problem computer wont get you very far. 

Assuming that I'm not interested in any exercise, (or why would I go into IT?) how would one implement such a feature?

---

### Post by SeijiSensei on 2010-12-02
The dhcp3 server can send updates to bind9.  Do a Google search for "dhcp3 bind9 add hosts to zone" and you'll see some tutorials.  I thought [this one](http://www.semicomplete.com/articles/dynamic-dns-with-dhcp/) was especially clear.

---

### Post by HermanAB on 2010-12-02
IT people that are really serious about security (military for example) do not use DHCP either.  On mil systems, all the 'auto-screw-up' features of MS Windoze are disabled.  So, yes, Active Directory can work without it.

---

### Post by Johnnotchris on 2010-12-02
> **HermanAB said:**
> IT people that are really serious about security (military for example) do not use DHCP either. On mil systems, all the 'auto-screw-up' features of MS Windoze are disabled. So, yes, Active Directory can work without it.
 
 
Would you like to bet on the Mil systems with DHCP.

---

### Post by ant2ne on 2010-12-04
> **SeijiSensei said:**
> The dhcp3 server can send updates to bind9.  Do a Google search for "dhcp3 bind9 add hosts to zone" and you'll see some tutorials.  I thought [this one](http://www.semicomplete.com/articles/dynamic-dns-with-dhcp/) was especially clear.This is probably exactly what I'm looking for. 

THANKS!!

I will investigate it when I find time. :-/

---

### Post by ant2ne on 2010-12-04
> **Johnnotchris said:**
> Would you like to bet on the Mil systems with DHCP.
I would like to hear about what services and servers the military does use.

I'm no MS AD or DNS expert, so I'd like to know more about this "auto-screw-up" that needs to be disabled. And how you might get AD to work. I can only speak from my past experience, and that is if DNS isn't resolving both ways (server knows client name, client knows server name) then you are not logging into that computer due to authentication problems. I know that AD and DNS are very tightly woven, and one must trust the other. That is why I always set up an Domain Controller and the DNS server in the same box.

I am Security+ certified, and know about DNS poisoning and other potential threats. And I'm certain that not using DNS is one solution to these security problems. But obviously, since I've set up a DHCP/DNS/LDAP server, I would indeed like to use it. But sometimes you need functionality. I for one would hate to run a large network without DNS or DHCP.

---

### Post by HermanAB on 2010-12-04
On most mil systems, everything is preplanned and controlled to the nth degree. Autoconfiguration is not used.

---

### Post by ant2ne on 2010-12-04
Johnnotchris doesn't seem to agree.

---

