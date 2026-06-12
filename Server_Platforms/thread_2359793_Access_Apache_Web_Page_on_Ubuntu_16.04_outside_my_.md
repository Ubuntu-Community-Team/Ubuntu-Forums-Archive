---
title: "Access Apache Web Page on Ubuntu 16.04 outside my Home Network."
date: 2017-04-27
forum: Server Platforms
---

### Post by sethanath2 on 2017-04-27
Hi,

I want to be able to view my web page from the internet. However, I currently can only view my server from my home, as you can see from the attachment1. I tried to assign my public IP address, which I found from my ATT router, to one of the free domains site, which is [http://www.dot.tk](http://www.dot.tk) in this case, but I can't get it to work.

Here are what I have done.

1. For easier troubleshooting, I allow all "Applications", all "Protocol", and "Port Number(s)" from the router for this "Ubuntu" server (Attachment2).  
2. I assigned public IP address shown in the router setting, to a free domains site, as you can see from the attachment3.
3. I also believe I have UFW firewall set correctly as you can see below.

$ sudo ufw status verbose
[sudo] password for:
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
8080                       ALLOW IN    Anywhere                  
80,443/tcp (Apache Full)   ALLOW IN    Anywhere                  
22/tcp                     ALLOW IN    Anywhere                  
80/tcp                     ALLOW IN    Anywhere                  
8080 (v6)                  ALLOW IN    Anywhere (v6)             
80,443/tcp (Apache Full (v6)) ALLOW IN    Anywhere (v6)             
22/tcp (v6)                ALLOW IN    Anywhere (v6)             
80/tcp (v6)                ALLOW IN    Anywhere (v6)         

However, when I tried to access my web page using "www.zethanath.tk", through Firefox, I can't get it to work. I keep getting this message "**Sorry, the page you were looking for does not exist or is not available".**

I wonder if you can help. 

Thanks.

---

### Post by sethanath2 on 2017-04-27
I am also not sure whey I keep getting port "80" is closed from the router as you can see from the attachement.

Thank you.

---

### Post by sethanath2 on 2017-04-27
Hi,

I rebooted the Ubuntu Server as well as the PC that I used to remote to the server. I notice that the information on my router changed. Please see the attachment for details.

Thank you. I hope someone can help me set my web server to work with "www.dot.tk".

---

### Post by sethanath2 on 2017-04-28
Hi,

By searching the internet, I found that I need to forward port, first, so that my web page would be accessible from outside the home router. I followed the post below to forward port from "Ubuntu" server.

[https://portforward.com/pace-plc/4111n-030/](https://portforward.com/pace-plc/4111n-030/)

[ATTACH=CONFIG]274810[/ATTACH]

However, my cousin from far away mentioned that my web page is still unreachable.

---

### Post by TheFu on 2017-04-28
```
$ whois www.zethanath.tk
Invalid query or domain name not known in Dot TK Domain Registry
$ ping www.zethanath.tk
ping: unknown host www.zethanath.tk
$ whois zethanath.tk
WHOIS lookup for ZETHANATH.TK can temporarily not be answered. Please try again.

```
You need to fix your domain name stuff first, then DNS.

Nothing will work until those are fixed.

---

### Post by sethanath2 on 2017-04-28
> You need to fix your domain name stuff first, then DNS.

Hi,

Thank you for your help. Here is the additional information that I have just pulled now.
Please also see my attachment for my "DotTK DNS setting". I don't know how to fix my domain name any further :P
From how I understand it, my domain name is "zethanath.tk" right?

```
erick@erick-ASROCK ~ $ whois 192.168.1.70

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/public/whoisinaccuracy/index.xhtml
#


#
# The following results may also be obtained via:
# https://whois.arin.net/rest/nets;q=192.168.1.70?showDetails=true&showARIN=false&showNonArinTopLevelNet=false&ext=netref2
#

NetRange:       192.168.0.0 - 192.168.255.255
CIDR:           192.168.0.0/16
NetName:        PRIVATE-ADDRESS-CBLK-RFC1918-IANA-RESERVED
NetHandle:      NET-192-168-0-0-1
Parent:         NET192 (NET-192-0-0-0-0)
NetType:        IANA Special Use
OriginAS:       
Organization:   Internet Assigned Numbers Authority (IANA)
RegDate:        1994-03-15
Updated:        2013-08-30
Comment:        These addresses are in use by many millions of independently operated networks, which might be as small as a single computer connected to a home gateway, and are automatically configured in hundreds of millions of devices.  They are only intended for use within a private context  and traffic that needs to cross the Internet will need to use a different, unique address.
Comment:        
Comment:        These addresses can be used by anyone without any need to coordinate with IANA or an Internet registry.  The traffic from these addresses does not come from ICANN or IANA.  We are not the source of activity you may see on logs or in e-mail records.  Please refer to http://www.iana.org/abuse/answers
Comment:        
Comment:        These addresses were assigned by the IETF, the organization that develops Internet protocols, in the Best Current Practice document, RFC 1918 which can be found at:
Comment:        http://datatracker.ietf.org/doc/rfc1918
Ref:            https://whois.arin.net/rest/net/NET-192-168-0-0-1


OrgName:        Internet Assigned Numbers Authority
OrgId:          IANA
Address:        12025 Waterfront Drive
Address:        Suite 300
City:           Los Angeles
StateProv:      CA
PostalCode:     90292
Country:        US
RegDate:        
Updated:        2012-08-31
Ref:            https://whois.arin.net/rest/org/IANA


OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   ICANN
OrgAbusePhone:  +1-310-301-5820 
OrgAbuseEmail:  abuse@iana.org
OrgAbuseRef:    https://whois.arin.net/rest/poc/IANA-IP-ARIN

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   ICANN
OrgTechPhone:  +1-310-301-5820 
OrgTechEmail:  abuse@iana.org
OrgTechRef:    https://whois.arin.net/rest/poc/IANA-IP-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/public/whoisinaccuracy/index.xhtml
#

```

---

### Post by sethanath2 on 2017-04-28
> **TheFu said:**
> ```
$ whois www.zethanath.tk
Invalid query or domain name not known in Dot TK Domain Registry
$ ping www.zethanath.tk
ping: unknown host www.zethanath.tk
$ whois zethanath.tk
WHOIS lookup for ZETHANATH.TK can temporarily not be answered. Please try again.

```
You need to fix your domain name stuff first, then DNS.

Nothing will work until those are fixed.

I also tried what you did above from my home. Here is what I have.
```

erick@Ubuntu:~$ whois www.zethanath.tk
Invalid query or domain name not known in Dot TK Domain Registry
erick@Ubuntu:~$ ping www.zethanath.tk
PING www.zethanath.tk (104.239.207.44) 56(84) bytes of data.
64 bytes from 104.239.207.44: icmp_seq=1 ttl=46 time=69.4 ms
64 bytes from 104.239.207.44: icmp_seq=3 ttl=46 time=68.5 ms
64 bytes from 104.239.207.44: icmp_seq=4 ttl=46 time=69.0 ms
64 bytes from 104.239.207.44: icmp_seq=5 ttl=46 time=67.7 ms
64 bytes from 104.239.207.44: icmp_seq=15 ttl=46 time=68.2 ms
64 bytes from 104.239.207.44: icmp_seq=17 ttl=46 time=68.6 ms
^Z
[1]+  Stopped                 ping www.zethanath.tk
erick@Ubuntu:~$ whois zethanath.tk
WHOIS lookup for ZETHANATH.TK can temporarily not be answered. Please try again.
```

---

### Post by TheFu on 2017-04-28
You need 3 things to have your website available on the internet.
* registered domain - the name and TLD.  These are usually $1.99/yr to $199/yr.
* authoritative DNS that answers for that domain for everyone on the internet, the registrar needs to be told which DNS is your "authoritative DNS" - this is usually a service.
* web server - this is where the DNS points the name <--> IP and IP <--> Name mapping.  The DNS needs to be configured for any specific host you want. If you want [www.domain.com](www.domain.com) to have an HTTP server, then setup [www.domain.com](www.domain.com). Many DNS service providers do this automatically, but if you do it yourself, it is NOT automatic.  There is nothing special about www or ftp or news or gopher or inn or mail or any other 3rd level name used. If you want mail.domain.com to be resolved, then you need to setup the DNS for it.

[http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) explains further. 

You can't use non-routable, private, IPs for services you want available world-wide. [https://en.wikipedia.org/wiki/Private_network](https://en.wikipedia.org/wiki/Private_network)

---

### Post by sethanath2 on 2017-04-28
> **TheFu said:**
> You need 3 things to have your website available on the internet.
* registered domain - the name and TLD.  These are usually $1.99/yr to $199/yr.
* authoritative DNS that answers for that domain for everyone on the internet, the registrar needs to be told which DNS is your "authoritative DNS" - this is usually a service.
* web server - this is where the DNS points the name <--> IP and IP <--> Name mapping.  The DNS needs to be configured for any specific host you want. If you want [www.domain.com]("http://www.domain.com") to have an HTTP server, then setup [www.domain.com]("http://www.domain.com"). Many DNS service providers do this automatically, but if you do it yourself, it is NOT automatic.  There is nothing special about www or ftp or news or gopher or inn or mail or any other 3rd level name used. If you want mail.domain.com to be resolved, then you need to setup the DNS for it.

[http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) explains further. 

You can't use non-routable, private, IPs for services you want available world-wide. [https://en.wikipedia.org/wiki/Private_network](https://en.wikipedia.org/wiki/Private_network)

Thank you so much. I think I will have to redo all my works above now as they don't match with what mentioned above.

---

### Post by TheFu on 2017-04-28
BTW, you don't have to have a [www.domain.com](www.domain.com) if you don't want it.  See how I have a blog.jdpfu.com?  If you go to just jdpfu.com, you'll be redirected to blog.jdpfu.com. I'm running about 30 different websites across different names - some on the same server and some go to different back-end servers.  And some to different IPs.  DNS controls much of that.

The port you choose to use for each service is up to you as well. If you stay with the defaults, things are a little easier.  For services that are meant to be private, using non-standard ports can be helpful to keep your logs cleaner.  It doesn't actually help much with actual security, but if attacks are more easily filtered, then we can be proactive in addressing them and making better choices.

Anyway, happy to help.  After you get the registrar, dns and web hosting setup, we can try to address the router port forwards and firewall stuff at that point.

Please understand that running a website on the internet can be very dangerous.  If you intend for everyone in the world to have access, then you need to allow everyone access. However, if you only want a few other people to have access, it would be smart to block 99.99999999% of the internet from having **any** access and only allow the source IPs for the people who you want to get in.  This can be a challenge when they travel, but the rest of the time, if they are always at home or work, you can allow just a few subnets - which will drastically limit who can even attack at all.

---

### Post by sethanath2 on 2017-04-29
Thanks. I will redo all my work now. Let's use this new post 

[https://ubuntuforums.org/showthread.php?t=2359900](https://ubuntuforums.org/showthread.php?t=2359900)

---

### Post by TheFu on 2017-04-29
I don't know/use cloudflare for security and privacy reasons.
Cannot help. Sorry.

---

