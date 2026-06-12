---
title: "exim4 doesn't work :(((("
date: 2011-03-21
forum: Server Platforms
---

### Post by mxblast on 2011-03-21
Hi Guys,
I've tried everything I know possible to get exim4 to work, but no luck so far. Before exim4 I've tried postfix, but tht got me in more trouble, so I switched back to exim4, here's my logs, if u guys find anything that can fix the problem, pls lemme know. Thanks!

I'm simply using php mail() function to send an email to my gmail account to test, but no luck.

```

tail -f /var/log/exim4/mainlog

2011-03-21 07:42:14 Start queue run: pid=6549
2011-03-21 07:42:14 1Q1XGK-0001gY-4B gmail-smtp-in.l.google.com [74.125.39.27] No route to host
2011-03-21 07:42:17 1Q1XGK-0001gY-4B alt1.gmail-smtp-in.l.google.com [72.14.213.27] No route to host
2011-03-21 07:42:20 1Q1XGK-0001gY-4B alt2.gmail-smtp-in.l.google.com [74.125.65.27] No route to host
2011-03-21 07:42:23 1Q1XGK-0001gY-4B alt3.gmail-smtp-in.l.google.com [74.125.67.27] No route to host
2011-03-21 07:42:26 1Q1XGK-0001gY-4B alt4.gmail-smtp-in.l.google.com [74.125.115.27] No route to host
2011-03-21 07:42:26 1Q1XGK-0001gY-4B == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (113): No route to host
2011-03-21 07:42:26 1Q1WJJ-0006Qh-J3 == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (-53): retry time not reached for any host
2011-03-21 07:42:26 1Q1XDh-0001gT-40 == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (-53): retry time not reached for any host
2011-03-21 07:42:26 1Q1Wx6-0001ec-V5 == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (-53): retry time not reached for any host
2011-03-21 07:42:26 1Q1XdC-0001hB-Jd == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (-53): retry time not reached for any host
2011-03-21 07:42:26 1Q1Wip-0000bx-Os == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (-53): retry time not reached for any host
2011-03-21 07:42:26 1Q1WHJ-0006QL-DR == MY_EMAIL@gmail.com R=dnslookup T=remote_smtp defer (-53): retry time not reached for any host


```>> I've forwarded port 25, and as you can see it's listening to the port. 
exim4     6347 exim    3u  IPv4  12126      0t0  TCP 127.0.0.1:25 (LISTEN)
exim4     6347 exim    4u  IPv6  12127      0t0  TCP [::1]:25 (LISTEN)
exim4     6347 exim    5u  IPv4  12129      0t0  TCP 192.168.1.116:25 (LISTEN)

>> sudo dpkg-reconfigure exim4-config
configured exim4 as follows
```

#Mail Server configuration
internet site; mail is sent and received directly using SMTP

# Mail Server configuration
mydomain.com

# Mail Server configuration ...116 = server ip in LAN
127.0.0.1 ; ::1 ; 192.168.1.116 ;

# Mail Server configuration
mydomain.com

# Domains to relay mail for (left empty cuz I want to only send mails not receive!)

# Machines to relay mail for: (again the local IP of the server)
192.168.1.116/24 ;

# Keep number of DNS-queries minimal (Dial-on-Demand)? 
NO

# Delivery method for local mail: 
mbox format in /var/mail/ 

# Split configuration into small files?
YES

```

---

