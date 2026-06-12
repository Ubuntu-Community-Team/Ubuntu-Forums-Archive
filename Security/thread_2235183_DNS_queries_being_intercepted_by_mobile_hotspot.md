---
title: "DNS queries being intercepted by mobile hotspot"
date: 2014-07-19
forum: Security
---

### Post by alpfa on 2014-07-19
There is a redirect visrus that appears to be able to infect Ubuntu and Windows platforms, all browsers, regardless of plugins. NoScipt is of no help. It redirects to a fake search website called  search-help.spirint.com.  WHOIS shows that the site is not owned by Sprint. It survives Windows and Ubuntu reinstalls and router resets (even after you check no thru-install options). Changing passwords on the router does nothing. Changing DNS on the router to Google's DNS also has no effect. Any help or info appreciated.

---

### Post by slooksterpsv on 2014-07-19
smob.cfg.srchdeliv.com - if I ping the address that's what it directs to. Hmm.... if you go to your router settings do you have any proxy information added to it? What router? What internet provider? What happens when you do a traceroute to it? What proxy settings do you have set on chrome, firefox, IE, etc.?

---

### Post by bapoumba on 2014-07-19
When you say it survived a reinstall, did yo start with fresh browser profiles or did you sync to a previous profile you had set up ?

---

### Post by alpfa on 2014-07-19
It's a Sprint mobile hotspot. There are no proxy settings on the router that I can find. tracert to hotspot IP address list only one entry, the hotspot itself. The DNS relay is enabled on the hotspot, but disabling it results in loss of internet connectivity. No proxy settings on any of the browsers. Win hosts file has no suspicious entries.

---

### Post by wildmanne39 on 2014-07-19
*Thread moved to **Security Discussions**.*

---

### Post by slooksterpsv on 2014-07-19
You may want to contact sprint. When I had their service, I remember that's the page I'd always get if it couldn't find a site I typed in. If it's happening on multiple devices, it could be something with sprint.

---

### Post by bapoumba on 2014-07-19
Do you have another device to connect to the same network and see if you have the same issue ?

---

### Post by sandyd on 2014-07-19
Change your dns servers on your computer (not the router) to something else. It is possible that your router is doing DNS hijacking, and since the dhcp server sets the default dns server to your router, all computers are affected.

Does using dig in your computer, i.e.
```

dig @routerip dig nonexistantdomain22222222222222.com
```
give the ip mentioned above?

If so, then your router is doing the dns hijacking

It should give something like
```

root@MollyQuinn:~# dig search-help.sprint.com

; <<>> DiG 9.9.5-3-Ubuntu <<>> search-help.sprint.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59444
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;search-help.sprint.com.		IN	A

;; ANSWER SECTION:
search-help.sprint.com.	3599	IN	CNAME	smob.cfg.srchdeliv.com.
smob.cfg.srchdeliv.com.	59	IN	A	198.105.254.64
smob.cfg.srchdeliv.com.	59	IN	A	198.105.244.64

;; Query time: 107 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Jul 19 12:16:55 PDT 2014
;; MSG SIZE  rcvd: 116

root@MollyQuinn:~# 

```

As for whois, they are using an external company to provide the search, which is not much of a surprise
```

root@MollyQuinn:~# whois 198.105.244.64

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#
# If you see inaccuracies in the results, please report at
# http://www.arin.net/public/whoisinaccuracy/index.xhtml
#


#
# The following results may also be obtained via:
# http://whois.arin.net/rest/nets;q=198.105.244.64?showDetails=true&showARIN=false&ext=netref2
#

NetRange:       198.105.240.0 - 198.105.255.255
CIDR:           198.105.240.0/20
OriginAS:       
NetName:        SEARCHGUIDE
NetHandle:      NET-198-105-240-0-1
Parent:         NET-198-0-0-0-0
NetType:        Direct Assignment
RegDate:        2012-07-10
Updated:        2012-07-10
Ref:            http://whois.arin.net/rest/net/NET-198-105-240-0-1

OrgName:        Search Guide Inc
OrgId:          SG-63
Address:        1942 Broadway
Address:        Suite 319
City:           Boulder
StateProv:      CO
PostalCode:     80302
Country:        US
RegDate:        2012-06-26
Updated:        2012-06-26
Comment:        Standard NOC hours are 7am to 6pm EST
Ref:            http://whois.arin.net/rest/org/SG-63

OrgAbuseHandle: NETWO5248-ARIN
OrgAbuseName:   Network Operations
OrgAbusePhone:  +1-603-277-3203 
OrgAbuseEmail:  noc@searchguideinc.com
OrgAbuseRef:    http://whois.arin.net/rest/poc/NETWO5248-ARIN

OrgNOCHandle: NETWO5248-ARIN
OrgNOCName:   Network Operations
OrgNOCPhone:  +1-603-277-3203 
OrgNOCEmail:  noc@searchguideinc.com
OrgNOCRef:    http://whois.arin.net/rest/poc/NETWO5248-ARIN

OrgTechHandle: NETWO5248-ARIN
OrgTechName:   Network Operations
OrgTechPhone:  +1-603-277-3203 
OrgTechEmail:  noc@searchguideinc.com
OrgTechRef:    http://whois.arin.net/rest/poc/NETWO5248-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#
# If you see inaccuracies in the results, please report at
# http://www.arin.net/public/whoisinaccuracy/index.xhtml
#


```

