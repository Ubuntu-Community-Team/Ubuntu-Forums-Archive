---
title: "Mail server says &quot;no route to host&quot; when sending mail outside of server"
date: 2012-05-23
forum: Server Platforms
---

### Post by KMatsumari on 2012-05-23
here's the deal, I just got EVERYTHING to work exactly as planned according to the recently released "perfect ubuntu server 12.04 LTS (Apache2, BIND, Dovecot, ISPConfig 3)", and I took a few hours waiting for my DNS A name and MX records to recirculate. After sending an email to my new email address, I was sure I was finally done and could rest. Too bad I am thorough in my testing... I replied to the message only to find that my mail server doesn't want to send email back to my yahoo account... go figure.

Logged into squirrelmail from internet, not LAN, using IMAP login: succeeded.
Sent email from one squirrelmail account to another on said IMAP login (my friend in another state was logged in to the other squirrelmail account and we were testing via skype): succeeded.
Sent emails from both squirrelmail accounts to one another a few times: succeeded.
Sent emails from both squirrelmail accounts to outside email address we own: failed.

my mail queue says this:

```

7BF364E003B9 1411 Wed May 23 02:32:30 user1@example.com
(connect to alt4.gmail-smtp-in.l.google.com[173.194.65.27]:25: No route to host)
anonymous@gmail.com

0AB4F4E012EE 1236 Wed May 23 02:20:50 user1@example.com
(delivery temporarily suspended: connect to mta5.am0.yahoodns.net[66.94.237.64]:25: No route to host)
anonymous@yahoo.com

9035F4E0131A 1231 Wed May 23 02:22:06 user1@example.com
(connect to alt4.gmail-smtp-in.l.google.com[74.125.131.27]:25: No route to host)
anonymous@gmail.com

D5F774E012BA 1348 Tue May 22 23:53:57 user1@example.com
(connect to mta7.am0.yahoodns.net[72.30.235.6]:25: No route to host)
anonymous@yahoo.com

DD5C24E013BC 1544 Wed May 23 02:45:17 user1@example.com
(connect to mta6.am0.yahoodns.net[72.30.235.196]:25: No route to host)
anonymous@yahoo.com

1775E4E012A7 1398 Wed May 23 02:14:09 user1@example.com
(connect to mta5.am0.yahoodns.net[98.139.54.60]:25: No route to host)
anonymous@yahoo.com

1C9A64E013D0 1315 Wed May 23 01:04:14 user1@example.com
(connect to mta6.am0.yahoodns.net[66.94.236.34]:25: No route to host)
anonymous@yahoo.com

EB6294E013D7 1307 Wed May 23 01:08:23 user2@example.com
(connect to alt4.gmail-smtp-in.l.google.com[74.125.131.27]:25: No route to host)
anonymous2@gmail.com

CDC0A4E013DC 1558 Wed May 23 02:34:35 user1@example.com
(connect to mta5.am0.yahoodns.net[66.94.237.64]:25: No route to host)
anonymous@yahoo.com

```

As far as I can tell, my server is acting like it can't establish a connection to the other SMTP servers as if it has no actual access to the internet, but that is definitely not the case as they are steadily and in less than a minute receiving messages from these accounts.

user1 = my squirrelmail account
user2 = my freind's squirrelmail account
anonymous = my personal yahoo or gmail account
anonymous2 = my friend's personal gmail account

I did start a few other threads and help questions over the past few months about these sorts of things, but I am much closer than I was before. I am almost done working out these bugs myself, having just redone the installations and package configurations over again and again... and again.

I can finally start passing out my business cards now that I can at least get email from prospective clients, but it would benefit me greatly if I could also reply to them as well and email them billing statements and reply to support tickets in my business.

I need to send mail with these email address ASAP, and I will be setting up another server like this one, and I need to know what went wrong or what I omitted so I can be sure to correct it in the future.

Aside from server output from commands, the only other thing I can submit right now is my mail log found in ISP Config. And don't be like one of the other guys from before and troll on me because I use ISP Config; it works great for me, and I know how to use it properly.

I can really use this last bit of help, and whoever can help me out here will have my undying gratitude... and a bounty if you wish (last time everyone said forget the bounty, so I leave it to be optional).

---

### Post by KMatsumari on 2012-05-23
I could really use some help here as I cannot get my SSL certificates issued to me because my issuer wants me to reply with my email account that only the domain owner controls (me). I can't send any emails. I was looking around a bit about different ports for smtp, and when I was looking at my postfix master.cf, i noticed something and I thought I'd ask if this could have anything to do with it:

This is what every post and guide I have seen says the line should be for postfix master.cf
```
smtp      inet  n       -       n       -       -       smtpd
```
Here is what I have
```
smtp      inet  n       -       -       -       -       smtpd
```
does the fact that I am chrooting my smtp have anything to do with why I am receiving emails from everywhere, but cannot send them outside of the server?

