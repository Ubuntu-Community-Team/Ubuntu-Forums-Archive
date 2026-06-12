---
title: "Ubuntu step by step log firewall proxy server for SOHO or parental control"
date: 2010-08-01
forum: Server Platforms
---

### Post by compweisen on 2010-08-01
Comments are welcome.. If this gets moved I apologize for putting it in the wrong place...
Purpose of server: RED GREEN ROUTER for SOHO or PARENTAL CONTROL 
       Block known bad URL,IP... ie porn, malware, ads, others
       Block Good URL,IP if Desired by OWNER
       Scan mail protocols for viruses out and in if out is found log and mail MASTER
       POSSIBILTY??? scan all protocols in and out for viruses 
             in block log
             out block log and mail MASTER

It is a server build log and possibly a step by step assist for new users.

Version of ubuntu server 10.04
Hardware 
Gateway Pentium 4 
2 network cards

Use of server RED GREEN ROUTER FIREWALL that blocks site list from shalla and my own list. general use would be for SOHO or Parental control

Install ubunutu server 10.04 pick eth0 as DHCP provided RED "OUTBOUND" NIC
installer step by step
pick language...pick it again???...country...no...country for kb...kb layout...eth0(as RED)...name it...timezone...HDD choice(i used guided-use entire disk)...user...proxy if needed(not for RED GREEN ROUTER!!!)...updates(i picked auto)...LAMP,openssh, mail server ...sqlpassword...grub...done

then
login as user/pass created in install
run following 
sudo passwd   .... 
exit   
login as root
apt-get update  ... work? great move on
vim /etc/network/interfaces   ...   add
auto eth1
iface eth1 inet static
     address          192.168.5.1
     netmask         255.255.255.0
     broadcast       192.168.5.255
     network          192.168.5.0
...
/etc/init.d/networking restart
... putty from a statically configured device connected to the eth1(GREEN) nic should now work ...

now lets get and configure dnsmasq and dhcp
apt-get install dnsmasq dhcp3-server
vim /etc/default/dhcp3-server
change line 
interfaces=""
to
interfaces="eth1"
...
a good idea for reading later and reference
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)
cp /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf.back
then create your own.
rm /etc/dhcp3/dhcpd.conf
vim /etc/dhcp3/dhcpd.conf
add ...
# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.5.255;
option routers 192.168.5.1;
option domain-name-servers 192.168.5.1;
option domain-name "whatev.local";

