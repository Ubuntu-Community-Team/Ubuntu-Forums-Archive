---
title: "How to make domain pointing to server"
date: 2007-01-11
forum: Server Platforms
---

### Post by satimis on 2007-01-11
Hi folks,

Ubuntu-6.06-LAMP-server-amd64
Xfce4 desktop

I have registered "satimis.com" with Godaddy.com and my server is now running on static IP.  The domain is active parking on Godaddy.com and rechargeable.  Please advise how to make it pointing to my server.

I visited "Total DNS Control" and "Total DNS Control and MX Records" pages on "Godaddy.com" and could not figure out how to change them.

Contacted their Technical Support with a reply;```

You are receiving a Go Daddy parked page since the domain satimis.com is 
parked on our servers. In addition, the domain's A record is pointed at our parked     
IP address. In order to point your domain to a different location you will need to 
modify the A record and nameservers for your domain. Unfortunately we are 
limited on the support we can provide for pointing your domain at your own 
server.

```

Please help.  TIA.


B.R.
satimis

---

### Post by Paerez on 2007-01-11
First off, do you have a static IP address? If you have plain old home cable/dsl, the answer is no. If you bought business dsl or cable, the answer is yes.

---

### Post by satimis on 2007-01-11
Hi Paerez;

> 
do you have a static IP address? 

Yes.

> 
If you have plain old home cable/dsl, the answer is no. If you bought business dsl or cable, the answer is yes.
business dsl

Connection:-
Server --> Router --> Modem --> ISP

The router was pre-set by ISP with Virtual IP

satimis@mail:~$ sudo ping [www.satimis.com](www.satimis.com)
```

PING satimis.com (68.178.232.100) 56(84) bytes of data.
64 bytes from parkwebwin-v01.prod.mesa1.secureserver.net (68.178.232.100): icmp_seq=1 ttl=116 time=259 ms
64 bytes from parkwebwin-v01.prod.mesa1.secureserver.net (68.178.232.100): icmp_seq=2 ttl=116 time=253 ms
64 bytes from parkwebwin-v01.prod.mesa1.secureserver.net (68.178.232.100): icmp_seq=4 ttl=116 time=259 ms
64 bytes from parkwebwin-v01.prod.mesa1.secureserver.net (68.178.232.100): icmp_seq=7 ttl=116 time=262 ms
......

--- satimis.com ping statistics ---
11 packets transmitted, 8 received, 27% packet loss, time 10034ms
rtt min/avg/max/mdev = 251.992/258.609/266.339/4.603 ms

```

satimis@mail:~$ whois 68.178.232.100```


OrgName:    Go Daddy Software
OrgID:      GDS-31
Address:    14455 N Hayden Road
Address:    Suite 226
City:       Scottsdale
StateProv:  AZ
PostalCode: 85260
Country:    US
....

```
It pointed to Godaddy.com

Tks.


B.R.
satimis

---

### Post by Paerez on 2007-01-11
So basically, you need to tell godaddy what your server's ip is. First, you have to find out your server's ip. The only way I know how to do this is go to [http://whatismyip.com/](http://whatismyip.com/) using your server's web browser.

Then, you have to give this IP to godaddy. I guess you are having trouble telling godaddy your IP, and I can't help you there because I don't have a godaddy account so I don't know how it works. There should be somewhere you can type in your server's ip.

---

### Post by satimis on 2007-01-12
Hi Paerez;

I have my fixed IP.  But I can't figure out how to edit the items on Godaddy.com


Total DNS Control of Godaddy.com```
  	
satimis.com

Host	        Points To		    TTL		        Actions
@ 	        68.178.232.100 		    3600		change/delete

CNAMES (Aliases)
Host		Points To		                        TTL	Actions
www 		@ 				                3600    change/delete
	
mobilemail 	mobilemail-v01.prod.mesa1.secureserver.net 	3600	change/delete
	
pda 		mobilemail-v01.prod.mesa1.secureserver.net 	3600	change/delete
	
email 		email.secureserver.net 				3600	change/delete
	
mail 		pop.secureserver.net 				3600	change/delete
	
pop 		pop.secureserver.net 				3600	change/delete
	
smtp 		smtp.secureserver.net 				3600	change/delete
	
ftp 		@ 						3600	change/delete
	
webmail 	webmail.secureserver.net 			3600	change/delete
	
e 		email.secureserver.net 				3600	change/deleteTXT (Text)
	

MX (Mail Exchange)
Priority	Host		Goes To			        TTL	Actions
0 		@ 		smtp.secureserver.net 	        3600	change/delete
	
10 		@ 		mailstore1.secureserver.net 	3600	change/delete


TXT (Text)
Host		TXT Value		TTL			Actions

```
I tried to make;```

Host	        Points To		    TTL		        Actions
@ 	        my fixed IP 		    3600		change/delete

```

But it did not work.  On ping it still pointed to Godaddy.com IP


B.R.
satimis

---

### Post by Paerez on 2007-01-12
After you change it, it may take a few minutes before it goes to your real site.

If you type your static IP into your web browser, does your site come up? If not, it may not be godaddy's problem.

---

### Post by satimis on 2007-01-12
Hi Paerez,

> 
After you change it, it may take a few minutes before it goes to your real site.

I have a little confusion here about which IP address I have to replace the IP address under "Points To"

I have 2 fixed IP provided by ISP
1) WAN IP
2) Virtual IP on the router.