PLEASE HELP! I am getting desperate. I am certain it isn't a blacklisting problem since I would have a "rejected" error in my logs instead of "no route." Last time I was experiencing no mail in either direction, which lead me to call my ISP and ask them to open my then blocked port 25. Since after having that port unblocked, I installed my current setup and found that I can receive mail. I am going to call them again and see if they are blocking outbound traffic from port 25 (worth a shot to see if they are screwing with my stuff). I will reply to this post with my findings.

---

### Post by hawkmage on 2012-05-23
Run the following commands and post the output:
```
ifconfig
netstat -rn
```

---

### Post by KMatsumari on 2012-05-23
just got off the phone with my ISP, and they are not blocking port 25 in either direction, and their mail logs do not show anything from my domain name outbound, so the problem lies in my server somewhere. Is it possible that my router or my server firewall may be blocking outbound traffic anywhere, and if so how can I check the firewall for such a deny outbound traffic rule (I'm going to check my router when I get home since I am SSHing to it from elsewhere)?

I need help and fast. I am offering a $50 bounty to whoever fixes my issue soon and wants to get paid for it.

---

### Post by KMatsumari on 2012-05-23
```
eth0      Link encap:Ethernet  HWaddr 50:e5:49:6c:ed:5d
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe6c:ed5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:324414417 (324.4 MB)  TX bytes:12168475 (12.1 MB)
          Interrupt:40

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2676227 (2.6 MB)  TX bytes:2676227 (2.6 MB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

```

keep in mind that everything else is working, including my access from an outside source and I am receiving emails from outside sources as well.

---

### Post by SeijiSensei on 2012-05-23
Try "telnet mail.server 25" using the server names that you can't reach like, e.g., "telnet mta5.am0.yahoodns.net 25"?  Do they time out?  Can you ping those machines but not connect to port 25 on them?

If you can't ping them, try installing traceroute ("sudo apt-get install traceroute") and use that instead of ping to see the intermediate hops.  Can you identify the place where connectivity stops?

---

### Post by KMatsumari on 2012-05-23
```
root@main:/home/kurono# telnet mta5.am0.yahoodns.net 25
Trying 72.30.235.196...
Trying 98.137.54.238...
Trying 98.139.175.224...
Trying 209.191.88.254...
Trying 66.94.237.64...
Trying 66.94.237.139...
Trying 67.195.103.233...
Trying 72.30.235.6...
telnet: Unable to connect to remote host: No route to host

```

basic ping to mta5.am0.yahoodns.net was successful using this:

```
ping mta5.am0.yahoodns.net
```

traceroute:

```
traceroute to mta5.am0.yahoodns.net (98.137.54.238), 30 hops max, 60 byte packet                                                                                        s
 1  192.168.0.1 (192.168.0.1)  0.948 ms  1.424 ms  1.974 ms
 2  tukw-dsl-gw64-129.tukw.qwest.net (63.231.10.129)  41.472 ms  43.439 ms  44.8                                                                                        99 ms
 3  tukw-agw1.inet.qwest.net (71.217.185.249)  46.617 ms  47.788 ms  49.005 ms
 4  sea-brdr-02.inet.qwest.net (67.14.41.18)  51.196 ms  52.405 ms  53.665 ms
 5  te8-3-10G.ar5.SEA1.gblx.net (64.208.110.141)  55.689 ms  56.795 ms  58.246 m                                                                                        s
 6  e5-3-40G.ar5.SJC2.gblx.net (67.17.72.14)  89.268 ms  65.199 ms  68.091 ms
 7  YAHOO-SAN-JOSE.TenGig2-3.1189.ar3.SJC2.gblx.net (64.211.206.210)  62.098 ms                                                                                         YAHOO.TenGigabitEthernet2-4.1189.ar3.SJC2.gblx.net (208.48.239.254)  64.764 ms Y                                                                                        AHOO-SAN-JOSE.TenGig2-3.1189.ar3.SJC2.gblx.net (64.211.206.210)  67.349 ms
 8  ae-0-d160.msr1.sp1.yahoo.com (216.115.107.57)  68.917 ms  70.587 ms ae-1-d16                                                                                        1.msr1.sp1.yahoo.com (216.115.107.63)  71.603 ms
 9  et-17-25.fab2-1-gdc.sp2.yahoo.com (98.136.16.23)  73.014 ms et-17-1.fab3-1-g                                                                                        dc.sp2.yahoo.com (67.195.128.73)  74.479 ms et-18-1.fab2-1-gdc.sp2.yahoo.com (98                                                                                        .136.16.21)  75.429 ms
10  te-9-1.bas2-1-prd.sp2.yahoo.com (67.195.130.108)  77.133 ms te-9-3.bas2-1-pr                                                                                        d.sp2.yahoo.com (67.195.130.110)  79.192 ms te-9-1.bas2-1-prd.sp2.yahoo.com (67.                                                                                        195.130.108)  79.688 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

I follow some of this, but I am sick and am getting tired, so I am going to pick up on this a bit slower than usual. what do you see?

---

### Post by hawkmage on 2012-05-23
This is odd.  From that trace route the issue is not on your network.  It is getting 9 devices past your router.  It is getting 3 hops into the Yahoo network and then fails.  

I can't traceroute to mta5.am0.yahoodns.net either.  Where did you get the Yahoo smtp server that you are trying to use?  Could it have been  decommissioned?

---

### Post by SeijiSensei on 2012-05-23
> **hawkmage said:**
> I can't traceroute to mta5.am0.yahoodns.net either.  Where did you get the Yahoo smtp server that you are trying to use?  Could it have been  decommissioned?

I just picked one from the errors he reported earlier.  There's also alt4.gmail-smtp-in.l.google.com.  I can telnet to its port 25 just fine.

As for the traceroute, it's likely the other machines just don't accept ICMP traffic.

---

### Post by hawkmage on 2012-05-23
True, I keep forgetting that ICMP is filtered in may networks. However it is still not likely an issue with the local network.  The SMPT hosts are being resolved to an address, and the trace route  shows that routing is getting packets outside the local router.  

Getting a "no route to host" when you your local routing is working will often be caused by a iptables reject with one of the type icmp-net-unreachable or icmp-host-unreachable.  This can be on the host its self or somewhere upstream

---

### Post by KMatsumari on 2012-05-24
Could this have anything to do with my site not having a verified ssl cert? I didn,t even self-sign one before hand, and I don't think I am forcing secure transmissions on smtp. My guess is if it were a a denial based on lack of secure connection my mail log would have a rejection instead of no route to host.

Its like the problem seems to be on their ends, but they can still receive mail from other sources, only my server cannot send mail to anywhere except locally.

What can I do to see how far my messages actually make it and if a connection outside is even being established beyond my router, modem, or isp? What is the most simple answer to "why is there seemingly no route to host only when connecting with smtp?" (Simplest answer tends to be the right answer). It has to be my server otherwise no mail would get through at all, or their email lookups and headers are dead ends through and through.

I would like to test my email account with somebody with a "send copy" enabled i my ispconfig. I also just had an epiphany: maybe I need to make my clients forward the email through ispconfig to get sent onward. I will look into this tomorrow afternoon. I think I may have just figured it out. Its because ispconfig runs the server components and sublets the space to the customers (ispconfig calls them clients and resellers), which is why I have an index page for my host.domain.com and another for my [www.domain](www.domain)

---

### Post by KMatsumari on 2012-05-24
Nope, my idea did not hold water. Turns out that all messages are automatically handled by the server in which the vmail group and user is found (ispconfig). By all means, dovecot should be establishing a connection to the other smtp servers (it is accepting their connections when receiving their email transports), but it would seem that dovecot thinks it cannot find a way to get there...

I can telnet, ping, and receive mail from their smtp servers, so their servers are up and running, and mine is able to establish contact in general and answer their requests. There IS a route to the host in general. Dovecot SMTP says no route to host, so the ports which dovecot is trying to connect on aren't correct or are being blocked somewhere. They shouldn't be blocked by the destinations, as that would have "err:request rejected" or "connection refused", I get this when I try to ssh or vnc to my server with the wrong port number. I don't know if there would be a difference in the error message if my firewall, router, modem, or ISP is blocking outbound traffic on my smtp ports. My ISP says that port 25 is the ONLY port they initially block incoming connections to, but I had them unblock it a while back, and they say it is open both ways and I should not need to use a mail relayhost transport, smarthost, satellite relayhost, or anything of that nature; I should be able to use my own mail server to handle my mail delivery on the internet.

I will check through my firewall, but I am going to say that ISPConfig should have configured it properly when I installed it. Other than that, I can only think of what could have been forced into local-delivery-only mode if some things were specified as localhost, localhost.localdomain, or simply local (squirrelmail config has my IMAP and SMTP server set to localhost.localdomain)

---

### Post by KMatsumari on 2012-05-24
```

root@main:# iptables -L
ChainINPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-dovecot-pop3imap  tcp  --  anywhere             anywhere             multiport dports pop3,pop3s,imap2,imaps
fail2ban-pureftpd  tcp  --  anywhere             anywhere             multiport dports ftp
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-dovecot-pop3imap (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

Chain fail2ban-pureftpd (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

```

This is my output of my iptables. is any of this wrong or should any of this be different?

---

### Post by KMatsumari on 2012-05-24
Found the issue. I spoke with my ISP supervisor, and it turns out that a bunch of idiots were talking to me previously. They were blocking my output on port 25, and they have now unblocked it completely. I just got all of my test emails from my mail server, and my problems are now solved. I thank you guys for being especially helpful, because without your efforts to help me troubleshoot, I would not have kept suspecting my ISP as the problem.

So, for anyone who sets up their mailserver to exact specifications from those guides, and runs into problems, be sure to call your isp and tell them to unblock your problem ports in BOTH directions.

---

