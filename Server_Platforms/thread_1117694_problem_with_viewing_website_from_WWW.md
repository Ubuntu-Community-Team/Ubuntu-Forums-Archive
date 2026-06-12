---
title: "problem with viewing website from WWW"
date: 2009-04-06
forum: Server Platforms
---

### Post by Spikerok on 2009-04-06
can view websites on LAN but no on WWW
have tried using proxy.org service, its working but still not sure if others can see it from WWW

dig from [http://www.kloth.net/services/dig.php](http://www.kloth.net/services/dig.php)
ns2.web-a.org.uk
[PHP]
; <<>> DiG 9.3.2 <<>> @ns2.web-a.org.uk web-a.org.uk A
 ; (1 server found)
 ;; global options:  printcmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11341
 ;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2
 
 ;; QUESTION SECTION:
 ;web-a.org.uk.			IN	A
 
 ;; ANSWER SECTION:
 web-a.org.uk.		86400	IN	A	92.9.234.125
 
 ;; AUTHORITY SECTION:
 web-a.org.uk.		86400	IN	NS	ns1.web-a.org.uk.
 web-a.org.uk.		86400	IN	NS	ns2.web-a.org.uk.
 
 ;; ADDITIONAL SECTION:
 ns1.web-a.org.uk.	86400	IN	A	92.9.234.125
 ns2.web-a.org.uk.	86400	IN	A	92.9.234.125
 
 ;; Query time: 85 msec
 ;; SERVER: 92.9.234.125#53(92.9.234.125)
 ;; WHEN: Mon Apr  6 14:50:52 2009
 ;; MSG SIZE  rcvd: 114
[/PHP]

ns1.web-a.org.uk
[PHP]
; <<>> DiG 9.3.2 <<>> @ns1.web-a.org.uk web-a.org.uk A
 ; (1 server found)
 ;; global options:  printcmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30265
 ;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2
 
 ;; QUESTION SECTION:
 ;web-a.org.uk.			IN	A
 
 ;; ANSWER SECTION:
 web-a.org.uk.		86400	IN	A	92.9.234.125
 
 ;; AUTHORITY SECTION:
 web-a.org.uk.		86400	IN	NS	ns2.web-a.org.uk.
 web-a.org.uk.		86400	IN	NS	ns1.web-a.org.uk.
 
 ;; ADDITIONAL SECTION:
 ns1.web-a.org.uk.	86400	IN	A	92.9.234.125
 ns2.web-a.org.uk.	86400	IN	A	92.9.234.125
 
 ;; Query time: 52 msec
 ;; SERVER: 92.9.234.125#53(92.9.234.125)
 ;; WHEN: Mon Apr  6 16:11:21 2009
 ;; MSG SIZE  rcvd: 114
[/PHP]

[http://www.ip-plus.net/tools/dns_check_set.en.html](http://www.ip-plus.net/tools/dns_check_set.en.html)
[PHP]
DNS check tool	Back

Domain web-a.org.uk, DNS server 92.9.234.125


Check if the server "92.9.234.125" is configured for "web-a.org.uk" ... ok.

Check SOA Record ...
Server: host-92-9-234-125.as43234.net
Address: 92.9.234.125

Query about web-a.org.uk for record types SOA
Trying web-a.org.uk ...
web-a.org.uk        	86400	IN	SOA	ns1.web-a.org.uk admin.web-a.org.uk (
			2009040605	;serial (version)
			28800	;refresh period (8 hours)
*** WARNING *** Refresh 28800 , use recommended value "10800"

			7200	;retry interval (2 hours)
*** WARNING *** Retry   7200 , use recommended value "3600"

			604800	;expire time (1 week)
			86400	;default ttl (1 day)

Check NS Records ...
Server: host-92-9-234-125.as43234.net
Address: 92.9.234.125

Query about web-a.org.uk for record types NS
Trying web-a.org.uk ...
Query done, 2 answers, authoritative status: no error
web-a.org.uk        	86400	IN	NS	ns1.web-a.org.uk
ns1.web-a.org.uk is primary nameserver
web-a.org.uk        	86400	IN	NS	ns2.web-a.org.uk
ns2.web-a.org.uk is secondary nameserver
Additional information:
ns1.web-a.org.uk    	86400	IN	A	92.9.234.125
ns2.web-a.org.uk    	86400	IN	A	92.9.234.125
Found IP address "92.9.234.125" for server "ns1.web-a.org.uk"
*** WARNING *** failed reverse lookup for "92.9.234.125"
*** WARNING *** 92.9.234.125  PTR record not found.
*** WARNING *** It's recommended to have reverse lookup for your nameservers
Found IP address "92.9.234.125" for server "ns2.web-a.org.uk"
*** WARNING *** failed reverse lookup for "92.9.234.125"
*** WARNING *** 92.9.234.125  PTR record not found.
*** WARNING *** It's recommended to have reverse lookup for your nameservers

Check SOA Record for Consistency on all Servers  ...
web-a.org.uk        	NS	ns1.web-a.org.uk
ns1.web-a.org.uk	admin.web-a.org.uk	(2009040605 28800 7200 604800 86400)
web-a.org.uk        	NS	ns2.web-a.org.uk
ns1.web-a.org.uk	admin.web-a.org.uk	(2009040605 28800 7200 604800 86400)


Check Zone Transfer
This may take a while, please wait ... /opt/wwwtools-1.0/checkdom/hostsqs  -Z -a -l -v -A -G -D -S   -P 92.9.234.125 web-a.org.uk 92.9.234.125 2>&1
 done.
*** WARNING ***  !!! web-a.org.uk MX host secure.web-a.org.uk does not exist



No errors found in "web-a.org.uk"
5 warnings found in "web-a.org.uk"
[/PHP]

---

### Post by Spikerok on 2009-04-06
DNS zone file
[PHP]
$TTL        86400
@       IN      SOA     ns1.web-a.org.uk. admin.web-a.org.uk. (
                        2009040605       ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;
                NS      ns1.web-a.org.uk.              ; Inet Address of name server 1
                NS      ns2.web-a.org.uk.              ; Inet Address of name server 2
;

  MX      10 secure.web-a.org.uk.

web-a.org.uk.      A        92.9.234.125
www       A       192.168.1.66
server1       A       92.9.234.125

web-a.org.uk.       TXT  "v=spf1 a mx ptr ~all"

;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;
ns1     A       92.9.234.125
ns2     A       92.9.234.125
[/PHP]

---

### Post by Spikerok on 2009-04-06
port 53 and 80 are open

---

### Post by Spikerok on 2009-04-06
pump

---

### Post by ephmanjmm on 2009-04-06
Did you realize that www is pointing to a private IP address?

www       A       192.168.1.66

---

### Post by Spikerok on 2009-04-06
ty, missed it out ;)

---

