---
title: "Unable to receive mail."
date: 2012-02-07
forum: Server Platforms
---

### Post by satimis on 2012-02-07
Hi all,

postfix can send mail but fails to receive mail.

fixed ip address
hostname - ser01.mydomain.com
On router - ports 25/443/995/80/8080/etc. pointing to 192.168.0.218 (local ip of the server)

I was following;
Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 11.10)
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10)

building this server on ubuntu-10.04 (LTS)


1)
sent 1st mail to server on yahoo mail.
[email]sales@mydomain.com[/email]

Failed

# tail /var/log/mail.log```

Feb  7 13:40:11 ser01 amavis[1106]: (01106-02) Passed CLEAN, [98.139.91.228] [xxx.xxx.xxx.xxx] <somebody@yahoo.com> -> <sales@mydomain.com>, Message-ID: <1328593199.63314.YahooMailNeo@web113203.mail.gq1.yahoo.com>, mail_id: c5+qVqqIhNZV, Hits: 0.992, size: 2971, queued_as: 8D257A009E, dkim_id=@yahoo.com,somebody@yahoo.com, 9518 ms
Feb  7 13:40:11 ser01 postfix/smtp[1954]: 78712A0018: to=<sales@mydomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=10, delays=0.78/0/0/9.5, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01106-02, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 8D257A009E)
Feb  7 13:40:11 ser01 postfix/qmgr[1837]: 78712A0018: removed
Feb  7 13:40:11 ser01 postfix/smtp[1960]: 8D257A009E: to=<sales@mydomain.com>, relay=none, delay=0.06, delays=0.02/0/0.04/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=mail.mydomain.com type=A: Host not found)
Feb  7 13:40:11 ser01 postfix/cleanup[1953]: 9DD18A009F: message-id=<20120207054011.9DD18A009F@ser01.mydomain.com>
Feb  7 13:40:11 ser01 postfix/bounce[1961]: 8D257A009E: sender non-delivery notification: 9DD18A009F
Feb  7 13:40:11 ser01 postfix/qmgr[1837]: 9DD18A009F: from=<>, size=5501, nrcpt=1 (queue active)
Feb  7 13:40:11 ser01 postfix/qmgr[1837]: 8D257A009E: removed
Feb  7 13:40:14 ser01 postfix/smtp[1960]: 9DD18A009F: to=<somebody@yahoo.com>, relay=mta6.am0.yahoodns.net[66.94.236.34]:25, delay=2.7, delays=0/0/1.1/1.7, dsn=2.0.0, status=sent (250 ok dirdel)
Feb  7 13:40:14 ser01 postfix/qmgr[1837]: 9DD18A009F: removed

```

2)
sent 2nd mail to server on yahoo mail.
[email]sales@ser01.mydomain.com[/email]

# tail /var/log/mail.log ```

Feb  7 13:28:06 ser01 postfix/smtpd[1931]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
Feb  7 13:28:06 ser01 postfix/smtpd[1931]: warning: TLS library problem: 1931:error:0906D06C:PEM routines:PEM_read_bio:no start line:pem_lib.c:650:Expecting: ANY PRIVATE KEY:
Feb  7 13:28:06 ser01 postfix/smtpd[1931]: warning: TLS library problem: 1931:error:140B0009:SSL routines:SSL_CTX_use_PrivateKey_file:PEM lib:ssl_rsa.c:669:
Feb  7 13:28:09 ser01 postfix/smtpd[1931]: warning: 122.179.144.143: hostname ABTS-mum-Dynamic-143.144.179.122.airtelbroadband.in verification failed: Name or service not known
Feb  7 13:28:09 ser01 postfix/smtpd[1931]: connect from unknown[122.179.144.143]
Feb  7 13:28:10 ser01 postfix/smtpd[1931]: NOQUEUE: reject: RCPT from unknown[122.179.144.143]: 550 5.1.1 <mydomain@mydomain.com>: Recipient address rejected: User unknown in virtual mailbox table; from=<kphrfysejngwdu@angelpuss.org> to=<mydomain@mydomain.com> proto=SMTP helo=<angelpuss.org>
Feb  7 13:28:10 ser01 postfix/smtpd[1931]: disconnect from unknown[122.179.144.143]
Feb  7 13:31:30 ser01 postfix/anvil[1934]: statistics: max connection rate 1/60s for (smtp:122.179.144.143) at Feb  7 13:28:09
Feb  7 13:31:30 ser01 postfix/anvil[1934]: statistics: max connection count 1 for (smtp:122.179.144.143) at Feb  7 13:28:09
Feb  7 13:31:30 ser01 postfix/anvil[1934]: statistics: max cache size 1 at Feb  7 13:28:09