> 
If you type your static IP into your web browser, does your site come up? If not, it may not be godaddy's problem.
1) if typing WAN IP on browser it popup requesting for "User Name" and Password.  I contacted ISP understanding that it was the IP of their router.

2) if typing "Virtual IP" the test homepage of the server displayed.

Tks.

B.R.
satimis

---

### Post by chrisfay on 2007-01-12
> if typing WAN IP on browser it popup requesting for "User Name" and Password. I contacted ISP understanding that it was the IP of their router.

You need to log into the router and port forward port 80 to your internal (apparently 'virtual') IP. I thought virtual IP's were more for load balancing and reducing physical network interface dependencies rather than ISP configured nat type translation, but whatever....:-? 

Becuase the router's web based admin pannel functions on port 80, you will continue to get that prompt until you forward the port to your server. You may also want to double check that remote administration is turned off and possibly change the port that the web utility functions on to something other than 80.

---

### Post by satimis on 2007-01-14
Hi chrisfay,

Problem solved by putting "satimis.com" on godaddy.com pointing to the WAN IP "220.232.213.178".  Waiting for 24 hrs then both "www.satimis.com" and "satimis.com" can browse the test homepage on the server.  Not the Virtual IP "192.168.0.10" as told previously by ISP.

> 
You need to log into the router and port forward port 80 to your internal (apparently 'virtual') IP. I thought virtual IP's were more for load balancing and reducing physical network interface dependencies rather than ISP configured nat type translation, but whatever....:-? 

Becuase the router's web based admin pannel functions on port 80, you will continue to get that prompt until you forward the port to your server. You may also want to double check that remote administration is turned off and possibly change the port that the web utility functions on to something other than 80.
The router which has been preset was supplied by ISP.  I'm not allowed to touch it.  That is really my headache.  ISP blocks all ports on the Virtual IP 192.168.0.10 to 192.168.0.60.  I have to request them to unblock ports 25 and 80 on "192.168.0.10".  To read the router panel I need login and password which ISP did not release.

Is there anyway to get over it?  Buy another router putting the ISP router aside.  Tks.


B.R.
satimis

---

### Post by chrisfay on 2007-01-14
> Problem solved
Glad to hear it!

> Is there anyway to get over it? Buy another router putting the ISP router aside. Tks

hmmm......im not sure about that. I've never heard of firewalled preset routers being distributed by ISP's to customers so not really sure how to circumvent it. It seems to me that for them to go to the trouble of configuring such a thing, it may a bit harder than just swapping it out for a standard router. There may be some integrated connection between your modem and their router that you can't modify...But who knows, you never know until you try!

---

### Post by satimis on 2007-01-14
Hi chrisfay,

> 
hmmm......im not sure about that. I've never heard of firewalled preset routers being distributed by ISP's to customers so not really sure how to circumvent it. It seems to me that for them to go to the trouble of configuring such a thing, it may a bit harder than just swapping it out for a standard router. There may be some integrated connection between your modem and their router that you can't modify...But who knows, you never know until you try!
I'll talk to ISP about the router on following points;

1) Although the router is on loan to me which is part of the contract, it is a component of my local area network[LAN]
2) I have absolute right to manage my LAN unless the router is a component of ISP's server network.

Any advice?   Or points to add?  TIA

Besides What information are needed from ISP to configure a router in my LAN.

What is the reason for ISP to control clients' LAN?  TIA


B.R.
satimis

---

### Post by TSMJ on 2007-01-15
> **Paerez said:**
> After you change it, it may take a few minutes before it goes to your real site.

It's usually 24 hours

---

### Post by satimis on 2007-01-15
Hi TSMJ,

> 
It's usually 24 hours

For godaddy.com propragation took overnight.  Tks.


B.R.
satimis

---

### Post by Paerez on 2007-01-15
Ah, see I use dyndns.org to give me a hostname to my server in my closet, then I have 1&1 map a real domain to the dyndns name using the CNAME field. 1&1 only took a couple minutes, I think.

---

