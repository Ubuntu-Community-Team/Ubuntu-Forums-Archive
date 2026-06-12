---
title: "postfix, dedicated www to dedicated smtp config request."
date: 2012-10-26
forum: Server Platforms
---

### Post by Ron Jones on 2012-10-26
I have a dedicated web server on the local network (tigger.mydomain.com) and a dedicated email server (pooh.mydomain.com).

The mail server works fine (thanks to [ExRatione]("http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/"), and [Flurdy]("http://flurdy.com/docs/postfix/index.html")). 

However, I want the web server to be able to send its logwatch files to my address on the mail server.

I also want the Drupal installation to be able to send out the occasional email ("you lost your password? click this link to reset it" etc).

Per the "[Postfix on a null client"]("http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client") configuration setup (the web server should never receive mail, only send it), this is my /etc/postfix/main.cf file:
> 
myhostname = tigger.mydomain.com*
myorigin = mydomain.com
#mydestination = 
relayhost = mail.mydomain.com
#mynetworks = 127.0.0.0/8 192.168.49.0/30** [::1]/128 [fe80::%eth0]/64
#mailbox_size_limit = 51200000
#recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = ipv4
* the domain in question has a real, authoritative DNS entry with securityspace.com. 
** the dedicated web server is hanging off a pfSense firewall, on its own DMZ (as is the mail server), and I've configured (and tested) the rules to allow ports 25, 53, 465, 587 to pass from the web server to the mail server (until I get this thing ironed out, and get the configuration right).

Unfortunately, I keep getting denied :confused:
When I attempted a telnet mail.mydomain.com 587, I got this from the syslog of the mail server:
> 
Oct 26 11:13:38 pooh postfix/submission/smtpd[6043]: NOQUEUE: reject: RCPT from tigger.mydomain.com[192.168.49.2]: 554 5.7.1 <tigger.jonesfamily.us[192.168.49.2]>: Client host rejected: Access denied; from=<admin@mydomain.com> to=<ron@mydomain.com> proto=ESMTP helo=<mail.mydomain.com>
And the feedback from the telnet screen said 
> 
554 5.7.1 <tigger.mydomain.com[192.168.49.2]>: Client host rejected: Access denied
Which would seem to indicate a problem with the mail server's main.cf file.
HOWEVER...
the first entry after smtpd_client_restrictions, smtpd_helo_restrictions, smtpd_sender_restrictions, and smtpd_recipient_restrications, is "permit_mynetworks" Which is identified as 
mynetworks = 192.168.29.0/24 192.168.39.0/30 192.68.49.0/30 127.0.0.0/8
(where 192.168.39.0/30 and 192.168.49.0/30 are the mail and web DMZ's respectively).

As if that weren't enough to stump me... when I telnet to mail.mydomain.com 25 it works just fine. (but when I change the relayhost variable in /etc/postfix/main.cf to [mail.mydomain.com]:25 and try to run the command "logwatch," I get nothin... not even a blip in the syslog tail.

Can someone point me to something that documents a simple solution..."Romper Room style"...?

---