```

Pls help.  TIA


B.R.
satimis

---

### Post by Wayne_V on 2012-02-07
do you have mx records (primary and secondary) configured in dns for your domain?

---

### Post by satimis on 2012-02-07
> **Wayne_V said:**
> do you have mx records (primary and secondary) configured in dns for your domain?

Whether you meant on resolv.conf?  Bind9 is not installed on the server.

The server is running on a VM of Oracle VirtualBox

Server
$ cat /etc/resolv.conf ```

nameserver xxx.xxx.xxx.xxx (ISP dns)
nameserver 192.168.0.1

```

on host
$ cat /etc/resolv.conf ```

nameserver 192.168.0.1

```

satimis

---

### Post by lisati on 2012-02-07
> **satimis said:**
> Whether you meant on resolv.conf?  Bind9 is not installed on the server.

The server is running on a VM of Oracle VirtualBox

Server
$ cat /etc/resolv.conf ```

nameserver xxx.xxx.xxx.xxx (ISP dns)
nameserver 192.168.0.1

```

on host
$ cat /etc/resolv.conf ```

nameserver 192.168.0.1

```

satimis
MX = "Mail Exchange". Have a look here: [http://en.wikipedia.org/wiki/MX_record](http://en.wikipedia.org/wiki/MX_record)

---

### Post by satimis on 2012-02-07
> **lisati said:**
> MX = "Mail Exchange". Have a look here: [http://en.wikipedia.org/wiki/MX_record](http://en.wikipedia.org/wiki/MX_record)

Ah I see.  Thanks

On domain register website```

Host	Points to
@	xxx.xxx.xxx.xxx (fixed ip)
ser01	xxx.xxx.xxx.xxx (fixed ip)

CNAME (Alias)
Host	Points to
e	ser01.mydomain.com
email	ser01.mydomain.com
imap	imap.secureserver.net
pop	ser01.mydomain.com
smtp	ser01.mydomain.com
webmail	ser01.mydomain.com
www	@

MX (Mail Exchanger)
Priority	Host	Points
30		@	mailstore1.secureserver.net
20		@	smtp.secureserver.net
10		@	ser01.mydomain.com

```

sent both;
[email]sales@mydomain.com[/email]
[email]sales@ser01.mydomain.com[/email]

both mails rejected.


$ tail /var/log/mail.log ```

Feb  7 15:31:00 ser01 amavis[1143]: (01143-01) Passed CLEAN, [98.139.91.98] [xxx.xxx.xxx.xxx] <somebody@yahoo.com> -> <sales@mydomain.com>, Message-ID: <1328599852.43564.YahooMailNeo@web113208.mail.gq1.yahoo.com>, mail_id: gmkC4Dg1vFzJ, Hits: 0.993, size: 2965, queued_as: C1B62A009B, dkim_id=@yahoo.com,somebody@yahoo.com, 5816 ms
Feb  7 15:31:00 ser01 postfix/smtp[1695]: 64F99A0018: to=<sales@mydomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=6.6, delays=0.79/0.01/0.01/5.8, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01143-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as C1B62A009B)
Feb  7 15:31:00 ser01 postfix/qmgr[1579]: 64F99A0018: removed
Feb  7 15:31:00 ser01 postfix/smtp[1702]: C1B62A009B: to=<sales@mydomain.com>, relay=none, delay=0.06, delays=0.02/0/0.04/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=mail.mydomain.com type=A: Host not found)
Feb  7 15:31:00 ser01 postfix/cleanup[1694]: D81CAA009C: message-id=<20120207073100.D81CAA009C@ser01.mydomain.com>
Feb  7 15:31:00 ser01 postfix/bounce[1703]: C1B62A009B: sender non-delivery notification: D81CAA009C
Feb  7 15:31:00 ser01 postfix/qmgr[1579]: D81CAA009C: from=<>, size=5495, nrcpt=1 (queue active)
Feb  7 15:31:00 ser01 postfix/qmgr[1579]: C1B62A009B: removed
Feb  7 15:31:03 ser01 postfix/smtp[1702]: D81CAA009C: to=<somebody@yahoo.com>, relay=mta7.am0.yahoodns.net[98.139.175.225]:25, delay=3, delays=0.01/0/0.94/2.1, dsn=2.0.0, status=sent (250 ok dirdel)
Feb  7 15:31:03 ser01 postfix/qmgr[1579]: D81CAA009C: removed

