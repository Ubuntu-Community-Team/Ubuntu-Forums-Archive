---
title: "Help setting up mail server"
date: 2013-08-25
forum: Server Platforms
---

### Post by bellygrevios on 2013-08-25
Hi everyone,
I'm trying to set up my own personal mail server using this tutorial: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) 
I can log into my imap account but can't send or receive messages (using both the squirrelmail gui and a telnet sessino).
Here's my tel net session
[HTML]telnet localhost smtpTrying 127.0.0.1...Connected to localhost.Escape character is '^]'.220 mydomain.com ESMTP Postfix (Ubuntu)from502 5.5.2 Error: command not recognizedhelo mydomain.com250 mydomain.commail from: me@mydomain.com250 2.1.0 OkRCPT TO: mygmailaccount@gmail.com250 2.1.5 Okdata354 End data with <CR><LF>.<CR><LF>SUBJECT: HELLO EMAILThis is a test email.250 2.0.0 Ok: queued as 472AB10119B
500 5.5.2 Error: bad syntaxquit221 2.0.0 ByeConnection closed by foreign host.[/HTML]
When i check my gmail I haven't received any new emails and when I try sending an email to myself I still don't receive anything. Any clues?

Thanks in advance

---

### Post by TheFu on 2013-08-25
It is hard to setup a "personal mail server" these days on most home internet connections.  ISPs block outbound port 25 connections to other servers - they are reducing the spam by doing this.  I explained all this in another thread here the last few days - search.

First, please explain your connection to the internet. 
Who is your ISP, which mail server gateway do they use? Is it mandatory?
Do you own "mydomain.com" - if not, that is NOT the FQDN you want to use on any internet connected machine.
Did you setup DNS MX records so that anyone in the world can find you?

Setting up postfix is just 1 part of setting up an email server.

---

### Post by bellygrevios on 2013-08-25
> **TheFu said:**
> It is hard to setup a "personal mail server" these days on most home internet connections.  ISPs block outbound port 25 connections to other servers - they are reducing the spam by doing this.  I explained all this in another thread here the last few days - search.

First, please explain your connection to the internet. 
Who is your ISP, which mail server gateway do they use? Is it mandatory?
Do you own "mydomain.com" - if not, that is NOT the FQDN you want to use on any internet connected machine.
Did you setup DNS MX records so that anyone in the world can find you?

Setting up postfix is just 1 part of setting up an email server.

