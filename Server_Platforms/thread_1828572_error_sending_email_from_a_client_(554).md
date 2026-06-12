---
title: "error sending email from a client (554)"
date: 2011-08-19
forum: Server Platforms
---

### Post by BrandonSk on 2011-08-19
Hello all,
I am having trouble sending e-mails from roundcube as postfix rejects them. But let's take this step by step.
 
I have followed the flurdy's guide all the way to the ssl authentication.
 
**_General:_**
I have 2 .com domains (let's say mydomain1.com and mydomain2.com)
My server domain (would it be the FQDN?) is server.home -> this one obviously not available from internet, only locally.
 
I set-up all DNS records and MX records for the 'com' domains to point to my external IP (router - let's assume 1.2.3.4) which forwards required ports (25, 110, 143, 465, 587, 993 [also 80 and 443 but that is irrelevant]) to my server's LAN address 192.168.100.222
 
As far as I know, the server is not running any kind of FW (yet) - at least I did not set-up iptables or shorewall.
 
**_The goal:_**
I want my mail server to handle communication (send/receive) for both 'com' domains and the local domain.
(e.g. [EMAIL="outsideuser@domain1.com"]outsideuser@domain1.com[/EMAIL]; or [EMAIL="anotheruser@domain2.com"]anotheruser@domain2.com[/EMAIL]; and [EMAIL="localuser@server.home"]localuser@server.home[/EMAIL])
 
**_What works:_**
I followed the howto mentioned above and successfully tested after each major section. That means that if I telnet to my server from the terminal on port 25, I could send emails to my local accounts, to my 'com' domains as well as to external addresses like gmail.com. That means, I suppose, that postfix handles sending and delivery to mailboxes ok.
 
The same tests were passed when I was not doing it on the server itself (via putty), but telneting into it from terminal on my ubuntu laptop (e.g. lan computer 192.168.100.10 was telneting 192.168.100.222:25). Everything worked.
 
**_The catch:_**
Instead of squirrelmail I opted for the roundcube.
I followed the instructions and I am able to log-in to the Roundcube from my lan pc using server's lan ip as well as using one of the com domains (e.g. [http://domain1/roundcube](http://domain1/roundcube)).
 
I can login and see the mail of local users (e.g. postmaster@localhost) and I can also login as an outside user (e.g. [EMAIL="outsideuser@domain1.com"]outsideuser@domain1.com[/EMAIL]) and see the emails in their mailbox that I have sent during the test.
 
However, if I try to send any email (no matter which user to which destination) I receive a smtp error:
*SMTP Error (554): Failed to add recipient "whoever@wherever.com" (5.7.1 : Client host rejected: Access denied)*
 
Now, I think this is in fact postfix problem related to secure authentication (all the telnet tests did not deal with ssl). Any ideas what may be wrong?
 
Thanks in advance.
Brano.

---

### Post by SeijiSensei on 2011-08-19
Is the problem that you can't send mail to off-site domains?  First guess is that your ISP blocks outbound port 25 traffic to defeat spambots created by Windows viruses.

Try running "telnet gmail-smtp-in.l.google.com 25" from your server.  Does it connect or hang?  If the latter, you're probably blocked.

If you can't receive inbound mail, again it could be an ISP policy.  If you're on a residential connection, your Terms of Service may forbid running servers, and the ISP may have blocked inbound port 25 to enforce that rule.

---