subnet 192.168.5.0 netmask 255.255.255.0 {
range 192.168.5.100 192.168.5.199;
#wireless range provided by switch connected wap
#192.168.5.200 192.168.3.250
}
...
/etc/init.d/dhcp3-server restart
/etc/init.d/networking restart
... dhcp should now work
... now to configure shorewall
apt-get install shorewall
... a good reference is
[https://help.ubuntu.com/community/ShorewallBasics](https://help.ubuntu.com/community/ShorewallBasics)
[http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway)
...
cp /usr/share/doc/shorewall/examples/two-interfaces/* /etc/shorewall/
vim /etc/shorewall/shorewall.conf
... change line
IP_FORWARDING=Keep
... to
IP_FORWARDING=On
...
vim /etc/default/shorewall
... change line
startup=0
... to
startup=1
...
vim /etc/shorewall/policy
... looks like the following 
#
# Shorewall version 4.0 - Sample Policy File for two-interface configuration.
# Copyright (C) 2006 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.
#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-policy"
###############################################################################
#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST

# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc             net             ACCEPT
loc             $FW             ACCEPT
loc             all             REJECT          info
#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW             net             ACCEPT
$FW             loc             ACCEPT
$FW             all             REJECT          info
#
# Policies for traffic originating from the Internet zone (net)
#
net             $FW             DROP            info
net             loc             DROP            info
net             all             DROP            info
# THE FOLLOWING POLICY MUST BE LAST
all             all             REJECT          info
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
... 
/etc/init.d/shorewall start
... you should now be able to surf the net
... good time to reboot and check dependencies and startup options
.... a good tool for checking traceroute
apt-get install traceroute

I will post now and see if any comments come in at this point I have a working firewall that has been tested for inbound block and outbound allow. My next steps are to configure a proxy.. then I want to be able to block URL and IP reverse and forward so that users can not enter IE: [www.facebook.com]("http://www.facebook.com") or 69.63.189.34

I have tried squid and am successful to block a found working malware list found at
some references i have found at this point
[http://www.digriz.org.uk/dns-malware-blacklisting](http://www.digriz.org.uk/dns-malware-blacklisting)
[http://www.shallalist.de/](http://www.shallalist.de/)
[http://malware.hiperlinks.com.br/](http://malware.hiperlinks.com.br/)

However squid will not reverse lookup IP address and block if found to be a BAD/Blocked URL

---

### Post by compweisen on 2010-08-02
ok so I am going to try dansguardian with squid
good resources are
[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)
[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)
...ignore the httpd_accel stuff it is actually for an inbound request
so lets get the following installed
apt-get install clamav-freshclam dansguardian squid
vim /etc/squid/squid.conf
... add or change the follow lines
http_port 3128 transparent
.... BTW all allows should be before any deny... look for
http_access allow .... and replace what looks like the following with the following...
# Only allow cachemgr access from local
http_access allow localnet
http_access allow manager localhost
http_access deny manager
...
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network ... should already be there
... this should work if not change it to 192.168.5.0/24 ... or whatever 192.168.x.0/24
cache_dir ufs /var/spool/squid 7000 16 256

We can test squid by doing the following
iptables -t nat -A PREROUTING -i  [COLOR=#ff0000]eth1[/COLOR] -p tcp --dport [COLOR=#ff0000]80[/COLOR] -j DNAT --to 192.168.5.1:3128
... start squid
1 of the following commands works my order was
 /etc/init.d/squid start
squid -k reconfigure
service squid restart
... Works now we can remove the the prerouting and move on to dansguardian config

---

### Post by compweisen on 2010-08-02
Dansguardian config
[http://dansguardian.org/](http://dansguardian.org/)
[http://forums.fedoraforum.org/showthread.php?t=142038](http://forums.fedoraforum.org/showthread.php?t=142038)
many others just google it anyway here is what I did
vim /etc/dansguardian/dansguardian.conf
...
#UNCONFIGURED - Please remove this line after configuration
...
daemonuser = 'root'
...
daemongroup = 'root'
...
accessdeniedaddress = 'http://localhost/cgi-bin/dansguardian.pl'
...Change the Dansguardian log folder to the correct ownership and start Dansguardian: 

chown -R root:root /var/log/dansguardian
/etc/init.d/dansguardian start
... Shorewall
vim /etc/shorewall/rules
... add to bottom
ACCEPT          $FW             net     tcp     www
REDIRECT        loc             8080    tcp     www
...
 /etc/init.d/shorewall restart
... dansguardian works now with default rules
vim /etc/clamav/freshclam.conf
...
checks 48
...
/etc/init.d/clamav-freshclam restart
...

I have tested and all things bad and nasty are being blocked. My next step is to block my own unwanted list by url and ip
Here is where comments are welcome and appreciated
IE: I want to block [www.facebook.com]("http://www.facebook.com") this is easy enough I have already done it unfortunately if a user types in the IP it still works. :(
So I need a reverse lookup performed if by IP instead of URL or better yet just block all request by IP.

Also I have edited the file dansguardain.pl in /usr/lic/cgi-bin to get rid of some unneeded verbage however it has not been updated when the request is blocked. ????
what did I miss?
Do i need to restart apache. I would think not. Or maybe restart Dansguardian?

---

### Post by compweisen on 2010-08-03
I just hit paydirt for my IP blocking and URL blocking problem.
[http://dansguardian.org/downloads/detailedinstallation2.html](http://dansguardian.org/downloads/detailedinstallation2.html)
look for reverselookup

I know all of you are probably laughing at this point but there is a lot of reading...and learning curve is exponential.

---

### Post by compweisen on 2010-08-04
Got everything working all the above works and the last settings I played around with are now working.
reference [http://dansguardian.org/downloads/detailedinstallation2.html](http://dansguardian.org/downloads/detailedinstallation2.html)
so ...
vim /etc/dansguardian/dansguardian.conf
...
everseaddresslookups = on
loglevel = 1
...
this allows only blocked logging squid will log the rest
will block ip if url is on the blockedsitelist file
vim /etc/dansguardian/lists/bannedsitelist
... find badboys.com
... added
facebook.com
myspace.com
fanbook.com


also figured out to edit the html page that is shown
it is found at /etc/dansguardian/languages/ukenglish/template.html

cheers

---

### Post by compweisen on 2010-08-10
ok so new problem probably has a real simple solution 

i moved the server over to the dsl provider to remove the router in between so I need to set up PPPoE. I have found good references.
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
But I have also found problem pages with the setup.

so the big question is what do I need to place in the 
/etc/network/interfaces file to point eth0 to PPPoE instead of auto DHCP????

Please help

---

### Post by compweisen on 2010-08-10
k found a new ref...
[http://manpages.ubuntu.com/manpages/hardy/man8/pppoe.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pppoe.8.html)

which specifies that interface should be up but not configured for ip....
in my last posts I show that my interface file has eth0 as auto dhcp
how do I specify it as up but not configured?

---

### Post by garfonzo on 2010-08-11
First off, I think it is great that you are filling a whole thread with your own posts. It's almost like a blog! (I mean that in a good way).

Second, I am really glad you are doing this because I want to do the exact same thing on my home LAN. I have scanned the inter-tubes and found many scattered tutorials and information but never just jumped in. I have been hesitant to actually set something up but, with this thread I will likely give it a shot soon. 

Thanks again. If I run into anything beyond what you have experienced, I will post my results here. 

What are you using your setup for?

---

### Post by garfonzo on 2010-08-11
Oh, question I had about the two network cards:

Would I be correct to assume that because my home's ISP connection is a 15 Mb/s connection, having two 100Mb/s NICs on this server will not affect my LAN's Gb/s network?

I think that is true, but I want to make sure. I stream HD video all over the house on a gigabit network and don't want to mess that up.

---

### Post by compweisen on 2010-08-11
> **garfonzo said:**
> Oh, question I had about the two network cards:

Would I be correct to assume that because my home's ISP connection is a 15 Mb/s connection, having two 100Mb/s NICs on this server will not affect my LAN's Gb/s network?

I think that is true, but I want to make sure. I stream HD video all over the house on a gigabit network and don't want to mess that up.

Basically this is used to guard your internal network from intrusion from the outside and any BAD request for stuff from the internet.

So the configuration of the 2 NICs on the server described above eth0 gets connected to your outbound dsl/cable connection. eth1 gets connected to your existing router or switch. So no it will not effect internal trasmissions. 

It could get configured differently if needed to provide for a DMZ or all green zone using a third NIC.

I am configuring this server to be used at a small office. But I used it at home for 3 weeks. with everything setup all the way to post number 5.

---

### Post by compweisen on 2010-08-11
> **compweisen said:**
> ok so new problem probably has a real simple solution 

i moved the server over to the dsl provider to remove the router in between so I need to set up PPPoE. I have found good references.
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
But I have also found problem pages with the setup.

so the big question is what do I need to place in the 
/etc/network/interfaces file to point eth0 to PPPoE instead of auto DHCP????

Please help

OK so I edited /etc/network/interfaces
commenting out the line 
iface eth1 inet static
...
Then /etc/init.d/networking restart
it ignored the eth0 which was exactly what I wanted
using this reference
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
I then ran
pppoeconf
worked great
I edited /etc/ppp/peers/dsl-provider
to change MTU to 1412
ifconfig ppp0
shows me having a valid IP and subnetmask from the ISP

I cannot ping [www.google.com](www.google.com)
I cannot surf using a connected workstation
I beleave my problem at this point is that DNS is not getting forwarded because the PPPoE inbound traffic is getting blocked.
So I am going to take a look at dnsmasq to see if I can tell it the outbound dns server to contact.

Cheers

---

### Post by compweisen on 2010-08-13
so at this point I have rebuilt the server to working at home again...........
the pppoeconf and changes above did not work I think they will if I do the following
vim /etc/resolv.conf
... add
nameserver 8.8.8.8
nameserver 8.8.4.4
... if your isp gives you any specific DNS servers add them as well
... the above addresses are for google dns

---