```


On rejected mail```

<somebody@yahoo.com>: Host or domain name not found. Name service error for
    name=mail.mydomain.com type=A: Host not found
test 01

```

B.R.
satimis

---

### Post by Wayne_V on 2012-02-07
what does "dig mydomain.com mx" say?   it can take up to 48 hours for changes at your domain register to propagate.

---

### Post by satimis on 2012-02-07
> **Wayne_V said:**
> what does "dig mydomain.com mx" say?   it can take up to 48 hours for changes at your domain register to propagate.
On host terminal
================

$ dig mydomain.com mx```

; <<>> DiG 9.7.3 <<>> mydomain.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55645
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 2, ADDITIONAL: 5

;; QUESTION SECTION:
;mydomain.com.			IN	MX

;; ANSWER SECTION:
mydomain.com.		3600	IN	MX	10 ser01.mydomain.com.
mydomain.com.		3600	IN	MX	20 smtp.secureserver.net.
mydomain.com.		3600	IN	MX	30 mailstore1.secureserver.net.

;; AUTHORITY SECTION:
mydomain.com.		2636	IN	NS	ns26.domaincontrol.com.
mydomain.com.		2636	IN	NS	ns25.domaincontrol.com.

;; ADDITIONAL SECTION:
ser01.mydomain.com. 2896	IN	A	xxx.xxx.xxx.xxx
smtp.secureserver.net.	4	IN	A	216.69.186.201
mailstore1.secureserver.net. 4	IN	A	72.167.238.201
ns25.domaincontrol.com.	49235	IN	A	216.69.185.13
ns26.domaincontrol.com.	49235	IN	A	208.109.255.13

;; Query time: 53 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Feb  7 19:41:48 2012
;; MSG SIZE  rcvd: 253

```

$ dig ser01.mydomain.com mx```

; <<>> DiG 9.7.3 <<>> ser01.mydomain.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44137
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ser01.mydomain.com.	IN	MX

;; AUTHORITY SECTION:
mydomain.com.		900	IN	SOA	ns25.domaincontrol.com. dns.jomax.net. 2012020702 28800 7200 604800 3600

;; Query time: 54 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Feb  7 19:43:39 2012
;; MSG SIZE  rcvd: 109

```


$ dig mail.mydomain.com mx```

; <<>> DiG 9.7.3 <<>> mail.mydomain.com mx
;; global options: +cmd
;; connection timed out; no servers could be reached

```


On server (VM) terminal
=======================

$ dig mail.mydomain.com mx```

; <<>> DiG 9.7.0-P1 <<>> mail.mydomain.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 25279
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.mydomain.com.              IN      MX

;; AUTHORITY SECTION:
mydomain.com.            2750    IN      SOA     ns25.domaincontrol.com. dns.jomax.net. 2012020702 28800 7200 604800 3600

;; Query time: 33 msec
;; SERVER: 202.14.67.4#53(202.14.67.4)
;; WHEN: Tue Feb  7 19:45:07 2012
;; MSG SIZE  rcvd: 102

