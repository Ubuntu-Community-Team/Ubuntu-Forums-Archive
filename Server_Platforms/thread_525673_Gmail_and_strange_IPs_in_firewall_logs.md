---
title: "Gmail and strange IPs in firewall logs"
date: 2007-08-14
forum: Server Platforms
---

### Post by zuuul on 2007-08-14
Hello, I have a strange question.

I've noticed in my firewall logs, blocked connection attempts, coming from an ip beginning with 172.x.x.x of varying numbers. I know it should be an internal IP adress, but i dont have that range on my LAN. My range is 192.168.x.x.

I've noticed, that it appears after checking email on Googles Email service, Gmail. But no software from google is actually installed on my LAN, i only use Evolution to check the email via pop:port 995.

How can this IP appear?
Is there any way i can investigate this on my own, and if so where should i begin, and what procedures should i take?

My LAN looks like this:
Smoothwall firewall
A fileserver with Fedora 7
My regular desktop running ubuntu 7.04

Both the fileserver and desktop have wifi. On the desktop wifi is disabled in bios, but I cant do that on the fileserver, however it doesn't have any antenna attached. Could it be possible to connect via wifi, even without the antenna attached? When i type ifconfig -a on the fileserver, no ip address is listed on wifi, only eth0, which is the interface i use. All my network is wire-based.

I don't like smoothwalls forum, because i think they are very harsh on newbies there, although the firewall is excellent, so I ask here.

Best regards.

---

### Post by p_quarles on 2007-08-14
I would start by getting some information about the device. Make a note of the current IP address, and then use nmap:
```
sudo nmap -O 172.xx.xx.xx
```
If all ports are closed, you'll also need to add the "-P0" (<-zero) option.

---

### Post by zuuul on 2007-08-14
Hi p_quarles, thanks for the quick response.


sudo nmap -O -P0 172.21.186.1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-08-14 22:13 CEST
Warning:  OS detection for 172.21.186.1 will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port
All 1697 scanned ports on 172.21.186.1 are filtered
Too many fingerprints match this host to give specific OS details

OS detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap finished: 1 IP address (1 host up) scanned in 18.074 seconds

I dont know what to make of it? but this is the output. It says the host is up?

---

### Post by zuuul on 2007-08-14
Time       |        in    |   out |  proto  |    source       |        Src port | destination | dst port

21:33:25  	eth2  	-  	  TCP  	  172.21.127.11        11104 	 <myip>         45352
21:33:25 	eth2 	- 	  TCP 	172.21.231.35	       11104     <myip>	        45355
21:33:25 	eth2 	- 	  TCP 	172.21.13.15	         11018     <myip>        59607
21:33:25 	eth2 	- 	  TCP 	 172.21.14.11	         11018     <myip>	 59608

Thats an example of the log.

Edit: I should mention that Eth2 is the nic connected the the internet, as red interface. So it appears to come from outside? which is what i dont understand.

---

### Post by bapoumba on 2007-08-14
Okay, I was puzzled by your post. I ran a whois on one of the IP you mentioned:
```
:~ $ whois 172.21.127.11

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   172.16.0.0 - 172.31.255.255 
CIDR:       172.16.0.0/12 
NetName:    IANA-BBLK-RESERVED
NetHandle:  NET-172-16-0-0-1
Parent:     NET-172-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    
RegDate:    1994-03-15
Updated:    2002-09-12

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  abuse@iana.org

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  abuse@iana.org

# ARIN WHOIS database, last updated 2007-08-13 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.
```

Looking for that blakhole adress, I found this: [http://www.iana.org/faqs/abuse-faq.htm]("http://www.iana.org/faqs/abuse-faq.htm")
Read the Q&A, looks like this has to do with your DNS.

In any case, the entries in Fs are the ones that have been blocked, ie Fs was doing its job ;)

---

### Post by p_quarles on 2007-08-14
The nmap report is pretty typical. If the address had at least one normal range port open, it would have been able to make a guess at the OS running on it, which might have been a helpful clue.

I guess if I were you, I'd scour all the access logs you can find on the firewall (I take it this is a separate machine running a hardware firewall). 

You said your network is wired, but do you have *any* wireless access points located on the network? On the firewall/router, for instance?

EDIT: Ah. Bapoumba's point is compelling. According to that FAQ, this is a pretty common occurrence.

---

### Post by zuuul on 2007-08-15
Thanks for the info Bapoumpa. If I understand it right, it should be harmless, but I can maybe make it go away, by using my ISPs DNS server, instead of the Smoothwall? As it is now, the firewall is doing this task for my LAN, while itself getting the info from my ISPs DNS, working as a router too. At least i think it works this way. But it is only after getting a new ISP, that I started seeing these "inverted queries" as they seem to be called.

To answer your question p_quarles, then it's true that it is a standalone machine running a linux version, taylored to be a firewall.  It is a NAT firewall, permitting all outgoing while blocking all unauthorized incoming traffic. This I understand is what could be causing the problem I have? The strange thing is, I didn't see these entries, before changing ISP.

I had a mail server up for a month (on this new ISP), on a separate sub-net, that was not exactly broken into, but people tried hard to break in, so i took it down. But since it was on a different sub-net than my LAN, they should not be able to get into my other machines. Also, I have a DynDNS name pointing to my IP, I don't know if that has any significance?

---

### Post by bapoumba on 2007-08-15
> **zuuul said:**
> Thanks for the info Bapoumpa. If I understand it right, it should be harmless, but I can maybe make it go away, by using my ISPs DNS server, instead of the Smoothwall? As it is now, the firewall is doing this task for my LAN, while itself getting the info from my ISPs DNS, working as a router too. At least i think it works this way. But it is only after getting a new ISP, that I started seeing these "inverted queries" as they seem to be called.
...
Also, I have a DynDNS name pointing to my IP, I don't know if that has any significance?
Maybe. Just give it a try and see. I'll look if it could be DynDNS.

---

