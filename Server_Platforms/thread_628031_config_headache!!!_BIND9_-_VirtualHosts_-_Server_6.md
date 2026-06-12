---
title: "config headache!!! BIND9 - VirtualHosts - Server 6.06LTS"
date: 2007-11-30
forum: Server Platforms
---

### Post by magpy on 2007-11-30
Hi Ubuntu !!

Great site and really informative too.  I have a question that I need help with.  It is about DNS (BIND9) mainly 'IP to Hostname resolution' on an ubuntu server.  I have my router and LAN set up.  At the moment I am using the static IP Address given by my ISP 80.45.123.31 which is assigned to the router which is also the gateway device for all local machines.  The router has DHCP turned off and all (4) local machines are subnetted to the router's IP in the same subnetwork.  All are populated with the  DNS servers 212.74.112.66 & 212.74.112.67 (given via my ISP), my LAN is described below:



     ROUTER
(80.45.123.31)
           |
           |
           |                
MAC OSX            
(80.45.123.32)                      
       
XP LAP-TOP
(80.45.123.34)
                                                                          
UBUNTU 6.06                                                                  
 LTS                                                                                                                              
(80.45.123.33)                                                   
WEB SERVER                                                                                                                                                 

XP HOME
 (80.45.123.36)
*[via wireless b/g]                           
                          


*All other machines are connected via ethernet cables

I am behind an SUA (Single User Account) and I have set up 'port forwarding' on port 80 (http) to my UBUNTU server (80.45.123.33).  I have also set two firewall rules for the server which allows requests to and from it on the same port to be accepted from 'anyone' in a "many-2-one||one-2-many relationship".
I hope allowing traffic to and from the server in the direction of WAN->LAN || LAN->WAN.

My domain names are registered with tiscali((1) 'criticalmatters.net') and the other with telivo/nominet((2) 'plinth-project-london.org.uk').  I have tried "nslookup" and "dig" for my domain names which returned:

//results for dig
//FOR criticalmatters.net

Lookup has started ...

; <<>> DiG 9.2.2 <<>> criticalmatters.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30140
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;criticalmatters.net.		IN	A

//This is what I managed to get as a result of your how to at:                                                                                                //http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html
//when I had nothing configured I only got the tiscali nameserver
//after your instructions I got the 'IN    A' record set above - a possible result?

;; AUTHORITY SECTION:
criticalmatters.net.	7095	IN	SOA	pipino.tiscali.it. nsadmin.it.tiscali.com. 249396159 86400 3600 604800 86400

;; Query time: 56 msec
;; SERVER: 212.74.112.66#53(212.74.112.66)
;; WHEN: Fri Nov 30 19:10:05 2007
;; MSG SIZE  rcvd: 112




Lookup has started ...

//AND ALSO FOR plinth-project-london.org.uk

; <<>> DiG 9.2.2 <<>> plinth-project-london.org.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22184
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;plinth-project-london.org.uk.	IN	A       //Same as above only difference is the nameserver of the company

;; AUTHORITY SECTION:
plinth-project-london.org.uk. 6451 IN	SOA	ns0.telivo.com. hostmaster.telivo.com. 2006062201 28800 7200 604800 86400

;; Query time: 32 msec
;; SERVER: 212.74.112.66#53(212.74.112.66)
;; WHEN: Fri Nov 30 19:22:59 2007
;; MSG SIZE  rcvd: 107


                      ***********************************************************************************
//below nslookup

Lookup has started ...

Server:		212.74.112.66
Address:	212.74.112.66#53

Non-authoritative answer:
*** Can't find plinth-project-london.org.uk: No answer

--

Lookup has started ...

Server:		212.74.112.66
Address:	212.74.112.66#53

Non-authoritative answer:
*** Can't find criticalmatters.net: No answer



I believe that I have set up apache o.k. but when I restart the web server I get this message:

[warn] NameVirtualHost 80.45.123.33:0 has no VirtualHosts //which I don't fully understand

I have a feeling that this thread could get longer for example I imagine that for one to help diagnose any problem one may need to know my UBUNTU set up,
i.e. /etc/hosts, /etc/network.interfaces, and /etc/resolv.conf and possiblly even config files in /etc/bind such as named.conf, named.conf.local, named.conf.options, db.local, db.plinth-project-london.org.uk and db.criticalmatters.net - maybe even also apache virtual host files at /sites-available.  If anyone wants to take a look at those files I can upload them sharpish.

Any help MUCH!!!! MUCH!!!! appreciated as this has been a real head wrangler.

---