```

B.R.
satimis

---

### Post by Wayne_V on 2012-02-07
so lets back up a little

- you have one static IP from your ISP?
- you have registered your domain name with a registrar and have DNS management capability?
- you have assigned your static IP to your router?
- your router is also you dhcp server and dns server (forwards dns request to your ISP)?
- you have 2(?) servers NAT'd behind your router: one physical and one virtual, both in 192.168.0.x (the vbox server is not NAT'd by the physical server, you are using a bridged interface)?
- you have updated the DNS config at your registrar and waited ~48 hours for the changes to propagate?

I think your resolv.conf should be identical on all systems behind your router.
This line concerns me:  
> Feb  7 15:31:00 ser01 postfix/smtp[1702]: C1B62A009B: to=<sales@mydomain.com>, relay=none, delay=0.06, delays=0.02/0/0.04/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=mail.mydomain.com type=A: Host not found)

Where is mail.mydomain.com coming from?  Was that an old entry in DNS that hasn't updated yet?

Does 'nslookup ser01.mydomain.com' give your static IP on ALL systems, and does 'nslookup <static IP>' give ser01.mydomain.com on ALL systems?

---

### Post by satimis on 2012-02-07
> **Wayne_V said:**
> so lets back up a little

- you have one static IP from your ISP?

Yes

> 
- you have registered your domain name with a registrar and have DNS management capability?

Yes

> 
- you have assigned your static IP to your router?

Yes

> 
- your router is also you dhcp server and dns server (forwards dns request to your ISP)?

Yes

> 
- you have 2(?) servers NAT'd behind your router: one physical and one virtual, both in 192.168.0.x (the vbox server is not NAT'd by the physical server, you are using a bridged interface)?

One host (desktop) for running VirtualBox and one VM, the server
Both bridged interface
Both in 192.168.0.x

> 
- you have updated the DNS config at your registrar and waited ~48 hours for the changes to propagate?

No.  About 3 hrs after the changes.

> 
I think your resolv.conf should be identical on all systems behind your router.

They are almost the same.

> 
This line concerns me:  
> Feb  7 15:31:00 ser01 postfix/smtp[1702]: C1B62A009B: to=<sales@mydomain.com>, relay=none, delay=0.06, delays=0.02/0/0.04/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=mail.mydomain.com type=A: Host not found)

Where is mail.mydomain.com coming from?  Was that an old entry in DNS that hasn't updated yet?

$ cat /etc/postfix/main.cf | grep mydestination```

mydestination = localhost.$mydomain.com, localhost, mail.mydomain.com
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

```

> 
Does 'nslookup ser01.mydomain.com' give your static IP on ALL systems, and does 'nslookup <static IP>' give ser01.mydomain.com on ALL systems?
Performed following tests:-

On host
=======

$ nslookup ser01.mydomain.com```

Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	ser01.mydomain.com
Address: xxx.xxx.xxx.xxx (fixed ip)

```

$ nslookup xxx.xxx.xxx.xxx (fixed ip)```

;; connection timed out; no servers could be reached

```


Sent a mail from yahoo.  Mail rejected

$ tail /var/log/mail.log```

Feb  7 22:37:19 ser01 amavis[1134]: (01134-01) Passed CLEAN, [98.139.91.100] [220.232.213.178] <somebody@yahoo.com> -> <sales@mydomain.com>, Message-ID: <1328625429.15507.YahooMailNeo@web113213.mail.gq1.yahoo.com>, mail_id: DAfTIjwKFbBC, Hits: -0.107, size: 2956, queued_as: C530CA00AE, dkim_id=@yahoo.com,somebody@yahoo.com, 6551 ms
Feb  7 22:37:19 ser01 postfix/smtp[1709]: A1970A0098: to=<sales@mydomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=7.4, delays=0.81/0.01/0.01/6.5, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01134-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as C530CA00AE)
Feb  7 22:37:19 ser01 postfix/qmgr[1571]: A1970A0098: removed
Feb  7 22:37:19 ser01 postfix/smtp[1716]: C530CA00AE: to=<sales@mydomain.com>, relay=none, delay=0.09, delays=0.01/0/0.07/0, dsn=5.4.6, status=bounced (mail for mail.mydomain.com loops back to myself)
Feb  7 22:37:19 ser01 postfix/cleanup[1708]: DEF13A00AF: message-id=<20120207143719.DEF13A00AF@ser01.mydomain.com>
Feb  7 22:37:19 ser01 postfix/bounce[1717]: C530CA00AE: sender non-delivery notification: DEF13A00AF
Feb  7 22:37:19 ser01 postfix/qmgr[1571]: DEF13A00AF: from=<>, size=5372, nrcpt=1 (queue active)
Feb  7 22:37:19 ser01 postfix/qmgr[1571]: C530CA00AE: removed
Feb  7 22:37:24 ser01 postfix/smtp[1716]: DEF13A00AF: to=<somebody@yahoo.com>, relay=mta6.am0.yahoodns.net[66.94.236.34]:25, delay=4.2, delays=0/0/1.7/2.5, dsn=2.0.0, status=sent (250 ok dirdel)
Feb  7 22:37:24 ser01 postfix/qmgr[1571]: DEF13A00AF: removed

```


On Server VM
============

$ nslookup ser01.mydomain.com```

Server:         202.14.67.4
Address:        202.14.67.4#53