---

### Post by alpfa on 2014-07-19
> **bapoumba said:**
> When you say it survived a reinstall, did yo  start with fresh browser profiles or did you sync to a previous profile  you had set up ?
Happens even when I use a read only Ubuntu live setup


> **sandyd said:**
> Change your DNS servers on your computer (not the  router) to something else. It is possible that your router is doing DNS  hijacking, and since the dhcp server sets the default dns server to  your router, all computers are affected.

Changing the DNS in Network Connections (using Automatic DHCP addresses only option) to 8.8.8.8. does nothing. 


```
u1@u1-HP-Pavilion-17-Notebook-PC:~$ _**dig @routerip nonexistantdomain.com**_

; <<>> DiG 9.9.5-3-Ubuntu <<>> @routerip nonexistantdomain.com
; (4 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17590
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1440
;; QUESTION SECTION:
;nonexistantdomain.com.        IN    A

;; ANSWER SECTION:
nonexistantdomain.com.    600    IN    A    50.63.202.33

;; AUTHORITY SECTION:
nonexistantdomain.com.    3600    IN    NS    ns32.domaincontrol.com.
nonexistantdomain.com.    3600    IN    NS    ns31.domaincontrol.com.

;; Query time: 193 msec
;; SERVER: 198.105.244.64#53(198.105.244.64)
;; WHEN: Sat Jul 19 15:15:07 MDT 2014
;; MSG SIZE  rcvd: 118

```

dig returns the address of the Search help thing, not my router's IP address.

---

### Post by bashiergui on 2014-07-19
Sounds like your router might have gotten rolled. I would consider resetting your router to factory settings.

---

### Post by alpfa on 2014-07-19
Resetting the router doesn't work. I tried system restore and router reset, but that doesn't get rid of it.

---

### Post by bashiergui on 2014-07-19
What country are you in? Who is your ISP?

---

### Post by sandyd on 2014-07-20
> **alpfa said:**
> Happens even when I use a read only Ubuntu live setup




Changing the DNS in Network Connections (using Automatic DHCP addresses only option) to 8.8.8.8. does nothing. 


```
u1@u1-HP-Pavilion-17-Notebook-PC:~$ _**dig @routerip nonexistantdomain.com**_

; <<>> DiG 9.9.5-3-Ubuntu <<>> @routerip nonexistantdomain.com
; (4 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17590
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1440
;; QUESTION SECTION:
;nonexistantdomain.com.        IN    A

;; ANSWER SECTION:
nonexistantdomain.com.    600    IN    A    50.63.202.33

;; AUTHORITY SECTION:
nonexistantdomain.com.    3600    IN    NS    ns32.domaincontrol.com.
nonexistantdomain.com.    3600    IN    NS    ns31.domaincontrol.com.

;; Query time: 193 msec
;; SERVER: 198.105.244.64#53(198.105.244.64)
;; WHEN: Sat Jul 19 15:15:07 MDT 2014
;; MSG SIZE  rcvd: 118

```

dig returns the address of the Search help thing, not my router's IP address.


oops - wrong command, that domain actually exists.

btw, what is the output of
```

cat /etc/resolv.conf
```
after setting the DNS server on the computer.

---

### Post by slooksterpsv on 2014-07-20
I honestly don't think it's a virus. I think it's just Sprint's redirect to their "search engine" when you find a non-existent domain. If it's going through a Sprint Hotspot (not saying that issues like this haven't come up) I've been to this page on my phone. I really don't think it's a virus, but more like their "walled-garden" cannot find page. CenturyLink routes you to a CenturyLink page, Comcast same, T-Mobile same. Even though it's not owned specifically in WHOIS by Sprint, it could be a 3rd party company that manages that site.

---

### Post by bashiergui on 2014-07-20
> **alpfa said:**
> It's a **Sprint mobile hotspot**. There are no proxy settings **on the router** that I can find. tracert to hotspot IP address list only one entry, the hotspot itself. The DNS relay is enabled on the hotspot, but disabling it results in loss of internet connectivity. No proxy settings on any of the browsers. Win hosts file has no suspicious entries.It's a hotspot. And you have a router? Where? Are all the devices connected to the hotspot? Provide a quick diagram of the setup please.

Have you considered that you have used up your available data on your sprint plan? Basically Sprint won't let you submit any get requests except to their website to pay them.

---

### Post by alpfa on 2014-07-20
> **sandyd said:**
> oops - wrong command, that domain actually exists.  btw, what is the output of ```
 cat /etc/resolv.conf
``` after setting the DNS server on the computer.     ```
~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1    127.0.1.1 
```

is also the only address in the WIn Hosts file. ```
$ cat /etc/hosts  
127.0.0.1    localhost 127.0.1.1    u1-HP-Pavilion
```

---

