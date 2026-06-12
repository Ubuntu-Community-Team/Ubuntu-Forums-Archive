---
title: "Sign emails with OpenDkim + Postfix + Ubuntu 10.04 64x"
date: 2010-09-30
forum: Server Platforms
---

### Post by pmla on 2010-09-30
Sign emails with OpenDkim + Postfix + Ubuntu 10.04 64x

How-to implement a domain key signature using Postfix Ubuntu based email server. Implementing a domain key will help your outgoing email not being marked as SPAM by the receiving servers that implement DKIM signatures verification., i.e. Yahoo, Gmail, etc.

[FULL HOW-TO]("http://www.pmabox.com/index.php/iceland-blog/47-sign-your-emails-with-opendkim-postfix-in-ubuntu-1004-64x")

---

### Post by clegends on 2010-10-07
We love you! You are a star. Thanks for the great tutorial. My emails and server are now happy. Installing this now.

---

### Post by clegends on 2010-10-12
Hi, I'm having issues with this guide. 4 days ago it seemed great, and everything installed nicely... for the life of me I can't figure out what's gone wrong. I keep getting the "dkim=perm error" in verification emails, & am told that my dkim key can't be found. I've followed this guide twice now from scratch. Can someone help me troubleshoot this? Thanks.

edit: have tried so many things now... can't get either dk-filter (dkim keys, used currently by yahoo) or opendkim working. Seems like my zone files in bind aren't working. Keep getting this error from [email]check-auth@verifier.port25.com[/email]