Non-authoritative answer:
Name:   ser01.mydomain.com
Address: xxx.xxx.xxx.xxx (fixed ip)

```

$ nslookup xxx.xxx.xxx.xxx (fixed ip)```

Server:         202.14.67.4 (ISP DNS)
Address:        202.14.67.4#53

** server can't find 178.213.232.220.in-addr.arpa.: NXDOMAIN

```

$ telnet localhost smtp```

Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ser01.mydomain.com ESMTP Postfix (Ubuntu)
ehlo mydomain.com
250-ser01.mydomain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:<sales@mydomain.com>
250 2.1.0 Ok
rcpt to:<sales@mydomain.com>
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Hi sales
.
250 2.0.0 Ok: queued as E6976A0098
quit
221 2.0.0 Bye
Connection closed by foreign host.

```


tail /var/log/mail.log```

Feb  7 22:46:16 ser01 postfix/smtp[1781]: E6976A0098: to=<sales@mydomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=67, delays=61/0/0.01/5.7, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01135-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 2B658A00B1)
Feb  7 22:46:16 ser01 postfix/qmgr[1571]: E6976A0098: removed
Feb  7 22:46:16 ser01 postfix/smtp[1787]: 2B658A00B1: to=<sales@mydomain.com>, relay=none, delay=0.06, delays=0.02/0/0.04/0, dsn=5.4.6, status=bounced (mail for mail.domain.com loops back to myself)
Feb  7 22:46:16 ser01 postfix/cleanup[1779]: 3C308A00B2: message-id=<20120207144616.3C308A00B2@ser01.domain.com>
Feb  7 22:46:16 ser01 postfix/qmgr[1571]: 3C308A00B2: from=<>, size=2772, nrcpt=1 (queue active)
Feb  7 22:46:16 ser01 postfix/bounce[1788]: 2B658A00B1: sender non-delivery notification: 3C308A00B2
Feb  7 22:46:16 ser01 postfix/qmgr[1571]: 2B658A00B1: removed
Feb  7 22:46:16 ser01 postfix/smtp[1787]: 3C308A00B2: to=<sales@mydomain.com>, relay=none, delay=0.04, delays=0/0/0.04/0, dsn=5.4.6, status=bounced (mail for mail.domain.com loops back to myself)
Feb  7 22:46:16 ser01 postfix/qmgr[1571]: 3C308A00B2: removed
Feb  7 22:46:18 ser01 postfix/smtpd[1775]: disconnect from localhost[127.0.0.1]

```

$ ls -l /home/vmail/```

total 0

```
No mail received.


B.R.
satimis

---

### Post by Wayne_V on 2012-02-07
why mydestination = localhost.$mydomain.com, localhost, mail.mydomain.com?  mail.mydomain.com is not a host on your network is it?

see [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html).

make sure resolv.conf is the same - nslookup/dig must be working before you can send mail.

make sure the network on the VM is working - is the default route correct?  can you ping the router and or hosts on the internet?

and also, don't expect anything to work until dig/nslookup shows the hostnames/IP's that you entered at your registrar (and that can take 48 hours)

---

### Post by satimis on 2012-02-08
> **Wayne_V said:**
> why mydestination = localhost.$mydomain.com, localhost, mail.mydomain.com?  mail.mydomain.com is not a host on your network is it?

Have made following change;

$ cat /etc/postfix/main.cf | grep mydestination```

mydestination = ser01.mydomain.com, localhost, localhost.localdomain
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

```

> 
make sure resolv.conf is the same - nslookup/dig must be working before you can send mail.

On host terminal:
$ cat /etc/resolv.conf ```

# Generated by NetworkManager
nameserver 192.168.0.1
nameserver xxx.xxx.xxx.xxx (ISP DNS)
nameserver xxx.xxx.xxx.xxx (ISP DNS)

```

On server VM terminal:
$ cat /etc/resolv.conf ```

nameserver 192.168.0.1
nameserver xxx.xxx.xxx.xxx (ISP DNS)
nameserver xxx.xxx.xxx.xxx (ISP DNS)

```

> 
make sure the network on the VM is working - is the default route correct?  can you ping the router and or hosts on the internet?

All work w/o problem.  Server can be remotely connected on host via ssh.

> 
and also, don't expect anything to work until dig/nslookup shows the hostnames/IP's that you entered at your registrar (and that can take 48 hours)

According to the Howto on;```