### Post by alpfa on 2014-07-20
> **bashiergui said:**
> It's a hotspot. And you have a router? Where? Are all the devices connected to the hotspot? Provide a quick diagram of the setup please.  Have you considered that you have used up your available data on your sprint plan? Basically Sprint won't let you submit any get requests except to their website to pay them.  A mobile hotspot is a router. This redirect always happens, regardelss of payment.

---

### Post by sandyd on 2014-07-20
> **alpfa said:**
> ```
~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1    127.0.1.1 
```

is also the only address in the WIn Hosts file. ```
$ cat /etc/hosts  
127.0.0.1    localhost 127.0.1.1    u1-HP-Pavilion
```

hmm,
DNSMasq is on - which is hiding the nameservers set for your system.

Run
```

sudo sed -i s/dns=dnsmasq/#dns=dnsmasq/ /etc/NetworkManager/NetworkManager.conf
```
and restart your system (or NetworkManager) and run
```

cat /etc/resolv.conf
``` again.

---

### Post by alpfa on 2014-07-20
> **sandyd said:**
> hmm, DNSMasq is on - which is hiding the nameservers set for your system.  Run ```
 sudo sed -i s/dns=dnsmasq/#dns=dnsmasq/ /etc/NetworkManager/NetworkManager.conf
``` and restart your system (or NetworkManager) and run ```
 cat /etc/resolv.conf
``` again.  ```
$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 8.8.4.4 nameserver 8.8.8.8 search lan
```

---

### Post by sandyd on 2014-07-21
> **alpfa said:**
> ```
$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 8.8.4.4 nameserver 8.8.8.8 search lan
```

/me scratches head

maybe..
```

dig @8.8.8.8 hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com
```

If that actually returns an ip address, then your router is intercepting your DNS requests, and there is not really anything you can do.

---

### Post by CharlesA on 2014-07-21
It's likely built into the hotspot. I'd contact sprint and complain and/or see if either they can disable it or get around it somehow.

I had to change the DNS servers on my router and set them to static because my ISP did the same thing... that should have worked to get it to stop hijacking nonexistant domains.

EDIT: Just for the hell of it, I ran the dig command above and it returned this:

```
dig @8.8.8.8 hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com

; <<>> DiG 9.8.4-rpz2+rl005.12-P1 <<>> @8.8.8.8 hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 3130
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. IN A

;; AUTHORITY SECTION:
com.                    899     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1405915992 1800 900 604800 86400

;; Query time: 204 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Jul 20 21:13:30 2014
;; MSG SIZE  rcvd: 147

```

That should be right..

---

### Post by alpfa on 2014-07-21
;  DiG 9.9.5-3-Ubuntu  @8.8.8.8 hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com ; (1 server found) ;; global options: +cmd ;; Got answer: ;; ->>HEADER

---

### Post by alpfa on 2014-07-21
```
; <<>> DiG 9.9.5-3-Ubuntu <<>> @8.8.8.8 hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52626
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. IN A

;; ANSWER SECTION:
hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. 0 IN A 198.105.254.64
hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. 0 IN A 198.105.244.64

;; Query time: 179 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Jul 21 09:59:54 MDT 2014
;; MSG SIZE  rcvd: 106
```

---

### Post by CharlesA on 2014-07-21
Definitely a sprint thing. I would recommend getting in touch with them and seeing how to disable that search feature.

---

### Post by sandyd on 2014-07-21
> **alpfa said:**
> ```
; <<>> DiG 9.9.5-3-Ubuntu <<>> @8.8.8.8 hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52626
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. IN A

;; ANSWER SECTION:
hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. 0 IN A 198.105.254.64
hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii.com. 0 IN A 198.105.244.64

;; Query time: 179 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Jul 21 09:59:54 MDT 2014
;; MSG SIZE  rcvd: 106
```

My suspicions were correct, the sprint mobile hotspot is intercepting your DNS requests.
See [https://community.sprint.com/baw/thread/72225](https://community.sprint.com/baw/thread/72225)
[https://forums.opendns.com/comments.php?DiscussionID=1277](https://forums.opendns.com/comments.php?DiscussionID=1277)

---

### Post by Elfy on 2014-07-21
title changed to something that's actually helpful for others

---

### Post by fugu2 on 2014-07-23
another thing you might consider doing is just blocking sprints dns packets directly. 
```

iptables -I INPUT 1 -p udp -m udp --sport 53 -m string --hex-string "|73 65 61 72 63 68 2d 68 65 6c 70 07 73 70 69 72 69 6e 74 03 63 6f 6d|" --algo bm -j DROP

```
this might not be exactly right, I didnt test it for accuracy. you may need to adjust the hex code. But this might give you the desired results.

---

### Post by SeijiSensei on 2014-07-23
This is a common behavior by ISPs.  They hijack unresolvable DNS requests and redirect them to a page that shows advertising.  Search Google for "dns hijacking by isp" and you'll see lots of results.

---

### Post by PondPuppy on 2014-07-23
Yes. I was fortunate; I found an opt-out page which actually disabled the ISP hijack.

---

### Post by nuts2 on 2014-08-01
It is probably just the NSA trying to see if you have any illegal cat pictures.

---