Hi, I'm extremely new to so bare with me.
*I'm connected to the internet through a router. I'm forwarding port 25 and 143 for SMTP and IMAP to my server.
*I'm using AT&T and I don't know how to check what mail server gateway they're using.
*I own mydomain.com (actually it's a .ml address)
*I'm not sure how to setup the DNS MX records.

---

### Post by sandyd on 2013-08-25
> **bellygrevios said:**
> Hi, I'm extremely new to so bare with me.
*I'm connected to the internet through a router. I'm forwarding port 25 and 143 for SMTP and IMAP to my server.
*I'm using AT&T and I don't know how to check what mail server gateway they're using.
*I own mydomain.com (actually it's a .ml address)
*I'm not sure how to setup the DNS MX records.
Read thread to check if you need to insert firewall rule to unblock incoming port 25
[https://forums.att.com/t5/Features-and-How-To/Port-25-Charges-49-or-15-or-Free/td-p/3154605](https://forums.att.com/t5/Features-and-How-To/Port-25-Charges-49-or-15-or-Free/td-p/3154605)

---

### Post by TheFu on 2013-08-25
> **bellygrevios said:**
> Hi, I'm extremely new to so bare with me.
*I'm connected to the internet through a router. I'm forwarding port 25 and 143 for SMTP and IMAP to my server.
*I'm using AT&T and I don't know how to check what mail server gateway they're using.
*I own mydomain.com (actually it's a .ml address)
*I'm not sure how to setup the DNS MX records.

I'm fairly certain that AT&T blocks inbound and outbound SMTP on port 25 - you'll need to use their SMTP-gateway unless you are on a business connection.

IMAP rocks, but IMAPS on 993 would be more secure. I don't think 993 is blocked by any ISP ... except hotels.

So, if you have a domain, then you've setup a DNS already "somewhere."  In that same system (I hope it is external to your home network) used to setup DNS, you'll create an MX record. Follow their instructions.  There is NO WAY TO DIRECT inbound EMAIL for any domain on the internet without an MX DNS record.

If your ISP blocks port 25 (likely), you'll need to pay an external provider or setup an email forwarding server on a VPS somewhere else to forward or hold email until your home box grabs it.  I run an email gateway for different reasons, but this would also be valid. 

Use telnet to check whether any ports are blocked inbound or outbound.

---

### Post by ZippyUbu on 2013-08-25
> Hi, I'm extremely new to so bare with me.
*I'm connected to the internet through a router. I'm forwarding port 25 and 143 for SMTP and IMAP to my server.
*I'm using AT&T and I don't know how to check what mail server gateway they're using.
*I own mydomain.com (actually it's a .ml address)
*I'm not sure how to setup the DNS MX records.

Hi - Some information to help you accomplish your goal. Not a complete list but some that you should check and sort prior to sending mail. Mail servers are configured to check DNS prior to accepting mail. There are lots of different kinds of DNS records but the most common records for a mail server are: MX Records - Reverse DNS records - and SPF Records. Each have a very unique task for a mail server.

 - The first record (MX Record) or known as a Mail Exchanger record: This is responsible for accepting email messages on behalf of a recipient's domain (your domain) There are certain values that you use to set-up your MX record - These values tell mail servers how to prioritise mail if several are available. You most likely will only have one MX record for your mail server. To confgure you MX record - Log into your domain providers website and choose to configure DNS records. This is sometimes the same place where you purchased your domain name.

- The second record (Reverse DNS records) Reverse DNS is IP address to domain name mapping - the opposite of forward (normal) DNS which maps domain names to IP addresses. Mail servers check reverse DNS to ensure the mail server has been configured correctly. If this check fails mail is usually dropped and won't be delivered. (Depending on how the recipients mail server or mail filter is configured) Your ISP will need to configure this for you - Most will do this through their support desk.

- The third record (TXT Record - SPF) This is not required for what you want to do. But a great option to protect mail spoofing - an additional piece - If your interested you can read about it [here]("http://en.wikipedia.org/wiki/Sender_Policy_Framework")

So, these are some of the settings that you would need to implement prior to sending email onto the internet - The above options assume that you have a static IP address and not a dynamic IP address where your mail server lives. Of course you will need the applicable firewall ports open as you previously stated.


--
Zu

---

### Post by bellygrevios on 2013-08-26
Thanks for all your help guys but it seems like at&t blocks all outbound SMTP so until I decide whether or not I want to pay extra for a simple service that should be free there's no point in figuring out anything else.

---

### Post by TheFu on 2013-08-26
> **bellygrevios said:**
> Thanks for all your help guys but it seems like at&t blocks all outbound SMTP so until I decide whether or not I want to pay extra for a simple service that should be free there's no point in figuring out anything else.

Yes, they block direct outbound SMTP connections - that is to prevent spammers from living on AT&T residential networks and having the rest of the internet block all email initiated by AT&T.  Most residential networks are also DHCP, so email servers will block connections from any DHCP address - I do.  OTOH, AT&T **does** have outbound email gateways. You just need to look for the settings and put those into your email server - there are how-tos.

Inbound email will be harder, since AT&T blocks port 25 inbound connections too AND you are on a DHCP address that changes a few times every week.  I was on DHCP with a different provider for 10 yrs - my IP changed 4 times in 10 yrs. I was able to run email all that time, though a few places would reject my connection just for being on DHCP.  Inbound email relay services exist for about $20/yr.  As someone new to running email, getting that working is non-trivial, and understanding that the services are sold separately - inbound is completely different from outbound, so if you can't get AT&T to relay email from your domain, then you'll need an outbound service too.  DynDNS sells these and I've used the inbound for a year ... before switching my connection to a commercial broadband connection - then you get a static (or 5 or 15) IP and ZERO ports are blocked.

For most people the best answer is to get a tiny VPS somewhere - Amazon "tiny" VMs can be had for free the first 12 months which will work great for pure email send/receive.  Then setup a mail server at your home and poll your amazon instance to grab all email local and you can set outbound through it, just not on port 25 ... 465 is the standard for this and you can force TLS encryption in both directions since you run both boxes. 

Getting your email off some 3rd party box is always a good idea, if you ask me. Knowing they didn't make a backup and aren't using it for any undesirable reasons gives me a smile.  It sorta pisses me off when people use gmail, yahoo, msn, outlook .... any of the huge email providers. I have to give up my privacy just to communicate with them? Seriously?  MOre and more, I'm saying no.

Anyway, just wanted to provide some options.

---