----------------------------------------------------------
DKIM check details:
----------------------------------------------------------
Result:         permerror (key "selector._domainkey.curiouslegends.com.au" doesn't exist)
ID(s) verified:

edit: Have moved my question to this thread: [http://guide.ubuntuforums.org/showthread.php?t=1596450](http://guide.ubuntuforums.org/showthread.php?t=1596450)
I would appreciate some help, please reply there. Thanks!

---

### Post by pmla on 2010-10-18
You have major dns issues that need to be fixed. Your master dns server is no where to be found.

You need to insert IN TXT records in your master dns server ;)
ns1.xname.org


CheckDNS.NET is asking root servers about authoritative NS for domain
  Got DNS list for 'curiouslegends.com.au' from o.audns.net.au or o.audns.net.au or o.audns.net.au or o.audns.net.au
  Found NS record 'ns1.xname.org', but could not resolve it to IP, answer from 192.5.6.30: host 'ns1.xname.org' not found. 
  Found NS record: ns.curiouslegends.com.au[124.254.118.5], was resolved to IP address by o.audns.net.au 
  Found NS record: ns0.xname.org[195.234.42.1], was resolved to IP address by a0.org.afilias-nst.info 
  Found NS record: ns2.xname.org[88.191.64.64], was resolved to IP address by a0.org.afilias-nst.info 
  Domain has 4 DNS server(s) 

[B]CheckDNS.NET is verifying if NS are alive
  DNS server ns1.xname.org failed and will be dropped from other tests 
  Error fetching SOA from ns.curiouslegends.com.au [124.254.118.5], request timed out. Probably DNS server is offline. [/B]
  DNS server ns0.xname.org[195.234.42.1] is alive and authoritative for domain curiouslegends.com.au 
  DNS server ns2.xname.org[88.191.64.64] is alive and authoritative for domain curiouslegends.com.au 
  2 server(s) are alive 

CheckDNS.NET checks if all NS have the same version
**  Master DNS defined by SOA (curiouslegends.com.au) was not found among NS records. **

CheckDNS.NET is verifying if NS are alive
  DNS server ns.curiouslegends.com.au failed and will be dropped from other tests 

CheckDNS.NET checks if all NS have the same version
  All 2 your servers have the same zone version 201010068 

CheckDNS.NET verifies www servers
  Checking HTTP server [www.curiouslegends.com.au](www.curiouslegends.com.au) [124.254.118.5] 
  HTTP server [www.curiouslegends.com.au](www.curiouslegends.com.au)[124.254.118.5] answers on port 80 
  Received: HTTP/1.1 200 OK (Server: Apache/2.2.14 (Ubuntu)) . . . Curious Legends Theatre Company. . Curious .Legends Theatre .Company | &copy; 2007 . APM .Internetworks Pty Ltd. | . [email]info@curiouslegends.com.au[/email]. | (61) .3 8682 8577 . . Home. | . About Us. |. Shows. | . Workshops. | . Festivals. | . Birthday Parties. | . Sponsors. |  

CheckDNS.NET tests mail-servers
  Domain curiouslegends.com.au has only one mail-server 
  Checking mail server (PRI=1) mail.curiouslegends.com.au [124.254.118.5] 
  Mail server mail.curiouslegends.com.au[124.254.118.5] answers on port 25 
  <<< 220 curiouslegends.com.au ESMTP Postfix (Ubuntu)
  >>> HELO [www.checkdns.net](www.checkdns.net)
  <<< 250 curiouslegends.com.au
  >>> MAIL FROM: <dnscheck@uniplace.com>
  <<< 250 2.1.0 Ok
  >>> RCPT TO: <postmaster@curiouslegends.com.au>
  <<< 250 2.1.5 Ok
  >>> QUIT
  Mail server mail.curiouslegends.com.au [124.254.118.5] accepts mail for curiouslegends.com.au 
  All MX are configured properly

---

### Post by clegends on 2010-10-18
Thanks for that, now I'm really confused... better read up on bind again. Here is my db.curiouslegends.com.au file... what am I doing wrong?

```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     curiouslegends.com.au. curiouser.curiouslegends.com.au.$
                      2010101402        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
@       IN      A       124.254.118.5
@       IN      AAAA    ::1
ns      IN      A       124.254.118.5
www     IN      A       124.254.118.5
@       IN      MX 1    mail.curiouslegends.com.au.
mail    IN      A       124.254.118.5
curiouslegends.com.au.  IN      NS      ns0.xname.org.
curiouslegends.com.au.  IN      NS      ns1.xname.org.
curiouslegends.com.au.  IN      NS      ns2.xname.org.
curiouslegends.com.au.  IN      TXT     "v=spf1 a mx ~all"
2010._domainkey.curiouslegends.com.au.  IN      TXT "k=rsa; p=(key, but not posted to this forum)
mail._domainkey.curiouslegends.com.au.  IN      TXT     "k=rsa; p=(key, not posted to this forum)

```

---

### Post by clegends on 2010-10-18
Getting closer... now all three of the xname.org dns servers are resolving correctly, but I'm still getting this error from [www.checkdns.net](www.checkdns.net)
```

Error fetching SOA from ns.curiouslegends.com.au [124.254.118.5], request timed out. Probably DNS server is offline.
{/code]

Any help would be appreciated... no idea why my main dns server is not working... and yet the slaves seem to be working fine. Also, there is no problem with my mail server, so my mx records are fine.
[code]
Mail server mail.curiouslegends.com.au [124.254.118.5] accepts mail for curiouslegends.com.au 
  All MX are configured properly

```

I'm guessing that means my /etc/bind/named.conf.local file is fine, so that the problem must be in my /etc/bind/db.curiouslegends.com.au file below (edited it just now and restarted bind. DKIM config is gone, will add it back after bind is working correctly.) Any idea what's wrong with  my configuration? Thanks. I really appreciate your time.

```


;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.curiouslegends.com.au. curiouser.curiouslegends.com.$
                      2010101905        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
@       IN      A       124.254.118.5
@       IN      AAAA    ::1
ns      IN      A       124.254.118.5
www     IN      A       124.254.118.5
@       IN      MX 1    mail.curiouslegends.com.au.
mail    IN      A       124.254.118.5
curiouslegends.com.au.  IN      NS      ns0.xname.org.
curiouslegends.com.au.  IN      NS      ns1.xname.org.
curiouslegends.com.au.  IN      NS      ns2.xname.org.
curiouslegends.com.au.  IN      TXT     ns0.xname.org.
curiouslegends.com.au.  IN      TXT     ns1.xname.org.
curiouslegends.com.au.  IN      TXT     ns2.xname.org.
curiouslegends.com.au.  IN      TXT     "v=spf1 a mx ~all"

```

---

### Post by pmla on 2010-10-18
Have you inserted IN TXT:

2010._domainkey.curiouslegends.com.au.  IN      TXT "k=rsa; p=(key, but not posted to this forum)
mail._domainkey.curiouslegends.com.au.  IN      TXT     "k=rsa; p=(key, not posted to this forum)

in your public master and secondary dns servers ns"x".xname.org?

---

### Post by clegends on 2010-10-18
I had them in my primary master, ns.curiouslegends.com.au, who's database file is: /etc/bind/db.curiouslegends.com.au

I took them out temporarily, as I want to solve my bind errors first, as that's likely what's causing problems with my DNS. To explain, I'm hosting my primary DNS from my webserver, physically located under my desk, and at ip 124.254.118.5

The 3 slave DNS servers are through xname.org, so I'm unable to configure them at all, except asking them nicely through their website to point at my ip, and listing them as slaves in my config files.

From checkdns.org, it seems my main dns server is not being recognized, while the slaves are. I keep getting the error:
```
Error fetching SOA from ns.curiouslegends.com.au [124.254.118.5], request timed out. Probably DNS server is offline.
```

That makes me think that there's some issue with my db.curiouslegends.com.au config file, and/or possibly with my reverse dns file: db.124

I'm stumped, and fairly new at this. Any other ideas?

edit: Anyway, let me know if you're able to help me out with sorting my DNS issues. I'm aware this thread is for opendkim, which is my primary goal of sorting this, however I understant if this is getting off-topic. Let me know if you want me to post elsewhere until I sort my dns issues. Thanks again.

---

### Post by pmla on 2010-10-18
The public DNS records should be the same for all servers. Including IN TXT.

My advice. Remove your bind from the equation. Use 2 dns servers from xname.org with exact same settings... IN TXT included.

A solid clean DNS is a must in order for opendkim to work. As stated in the begging of my how-to.

You can try other free online dns server providers. Just google it "free dns servers"... hummm Google Public DNS, that's new.

 Hope it works for you.

---

### Post by clegends on 2010-10-18
Hmm. Thanks for your advice, but I think I'll try and get my own bind server working first. Part of the point of having my own server is the control associated with that... including stuffing around with bind. Will post in the general forums to see if I can sort my config issue, then post back when my dns issues are resolved. Thanks again for your help, I really appreciate it.

The google public dns seems to be mainly for caching nameservers... I don't think they have a project for dedicated nameservers... yet. Seems to work well though. Cheers.

---

### Post by clegends on 2010-10-19
Right, I've fixed my dns issues. Problem was my iptables firewall... I had forgotten to open port UDP 53 for DNS when I last reconfigured my firewall. 

Now the issue is with dkim, and specifically error messages I get after following your tutorial. When I put this in my db.curiouslegends.com.au file:
```

2010._domainkey.curiouslegends.com.au. IN   TXT "k=rsa; t=y; p=(real key)"

```
I get this error:
```

curiouser@curioushost:/etc/mail$ named-checkzone curiouslegends.com.au /etc/bind/db.curiouslegends.com.au
dns_rdata_fromtext: /etc/bind/db.curiouslegends.com.au:26: unbalanced quotes
dns_master_load: /etc/bind/db.curiouslegends.com.au:27: label too long
dns_master_load: /etc/bind/db.curiouslegends.com.au:28: label too long
dns_master_load: /etc/bind/db.curiouslegends.com.au:29: syntax error
zone curiouslegends.com.au/IN: loading from master file /etc/bind/db.curiouslegends.com.au failed: unbalanced quotes
zone curiouslegends.com.au/IN: not loaded due to errors.

```
Those lines are specific top the above TXT. Then when I run dig I get:
```

curiouser@curioushost:/etc/mail$ dig @ns.curiouslegends.com.au TXT curiouslegends.com.au

; <<>> DiG 9.7.0-P1 <<>> @ns.curiouslegends.com.au TXT curiouslegends.com.au
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 64859
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;curiouslegends.com.au.		IN	TXT

;; Query time: 1 msec
;; SERVER: 124.254.118.5#53(124.254.118.5)
;; WHEN: Tue Oct 19 17:17:33 2010
;; MSG SIZE  rcvd: 39

```

I've now removed the TXT entry above, and now named-checkzone loads fine, and with dig I get:
```


curiouser@curioushost:/etc/mail$ dig @ns.curiouslegends.com.au TXT curiouslegends.com.au

; <<>> DiG 9.7.0-P1 <<>> @ns.curiouslegends.com.au TXT curiouslegends.com.au
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5374
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 4, ADDITIONAL: 1

;; QUESTION SECTION:
;curiouslegends.com.au.		IN	TXT

;; ANSWER SECTION:
curiouslegends.com.au.	604800	IN	TXT	"ns2.xname.org."
curiouslegends.com.au.	604800	IN	TXT	"v=spf1 a mx ~all"
curiouslegends.com.au.	604800	IN	TXT	"ns0.xname.org."
curiouslegends.com.au.	604800	IN	TXT	"ns1.xname.org."

;; AUTHORITY SECTION:
curiouslegends.com.au.	604800	IN	NS	ns.curiouslegends.com.au.
curiouslegends.com.au.	604800	IN	NS	ns0.xname.org.
curiouslegends.com.au.	604800	IN	NS	ns2.xname.org.
curiouslegends.com.au.	604800	IN	NS	ns1.xname.org.

;; ADDITIONAL SECTION:
ns.curiouslegends.com.au. 604800 IN	A	124.254.118.5

;; Query time: 1 msec
;; SERVER: 124.254.118.5#53(124.254.118.5)
;; WHEN: Tue Oct 19 17:29:57 2010
;; MSG SIZE  rcvd: 245

```

Can you tell me what's going wrong here? It seems specific to your guide for opendkims. Thanks.

---

### Post by clegends on 2010-10-20
Bump....

Could you please help? The issue I'm having seems specific to your guide now that I've fixed my DNS issues. I'd really appreciate your help and time. Thanks.

---

### Post by Arenlor on 2010-11-11
I can't guarantee anything, but I think you accidentally copied it across multiple lines instead of on only one line.

---

### Post by clegends on 2010-11-11
I totally don't understand that... is this related to this post? Thanks anyway for your reply.

---

### Post by masgeeks on 2011-06-18
Hi - I had followed the instructions in this post last fall for Maverick x64 for Postfix with OpenDKIM worked like a charm... :D  

Does anyone know if it will work with Natty x64...???

I've set up a new Natty x64 VM and will be transferring my hosting from Maverick x64 to this new VM, so just doing a little home work right now on everything.  

If anyone knows if the instructions for Maverick x64 for OpenDKIM works with Natty x64 would sure appreciate some feedback...

Thanks in advance...!!!

---

### Post by TheGrave on 2013-02-14
> **pmla said:**
> Sign emails with OpenDkim + Postfix + Ubuntu 10.04 64x

How-to implement a domain key signature using Postfix Ubuntu based email server. Implementing a domain key will help your outgoing email not being marked as SPAM by the receiving servers that implement DKIM signatures verification., i.e. Yahoo, Gmail, etc.

[FULL HOW-TO]("http://www.pmabox.com/index.php/iceland-blog/47-sign-your-emails-with-opendkim-postfix-in-ubuntu-1004-64x")

Link is dead. Any mirrors?

---

### Post by howefield on 2013-02-14
Old thread closed.

---