13 Populate The Database And Test
If you want to make entries in the other two tables, that would look like this:
...

```
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10)

I already created mail.mydomain.com record```

INSERT INTO `transport` (`domain`, `transport`) VALUES ('mydomain.com', 'smtp:mail.mydomain.com');

```

mysql> SELECT * from transport;```

+-------------+-----------------------+
| domain      | transport             |
+-------------+-----------------------+
| mydomain.com | smtp:mail.mydomain.com |
+-------------+-----------------------+
1 row in set (0.00 sec)

```

After spent hours of working, now it comes to following state:-

Mail still can't be received by the server.

$ tail /var/log/mail.log ```

Feb  9 10:04:43 ub1004ser02 postfix/qmgr[1809]: 3B0C0A009A: from=<somebody@yahoo.com>, size=2966, nrcpt=1 (queue active)
Feb  9 10:04:43 ub1004ser02 postfix/smtp[1880]: connect to 127.0.0.1[127.0.0.1]:10024: Connection refused
Feb  9 10:04:43 ub1004ser02 postfix/smtp[1880]: 3B0C0A009A: to=<sales@mydomain.com>, relay=none, delay=1136, delays=1136/0/0/0, dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
Feb  9 10:04:43 ub1004ser02 postfix/smtpd[1872]: connect from e-bs.regit.ru[91.190.232.8]
Feb  9 10:04:44 ub1004ser02 postfix/smtpd[1872]: NOQUEUE: reject: RCPT from e-bs.regit.ru[91.190.232.8]: 550 5.1.1 <mail@mydomain.com>: Recipient address rejected: User unknown in virtual mailbox table; from=<labelling@kneeplace.com> to=<mail@mydomain.com> proto=SMTP helo=<e-bs.regit.ru>
Feb  9 10:04:44 ub1004ser02 postfix/smtpd[1872]: lost connection after RCPT from e-bs.regit.ru[91.190.232.8]
Feb  9 10:04:44 ub1004ser02 postfix/smtpd[1872]: disconnect from e-bs.regit.ru[91.190.232.8]
Feb  9 10:08:04 ub1004ser02 postfix/anvil[1875]: statistics: max connection rate 1/60s for (smtp:206.72.127.11) at Feb  9 10:03:37
Feb  9 10:08:04 ub1004ser02 postfix/anvil[1875]: statistics: max connection count 1 for (smtp:206.72.127.11) at Feb  9 10:03:37
Feb  9 10:08:04 ub1004ser02 postfix/anvil[1875]: statistics: max cache size 1 at Feb  9 10:03:37

```


On server VM terminal
=====================
$ dig mail.mydomain.com```


; <<>> DiG 9.7.0-P1 <<>> mail.mydomain.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 33735
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.mydomain.com.              IN      A

;; AUTHORITY SECTION:
mydomain.com.            3599    IN      SOA     ns25.domaincontrol.com. dns.jomax.net. 2012020704 28800 7200 604800 3600

;; Query time: 19 msec
;; SERVER: xxx.xxx.xxx.xxx#53(xxx.xxx.xxx.xxx) (ISP DNS)
;; WHEN: Thu Feb  9 10:16:27 2012
;; MSG SIZE  rcvd: 102

```

$ nslookup ser01.mydomain.com```

Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
Name:   ser01.mydomain.com
Address: xxx.xxx.xxx.xxx (fixed IP)

```

$ nslookup xxx.xxx.xxx.xxx (fixed IP)```

Server:         xxx.xxx.xxx.xxx (ISP DNS)
Address:        xxx.xxx.xxx.xxx#53 (ISP DNS)

** server can't find xxx.xxx.xxx.xxx.in-addr.arpa.: NXDOMAIN

```

I haven't installed bind9.  I'm using ISP DNS.

On host terminal
================

$ dig mail.mydomain.com```


; <<>> DiG 9.7.3 <<>> mail.mydomain.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 49391
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.mydomain.com.		IN	A

;; AUTHORITY SECTION:
mydomain.com.		3510	IN	SOA	ns25.domaincontrol.com. dns.jomax.net. 2012020704 28800 7200 604800 3600

;; Query time: 18 msec
;; SERVER: xxx.xxx.xxx.xxx#53(xxx.xxx.xxx.xxx) (ISP DNS)
;; WHEN: Thu Feb  9 10:17:56 2012
;; MSG SIZE  rcvd: 102

