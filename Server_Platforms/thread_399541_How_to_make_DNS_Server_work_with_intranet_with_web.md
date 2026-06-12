---
title: "How to make DNS Server work with intranet with web site on Unbutu Server?"
date: 2007-04-02
forum: Server Platforms
---

### Post by explorer1979 on 2007-04-02
Hi all,

  I want to set up a test environment for the Web Developing,so download a Unbutu Server 6.10, installed it on a old PC.

  I had setup the apache well....

  But on the intranet, something not work for me.

  I am using Netgear WNR854T for the broadband router. And all computer are using static IP base on 192.168.218.x, and all computer's DNS is setting to using ISP's DNS ....

  On my environment, here are the setting:

  PC A (Developmet Workstation)
  IP: 192.168.218.61
  Sub mask 255.255.255.0
  Gateway: 192.168.218.1
  DNS1: 218.102.66.71 (Want to change to using 192.168.218.121 also can resolv domain name)

Linux Server (full name is linux.testserver.org)
IP 192.168.218.121
Sub mask 255.255.255.0
Gateway: 192.168.218.1
DNS: 192.168.218.121


  The big problem is, while I change the DNS value from the ISP one to the Unbutu one, like from 218.102.66.71 change to 192.168.218.121 (The Intranet Linux Server DNS IP) on my workstation

  Try using nslookup on my workstation and the linux server It will time out, and can not resolv any domain name, both the Linux Server itself and the client, but if using the ISP' DNS server, the Linux server can resolv domain name ....

  The Router's Gateway is 192.168.218.1, and the Unbutu Server IP setting are like that.

in   /etc/resolv.conf
search testserver.org
nameserver 192.168.218.121
nameserver 192.168.218.1
-----------------------------------------------

in /etc/bind/named.conf

zone "testserver.org" {
    type master;
    file "/etc/bind/zone.testserver.org";
};
--------------------------------------------------------------

in /etc/bind/zone.testserver.org
$TTL    3600
@       IN      SOA     linux.testserver.org. root.localhost. (
                              1         ; Serial
                           3600         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
@       IN      NS      linux.testserver.org.
@       IN      A       192.168.218.121
www     IN      A       192.168.218.121
ftp     IN      A       192.168.218.121

It is all, how to setting the Unbutu DNS Server work on my intranet, since if it not work, I can not make a test environment to development the web site like enter this type of domain name ...

 [www.microsofttest01.com](www.microsofttest01.com), etc ....

It just time out while my workstation change from using ISP's DNS to the Linux Server one.

Thx for your time.

---

### Post by foxylad on 2007-04-04
Hi - 

DNS is a lot of work to configure properly. I used to run my own DNS, but in the end I found other ways to deal with local domain names (see below) and gratefully uninstalled my DNS server.

I do a lot of web development, and often you need to be able to locally simulate a domain name - so if you were making a new version of [www.microsoft.com](www.microsoft.com), I want that domain to resolve to my development server. My solution is to edit the hosts file on my client machine (/etc/hosts on Linux, c:\windows\system32\drivers\etc\hosts on Windows) and add an entry for the domain that points to your development server. Then restart your browser, type in [www.microsoft.com](www.microsoft.com) and you should get your development server instead - without having to run bind!

---

### Post by MrHorus on 2007-04-06
I think you have no glue on the root nameservers for this zone.

I suspect that when you try and resolve something within testserver.org then a call will be made to the root nameservers to find out where the nameservers for testserver.org are and unless you actually own this and have arranged for some nameservers to authoritively answer for this, then I doubt it will work.

I might be wrong, but this would be my best guess.

---

