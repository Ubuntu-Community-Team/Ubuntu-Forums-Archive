---
title: "Configuring Two Nameservers in Bind"
date: 2007-09-19
forum: Server Platforms
---

### Post by inlikeflint86 on 2007-09-19
Ok so I'm registered with Godaddy.com and it says it wants two nameservers if i'm going to use my own. I followed this tutorial -- [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093) and had my nameserver working but was wondering what configurations i have to make to the files to get two nameservers working.... any help from somebody that set up their own DNS server through Godaddy.com would be greatly appreciated.


Thanks,
Ben

---

### Post by HermanAB on 2007-09-20
The workaround is to assign two IP addresses to your machine.  BIND and most everything else will automatically glom onto both addresses and GoDaddy will be happy!

---

### Post by GigaVolt on 2007-09-20
Or create two glue record to one IP adress. ;)

---

### Post by inlikeflint86 on 2007-09-21
ok well i already split my ethernet card into seperate IP addresses but i'm not sure what files to edit to get it all working -- here is my domain zone file:

$TTL 86400
mydomain.com.	IN	SOA	ns1.mydomain.com. me.mydomain.com. (
								
			      	1		
			 	604800		
			  	86400		
				2419200		
				604800 
)
mydomain.com.	IN	NS		ns1.mydomain.com.
mydomain.com.	IN	NS		ns2.mydomain.com.
mydomain.com.	IN	MX	10	mta.mydomain.com.
www			IN	A		192.168.1.10
ns1			IN	A		192.168.1.11
ns2			IN	A		192.168.1.12
mta			IN	A		192.168.1.13


but the server only seems to work when i put this as my resolv.conf file: 

search mydomain.com
nameserver 192.168.1.10
domain mydomain

if i put in 192.168.1.11 and 192.168.1.12 as the nameserver IP's-- it doesn't work but if i do 192.168.1.10 i get this--



;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13912
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;bigeasychange.com.             IN      A

;; ANSWER SECTION:
mydomain.com.      86400   IN      A       192.168.1.10

;; AUTHORITY SECTION:
mydomain.com.      86400   IN      NS      ns1.mydomain.com.

;; ADDITIONAL SECTION:
ns1.mydomain.com.  86400   IN      A       192.168.1.10

;; Query time: 8 msec
;; SERVER: 192.168.1.10#53(192.168.1.10)
;; WHEN: Fri Sep 21 21:37:10 2007
;; MSG SIZE  rcvd: 85

I hope my problem is evident when seeing these files...thanks for the help so far

---

### Post by robert_pectol on 2007-09-22
The whole purpose for more than one nameserver is robustness and redundancy.  As a rule-of-thumb, you want at least 2 nameservers on completely unrelated networks, preferably geographically separated, in order to achieve this.  Here's what I propose.  Configure your own nameserver and make it the master.  Then, go with one of the free nameservice secondaries (such as [http://twisted4life.com](http://twisted4life.com)) that are available and let them slave your zone.  This way, all you have to do is maintain your zone, and changes will automatically be retrieved by the secondary through automatic zone transfers.  With this scenerio, you give Godaddy your nameserver's IP as the primary nameserver, and then the secondary's IP as the secondary nameserver.  You meet their requirement AND accomplish robustness and diversity in your nameservice!

---

### Post by HermanAB on 2007-09-22
However, if you have only one web server or one mail server, then having redundant DNS doesn't help...

If you have a room full of web servers, then it makes sense to have at least two DNS, but I don't think that is the case here.

---

### Post by robert_pectol on 2007-09-24
> **HermanAB said:**
> However, if you have only one web server or one mail server, then having redundant DNS doesn't help...
But it doesn't hurt, and it really is the recommended way to do it!

> **HermanAB said:**
> If you have a room full of web servers, then it makes sense to have at least two DNS, but I don't think that is the case here.
Whether it be a, 'room full of web servers' or a single server, having robust name resolution is a good idea.  I could understand if establishing and utilizing a secondary nameserver, as I suggested, were a difficult and time consuming thing to do.  In contrast, it's a very easy thing to do!

---