```

$ nslookup ser01.mydomain.com```

Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
Name:   ser01.mydomain.com
Address: xxx.xxx.xxx.xxx (fixed IP)

```

$ nslookup xxx.xxx.xxx.xxx (fixed IP)```

Server:         xxx.xxx.xxx.xxx (ISP DNS)
Address:        xxx.xxx.xxx.xxx#53 (ISP DNS)

** server can't find xxx.xxx.xxx.xxx.in-addr.arpa.: NXDOMAIN

```


B.R.
satimis

---

### Post by Wayne_V on 2012-02-10
again, why mail.mydomain.com?  I don't see an A record for that in the DNS config you posted earlier.

You don't need to run bind - but I would not use 192.168.0.1 for a dns server.  Configure everything to go direct to your real nameservers.  Mail from one host to another in your private network will go out to the public IP rather than the private or localhost but unless you expecting a large amount of internal mail I wouldn't worry about it.  Better to get the public side working first anyway.

Use nmap and make sure the ports are open as expected on your static IP.

Use dig and/or nslookup and make sure that every thing you have configured in your DNS is resolvable on all of your systems (real or virtual).  Until that happens nothing is going to work.   You may need to look for a how-to for your ISP and verify you have DNS configured properly.

---

### Post by satimis on 2012-02-10
> **Wayne_V said:**
> again, why mail.mydomain.com?  I don't see an A record for that in the DNS config you posted earlier.

You don't need to run bind - but I would not use 192.168.0.1 for a dns server.  Configure everything to go direct to your real nameservers.  Mail from one host to another in your private network will go out to the public IP rather than the private or localhost but unless you expecting a large amount of internal mail I wouldn't worry about it.  Better to get the public side working first anyway.

Use nmap and make sure the ports are open as expected on your static IP.

Use dig and/or nslookup and make sure that every thing you have configured in your DNS is resolvable on all of your systems (real or virtual).  Until that happens nothing is going to work.   You may need to look for a how-to for your ISP and verify you have DNS configured properly.

After creating mail.mydomain.com poiting to fixed IP on A(Host) record of domain Register's wedsite, mails arrive.  But they can't be delivered to mail box.

$ ls -al /home/vmail/```

total 20
drwxr-xr-x 2 vmail vmail 4096 2012-02-04 23:12 .
drwxr-xr-x 4 root  root  4096 2012-02-04 23:12 ..
-rw-r--r-- 1 vmail vmail  220 2010-04-19 10:15 .bash_logout
-rw-r--r-- 1 vmail vmail 3103 2010-04-19 10:15 .bashrc
-rw-r--r-- 1 vmail vmail  675 2010-04-19 10:15 .profile

```

Do I need creating a mail box for 'sales'?
```

/home/vmail/satimis.com/sales/

```
?

# tail /var/log/mail.log ```

Feb 11 11:09.56 ser01 postfix/smtpd[1691]: connect from unknown[xxx.xxx.xxx.xxx](fixed IP)
Feb 11 11:09:56 ser01 postfix/smtp[1933]: warning: host mail.mydomain.com[xxx.xxx.xxx.xxx](fixed IP):25 greeted me with my own hostname ser01.mydomain.com
Feb 11 11:09:56 ser01 postfix/smtp[1933]: warning: host mail.mydomain.com[xxx.xxx.xxx.xxx](fixed IP):25 replied to HELO/EHLO with my own hostname ser01.mydomain.com
Feb 11 11:09:56 ser01 postfix/smtp[1933]: 1C0D7A0097: to=<sales@mydomain.com>, relay=mail.mydomain.com[xxx.xxx.xxx.xxx]:25, delay=5.3, delays=0.01/0/5.3/0, dsn=5.4.6, status=bounced (mail for mail.mydomain.com loops back to myself)
Feb 11 11:09:56 ser01 postfix/smtpd[1921]: disconnect from unknown[xxx.xxx.xxx.xxx]
Feb 11 11:09:56 ser01 postfix/cleanup[1926]: 64B88A009C: message-id=<20120211030956.64B88A009C@ser01.mydomain.com>
Feb 11 11:09:56 ser01 postfix/bounce[1934]: 1C0D7A0097: sender non-delivery notification: 64B88A009C
Feb 11 11:09:56 ser01 postfix/qmgr[1910]: 64B88A009C: from=<>, size=5399, nrcpt=1 (queue active)
Feb 11 11:09:56 ser01 postfix/qmgr[1910]: 1C0D7A0097: removed
Feb 11 11:09:58 ser01 postfix/smtp[1933]: 64B88A009C: to=<somebody@yahoo.com>, relay=mta7.am0.yahoodns.net[74.6.140.64]:25, delay=2, delays=0/0/0.65/1.3, dsn=2.0.0, status=sent (250 ok dirdel)
Feb 11 11:09:58 ser01 postfix/qmgr[1910]: 64B88A009C: removed

