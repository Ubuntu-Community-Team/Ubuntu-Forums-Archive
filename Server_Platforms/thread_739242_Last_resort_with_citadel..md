---
title: "Last resort with citadel."
date: 2008-03-29
forum: Server Platforms
---

### Post by dantheman3212 on 2008-03-29
i have been trying for at least two weeks to get my Citadel/DNS server to co-exist with each other, and it just does not seem to work. I've posted a couple threads on the issue, and those seemed to be bypassed for now. 

Here is my problem. Receiving mail from the outside, such as a gmail account works fine, i get the email instantly, and when I send an email from my citadel account to another person on the same domain,it works perfectly. But when I try and send mail from my citadel account to my Gmail account, it just hangs in the SMTP que for at least an hour before saying "connection timed out". And if I go through telnet to send a message through command prompt, i get to RCPT TO: [email]dan@macdonaghs.com[/email] and it says 551 Relaying denied. 

I've been searching google for this problem and get nothing. I've decided to just post all my configuration files on these forums, and see if anyone can see something I'm doing wrong.

Here is how my server is setup. I have an outside IP address of 24.117.5.71 which goes to my router, and have all the right ports opened to forward to my server, who's IP is 192.168.0.4. I have manual static IP set up on the server, which a DHCP lease is giving the MAC address every restart, etc.

First here is my bind9 config file.

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "ptxsolutions.com" {
type master;
file "/etc/bind/zones/ptxsolutions.com.db";
};

zone "5.117.24.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.5.117.24.in-addr.arpa";
};


```

Everything resolves fine, I can get to my website [http://www.ptxsolutions.com]("http://www.ptxsolutions.com")
without a problem, and when I ping that domain it gives me an IP of 24.117.5.71. So i dont think the problem lines within that.

Here is my forward zone.

```

ptxsolutions.com. IN SOA ptxserver.ptxsolutions.com. admin.ptxsolutions.com. (
2006081401
28800
3600
604800
38400 )

ptxsolutions.com. IN NS ptxserver.ptxsolutions.com.
ptxsolutions.com. IN MX 10 ptxsolutions.com.

ptxsolutions.com. IN A 24.117.5.71
www IN A 24.117.5.71
ns1 IN A 24.117.5.71
@ IN A 24.117.5.71
mail IN A 24.117.5.71

```

All seems to be in order with that file, I knew i had to have an MX record in there, and i think i set it up right.

Here is the reverse.

```

@ IN SOA ptxsolutions.com. admin.ptxsolutions.com. (
2006081401;
28800;
604800;
604800;
86400 );

IN NS ptxserver.ptxsolutions.com.
71 IN PTR ptxsolutions.com.

```

The website works from the outside, so I figure my reverse is fine.


My hostname in both /etc/hosts and /etc/hostname is  ```
ptxsolutions.com
```

My /etc/resolve.conf is as follows

```

search ptxsolutions.com
nameserver 24.117.5.71
nameserver 24.116.2.50
nameserver 24.116.2.34

```

And my citadel server is set up as follows.

In Administration->Site Wide->General my node is ptxsolutions, and my FQDN is ptxsolutions.com. Now i have tried numerous changes of the FQDN from ptxserver.ptxsolutions.com to mail.ptxsolutions.com to just [www.ptxsolutions.com](www.ptxsolutions.com). Nothing seems to have any effect on anything.

In Network i have my settings as

PoP3:110
SMTP MTA: 25
Correct forged From: lines during authenticated SMTP is checked
IMAP listener port: 143
Server IP: 0.0.0.0
SMTP MSA: 587
IMAP SSL: 993
POP3 SSl: 995
SMTP SSL: 465

(Quick note: All these ports are forwarded to my IP through my router)

Allow unauthenticated SMTP clients to spoof this site's domains is checked. And with that setting, I have tried it with it both on and off, and with it off, and i tried to send mail it said "You must first log in to ptxsolutions.com to send mail". And with it on it sends error message "Relaying Denied". So I dont know what it should be at.

And in Administration->Domain names and Internet mail configuration
Local Host aliases: ptxsolutions.com
Gateway Domains: ptxsolutions.com
Smart Hosts: ptxsolutions.com

and again in this part of the config, i have tried every possible way to do this, and it still seems to not work.


Here is a couple dig files.

```

dig ptxsolutions.com

; <<>> DiG 9.4.1-P1 <<>> ptxsolutions.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41256
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;ptxsolutions.com.              IN      A

;; ANSWER SECTION:
ptxsolutions.com.       38400   IN      A       24.117.5.71

;; AUTHORITY SECTION:
ptxsolutions.com.       38400   IN      NS      ptxserver.ptxsolutions.com.

;; Query time: 38 msec
;; SERVER: 24.117.5.71#53(24.117.5.71)
;; WHEN: Sat Mar 29 12:18:59 2008
;; MSG SIZE  rcvd: 74

```


reverse

```

dig -x 24.117.5.71

; <<>> DiG 9.4.1-P1 <<>> -x 24.117.5.71
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 4178
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;71.5.117.24.in-addr.arpa.      IN      PTR

;; Query time: 28 msec
;; SERVER: 24.117.5.71#53(24.117.5.71)
;; WHEN: Sat Mar 29 12:19:28 2008
;; MSG SIZE  rcvd: 42

```

I just now noticed while doing that command that I do not get an answer with dig -x, but I was last night, and citadel doesnt seem to have changed in the slightest.



Well that is pretty much all i can tell you about my server, if any of you have the time to help me out and read over this and try to see what is wrong, i would be extremely grateful. You can also pm me!
Thanks so much


::One little edit here, i just turned off SMTP SSL and it doesnt hang in SMTP que anymore, it sends me a delivery notification status which says relaying denied::

---

### Post by dantheman3212 on 2008-03-29
Also when i switch SMTP MSA port to 666 instead of 25 it says connection refused.

---

### Post by artcancro on 2008-03-29
Have you tried simply using authenticated SMTP?  That is the right way to submit mail into your system anyway.  Or is Citadel accepting the mail but is having trouble delivering it outbound?  In that case it is possible that your ISP is blocking outbound connections to port 25.

---

### Post by dantheman3212 on 2008-03-30
I've tried doing authenicated SMTP, and it returns "you must first log in to ptxsolutions.com to send mail". The user in citadel is an admin on my ubuntu machine running the server, so I don't know what to do next. Can I bypass the problem with Cable one blocking port 25 with using the SSL Port 465?

---

### Post by HermanAB on 2008-03-30
To run a mail server, you need a 'server' account with two or more static IP addresses.  This costs about $10 per month more than a regular home account.  Otherwise, fuhgeddaboudit...

Cheers,

Herman

---

### Post by dantheman3212 on 2008-03-30
Well I was thinking about upgrading to cable ones business account, guess I'll let you guys know if that works out.

---

### Post by Shadowfire on 2008-04-05
> **HermanAB said:**
> To run a mail server, you need a 'server' account with two or more static IP addresses.  This costs about $10 per month more than a regular home account.  Otherwise, fuhgeddaboudit...

Cheers,

Herman


As long as you have one static IP you can run a Website / Mail server / DNS and so on all day long.  As far as where your ISP lets you do it on a residential or business that is a different story.

I have a number of locations that run off one ip.  All of them are business though.

---

### Post by MJN on 2008-04-06
> **HermanAB said:**
> To run a mail server, you need a 'server' account with two or more static IP addresses.  This costs about $10 per month more than a regular home account.  Otherwise, fuhgeddaboudit...

Cheers,

Herman

I successfully run a mail server with a single dynamic IP, and without a 'server' account, and have done so for years without any problem.

Mathew

---

