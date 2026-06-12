---
title: "How To: Create a DynDns Linux Server"
date: 2007-10-28
forum: Server Platforms
---

### Post by mattc908 on 2007-10-28
Hey guys and girls, I know a lot of people want a step by step guide on how to set up a FTP server using DYNDNS. Well I set up an easy guide on how you can. Just for kicks I hosting the guide on the server I created by using the guide I built. I test the steps to make sure they work! Let me know what you guys think. This guide is VERY step by step, and very simple. 


Guide:
[http://insightahoy.com/forum/viewtopic.php?f=4&t=2&p=2#p2](http://insightahoy.com/forum/viewtopic.php?f=4&t=2&p=2#p2)

---

### Post by meatpan on 2007-10-28
I'm glad to see a how-to that incorporates DynDNS services, however, there are a few problems with step by step 'checklist' guides.  

First, users tend to copy commands verbatim, without considering the purpose or implications of the command.  Secondly, if a detail of any of the required dependencies change, the entire checklist guide is out-of-date.  Perhaps I've had bad luck lately, but it seems like the *majority* of do-it-all installation checklists are out-of-date.

I think you could quickly improve your guide by adding some descriptive text around the major points of the checklist, and perhaps some links to external sites that describe key server protocols, design, etc....  Also, it wouldn't hurt to cross-reference some of the official ubuntu server documentation that describes the basic steps of OS installation.  Finally,  I recommend specifiying the major/minor verions of ALL the software packages you use.

Good Luck,

Meatpan

---

### Post by mattc908 on 2007-10-28
Alright, Ill try and put the guide into more depth! Yeah that is a major problem they do get out of date very fast.

---

### Post by tronica on 2007-11-16
thanks, been looking for something like this for awhile.

---

### Post by jtodaro on 2007-11-17
> **mattc908 said:**
> Guide: [http://mattc908.dyndns.org/forum/viewtopic.php?t=5](http://mattc908.dyndns.org/forum/viewtopic.php?t=5)

Curious as to why you are using both ipcheck and ddclient. They both seem to do the same thing (I run only ddclient, this is why I asked).

```
*[root@gatekeeper:~] aptitude show ipcheck
Package: ipcheck
Description: Dyndns.org client to register your dynamic IP address
 The Dynamic DNS service allows you to alias a dynamic IP address to a static
 hostname, allowing your computer to be more easily accessed from various
 locations on the Internet.

 This is a simple Python script to register your dynamic IP address using the
 NIC V2.0 protocol.

 The script is very easy to use and supports multiple methods for determining
 the external IP (parsing interfaces on the local machine, web based IP
 detection, direct support for devices from Linksys, Netgear, Draytek, Netopia,
 HawkingTech, Watchgard, Cayman, Nexland, ZyXEL, SMC, Compex, UgatePlus, DLink
 and Cisco).  It also supports the dyndns offline mode.

 Starting with version 0.141 ipcheck uses https by default and will fall back to
 http if a timeout occurs.
```

```
*[root@gatekeeper:~] aptitude show ddclient
Package: ddclient
Description: Update dynamic IP address at DynDNS.com
 A perl based client to update your dynamic IP address at DynDNS.com (or other
 dynamic DNS services such as Hammernode, Zoneedit or EasyDNS), thus allowing
 you and others to use a fixed hostname (myhost.dyndns.org) to access your
 machine. This client supports both the dynamic and (near) static services, MX
 setting, and alternative host. It caches the address, and only attempts the
 update if the address actually changes.

 For more information on DynDNS.com, see http://www.dyndns.com/.
```

---

### Post by mattc908 on 2007-11-17
IPCheck you can run manual updates while DDclient runs automatic, wasn't sure if DDclient could run manual.

---

### Post by mkzimms on 2007-11-29
i would be very careful about putting your server on the DMZ... no reason for it.  keep it behind your router's firewall and just open the ports you need to it.  

22 for SSH
80 and 8080 for HTTP
443 for HTTPS
20 and 21 for FTP
69500-69550 for PASV

etc... for whatever services your running.

also, if your using a linksys router, most of them already have dyndns support on them (i know my wrt54g v1 does), just enter your username and password, they will automatically update for you.

another thing to watch out for is ISP protocol blocking.  i use cablevision and since i dont pay 15$ extra a month for boost they block incomming reqs on ports 80, 8080, 25, 20, 21.  well, F THAT!  set your ports differently and your configs accordingly.  so for http you could use port 580 and give your URL as

[http://myserver.dyndns.org:580/](http://myserver.dyndns.org:580/)

---

### Post by mattc908 on 2007-12-04
Changed Address:
[http://insightahoy.com/forum/viewtopic.php?f=4&t=2&p=2#p2](http://insightahoy.com/forum/viewtopic.php?f=4&t=2&p=2#p2)

---