```

I found following thread:-
Postfix mail for domain.com loops back to myself Error and Solution
[http://www.cyberciti.biz/faq/postfix-mail-for-domaincom-loops-back-to-myself-error-and-solution/](http://www.cyberciti.biz/faq/postfix-mail-for-domaincom-loops-back-to-myself-error-and-solution/)

suggesting;```

mydestination = localhost.$mydomain, localhost, mail.example.com

```

But it didn't work for me here.

Now
# cat /etc/postfix/main.cf | grep mydestination```

mydestination = ser01.mydomain.com, localhost, localhost.localdomain
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

```

$ cat /etc/resolv.conf ```

nameserver 192.168.0.1
nameserver xxx.xxx.xxx.xxx (ISP DNS)
nameserver xxx.xxx.xxx.xxx (ISP DNS)

```

$ dig mydomain.com mx```

; <<>> DiG 9.7.3 <<>> mydomain.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4936
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 2, ADDITIONAL: 4

;; QUESTION SECTION:
;mydomain.com.			IN	MX

;; ANSWER SECTION:
mydomain.com.		3600	IN	MX	10 ser01.mydomain.com.
mydomain.com.		3600	IN	MX	20 smtp.secureserver.net.
mydomain.com.		3600	IN	MX	30 mailstore1.secureserver.net.

;; AUTHORITY SECTION:
mydomain.com.		987	IN	NS	ns26.domaincontrol.com.
mydomain.com.		987	IN	NS	ns25.domaincontrol.com.

;; ADDITIONAL SECTION:
ser01.mydomain.com. 3600	IN	A	xxx.xxx.xxx.xxx (fixed ip)
ns25.domaincontrol.com.	73026	IN	AAAA	2607:f208:206::d
ns26.domaincontrol.com.	82527	IN	A	208.109.255.13
ns26.domaincontrol.com.	73028	IN	AAAA	2607:f208:302::d

;; Query time: 230 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sat Feb 11 11:33:09 2012
;; MSG SIZE  rcvd: 261

```

$ nslookup mydomain.com```

Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	mydomain.com
Address: xxx.xxx.xxx.xxx (fixed ip)

```

$ dig xxx.xxx.xxx.xxx (fixed ip) mx```

; <<>> DiG 9.7.3 <<>> xxx.xxx.xxx.xxx (fixed ip) mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 58212
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;xxx.xxx.xxx.xxx (fixed ip).		IN	MX

;; AUTHORITY SECTION:
.			10798	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2012021001 1800 900 604800 86400

;; Query time: 18 msec
;; SERVER: 202.14.67.4#53(202.14.67.4)
;; WHEN: Sat Feb 11 11:34:10 2012
;; MSG SIZE  rcvd: 108

```

$ nslookup xxx.xxx.xxx.xxx (fixed ip)```

Server:		202.14.67.4
Address:	202.14.67.4#53

** server can't find 178.213.232.220.in-addr.arpa.: NXDOMAIN

```


I don't have nmap installed.

$ netstat -tap```

(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:ssh                   *:*                     LISTEN      -               
tcp        0      0 *:smtp                  *:*                     LISTEN      -               
tcp        0      0 localhost.localdo:10023 *:*                     LISTEN      -               
tcp        0      0 localhost.localdo:10024 *:*                     LISTEN      -               
tcp        0      0 localhost.localdo:10025 *:*                     LISTEN      -               
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN      -               
tcp       60      0 localhost.localdo:39560 localhost.localdo:10025 CLOSE_WAIT  -               
tcp        0      0 ser01.mydomain:ssh 192.168.0.200:46567     ESTABLISHED -               
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -               
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      -               
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      -               
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      -               
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      -               
tcp6       0      0 [::]:www                [::]:*                  LISTEN      -   

```


B.R.
satimis

---

