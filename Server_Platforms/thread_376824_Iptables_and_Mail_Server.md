---
title: "Iptables and Mail Server"
date: 2007-03-05
forum: Server Platforms
---

### Post by mikestefff on 2007-03-05
I am in the process of securing my VPS web/mail server. I am trying to get the IPtables to work with my mail server so i can send and receive mail properly. I am using Postfix and Squirrelmail as an IMAP client. Currently I have pop and imap enabled (secure and not) and smtp to send mail. Since I am not exactly sure how mail servers work, which ports do I need allow incoming traffic on in IPtables to receive and send mail. How should I set up the firewall?

(also- I am not sure if I should have port 53 open. I looked through the mail logs while I was trying different things and it seemed to have trouble looking up domain names)

Thanks

---

### Post by mikestefff on 2007-03-05
ALSO: does the use of IPtables slow down the services? My ssh takes like 10x as long to connect, websites are loading about 3x slower..

---

### Post by elst on 2007-03-05
Slow connections may be caused by DNS issues - you shouldn't see this loss of performance just by running iptables.

The file /etc/services on any *NIX system lists the IANA assigned port numbers for different services (it's very long, so use grep). Typically you only configure firewalls to restrict incoming connections, i.e. block all inbound traffic on all ports, apart from localhost, and those ports used by services that should accept external connections. If you are using SquirrelMail as the only IMAP client then you don't need to allow external connections to the IMAP service. You don't need to allow inbound connections to port 53 unless you actually operate a DNS server that maintains information for zones/domains.

If you are not sure how particular services operate then it's a good idea to set up a test virtual machine and experiment on that until you've got a working configuration, then copy the relevent config files across to the live server. It's much less stressful to rollback a test VM than recover from a firewall error on a remotely hosted server :).

---

### Post by mikestefff on 2007-03-05
Well then how does the machine receive email from other people?

And then why isn't the email working now after i set up iptables?

And one more question about IPTABLES: i set it to only allow from my IP for port 22 - that works fine for command line but when i use the file manager to connect through ssh to transfer files..it doesnt connect..any ideas?

---

### Post by gpredrag on 2007-03-05
Look at /etc/services for port numbers of well known services.

If you receive mail on that server (do you? or are you just using it for IMAP frontend) you should allow incoming SMTP (TCP 25)
You should allow incoming DNS only if you have DNS  server on that machine (you didn't mention).
If you are controlling outgoing traffic you should allow UDP 53, that is DNS queries from that computer to other DNS servers.

Have you looked at shorewall package? It has config files and macros to easily create firewalled machine, by listing services allowed in and out.

---

### Post by mikestefff on 2007-03-05
Mar  5 14:03:19 (SERVER_NAME) postfix/smtp[9902]: 780DC1ECFC0B8: to=<(EMAIL RCPT)>, relay=none, delay=12348, delays=12308/0.02/40/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=yahoo.com type=MX: Host not found, try again)

---

### Post by Mr. C. on 2007-03-05
Your mail server listens on port 25, the default port for inbound SMTP.  You need to open this port inbound, forwarded to your mail server's LAN address.

You may also decided to provide alternate submission ports, where external users can authenticate with your server to submit mail remotely.  Ask more when you get to this.

You send SMTP mail to other mail servers at their port 25; presumably your firewall allows all outgoing traffic, so this isn't a concern.

Squirrelmail and IMAP play no part in this, unless you are trying to use them remotely.

You do not need, nor likely want to, open the DNS port (53) for inbound connections unless you are going to provide name services to the world for your domain(s).  Setup bind on your own server simply for internal-use only.

If you are having trouble with name lookups, then your resolver or name server is incorrectly configured.  If you are running a DNS server, you need to setup /etc/resolv.conf to properly request name lookups from your DNS server.  Otherwise, you use your ISPs name servers.

This should get the ball rolling.
MrC

---

### Post by mikestefff on 2007-03-05
Well the vps came setup running port 53. I don't know if that means that I need it to accept incoming traffic or not. The mail still isnt working. I opened port 25 for incoming traffic with tcp and udp. There are no restrictions on outgoing traffic. I am still getting that log error of host not found..

What can be done?

And what about the ssh problem i mentioned before?

---

### Post by mikestefff on 2007-03-05
what about rndc on port 953 - that was opened by default too?

---

### Post by Mr. C. on 2007-03-05
> **mikestefff said:**
> ALSO: does the use of IPtables slow down the services? My ssh takes like 10x as long to connect, websites are loading about 3x slower..

Not significantly, unless you have many, many rules on a chain.

---

### Post by Mr. C. on 2007-03-05
> **gpredrag said:**
> You should allow incoming DNS only if you have DNS  server on that machine (you didn't mention).

This is a 1-way *if*, which I'm sure the poster knows, but for clarification to those unsure - you may run a DNS server on your LAN, and not open inbound 53.

---

### Post by mikestefff on 2007-03-05
lol no not that question - this one: i set it to only allow from my IP for port 22 - that works fine for command line but when i use the file manager to connect through ssh to transfer files..it doesnt connect..any ideas?

And the mail still doesnt work..same name lookup error..im going to kill myself

---

### Post by Mr. C. on 2007-03-05
> **mikestefff said:**
> Mar  5 14:03:19 (SERVER_NAME) postfix/smtp[9902]: 780DC1ECFC0B8: to=<(EMAIL RCPT)>, relay=none, delay=12348, delays=12308/0.02/40/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=yahoo.com type=MX: Host not found, try again)

Your DNS is not working.

---

### Post by Mr. C. on 2007-03-05
> **mikestefff said:**
> lol no not that question - this one: i set it to only allow from my IP for port 22 - that works fine for command line but when i use the file manager to connect through ssh to transfer files..it doesnt connect..any ideas?

And the mail still doesnt work..same name lookup error..im going to kill myself

Please ask new questions in new threads; this is more useful to others, and keeps thread length manageable.

---

### Post by Mr. C. on 2007-03-05
> **mikestefff said:**
> what about rndc on port 953 - that was opened by default too?

$ grep 953 /etc/services
$ man rndc

---

### Post by mikestefff on 2007-03-05
ok - still dont understand why this isnt work and what I can do to fix it. if  none of those services need incoming traffic then why would the enabling of iptables be interfering with my mail server?

edit: some mail has finally arrived on my server that i sent from yahoo about 7 hours ago - there never used to be a delay. a few messages go through to yahoo earilier too. its just erratic and slow now..i just dont get it...the mail hardly works, ssh lags like hell on login, ssh doesnt work now through the file manager, etc..

---

### Post by keithweddell on 2007-03-05
As others have said, your problems almost certainly relate to DNS.  You need to make sure that you have entered name servers correctly in /etc/resolv.conf and make sure that your firewall allows outgoing dns queries from your mail server.

Also does your firewall allow Established & Related incoming packets?


Keith

PS You could try using Firestarter or something similar to help configure iptables

---

### Post by mikestefff on 2007-03-05
nameservers are correct in /etc/resolv.conf and have never been a problem till i started with iptables. outgoing traffic has not been blocked at all. And i havent done anythign to affect established/related incoming packets.

i will look into firestarter

---

### Post by Mr. C. on 2007-03-05
Show your resolv.conf.

Having incorrect nameservers, in suboptimal ordering of multiple nameservers *will* cause excessive delays per DNS lookup, as the resolver must wait for a DNS timeout to occur (15 seconds / query).

Show your logs regarding the transactions sending to Yahoo; this will yield some clues.

Grab my postfix logwatch filter/reporter and run it against your postfix maillogs.  If you don't have logwatch already installed, see the README in the filter package:

[http://www.mikecappella.com/logwatch/postfix.tgz](http://www.mikecappella.com/logwatch/postfix.tgz)

Once you have your report at detail level 10, PM me a copy (it will be long), and I'll help you understand what's happening.

MrC

---

### Post by mikestefff on 2007-03-06
OK i finally figured it out..

I needed to add both of my name servers from /etc/resolv.conf to be allowed in the iptables..

and i needed both tcp/udp source/dest open for port 25

is there a security issue with having smtp open like that? how can i prevent people from using it for spam??

edit: i forgot the port is filtered - it doesn't show when the machine is scanned with nmap. i believe i set that up when i configured postfix..anything else i can do?

---

### Post by Mr. C. on 2007-03-06
Nice work!

UDP won't be used on port 25.  SMTP is a TCP connection.

Postfix is very secure, and was written with security as a primary goal.  As long as you have it configured correctly, you needn't worry.

Your SMTP server by default accepts email only destined for *your* places you list as domain, and will not allow others to use it to relay email elsewhere.  Be sure to understand any changes to the configuration (postfix's main.cf, master.cf).

Your SMTP server will allow you to send to all domains (provided they don't block you for any of a variety of reasons).

You will receive loads of spam addressed to your domain, and backscatter addressed to your domain, if you do not do recipient validation.  This is enabled by default.  If you enable wildcarding (eg: [email]anything@mydomain.com[/email]), you will receive loads of spam (a quick analysis of my home server logs shows 150,000 spam/backscatter attempts in the last few months).

MrC

---

### Post by mikestefff on 2007-03-06
MrC your a great person - thanks yet again for your help

One last thing before we end this thread - should I configure iptables for outgoing traffic? Does it really matter? 

THANKS

---

### Post by Mr. C. on 2007-03-06
Very kind, thanks.

I wouldn't worry about blocking outbound traffic.  If you had a bunch of rogues on your LAN, then you can start thinking about it.  The default state for most all stateful firewalls is:

   1) All outbound OK
   2) Inbound already established connections OK
   3) All inbound blocked

Outbound blocking is typically done in institutions, businesses, government, etc. where access is strictly controlled both in and out.

Enjoy that server!
MrC

---

