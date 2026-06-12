---
title: "AntiSpam &amp; AntiVirus Gateway Server"
date: 2007-11-27
forum: Server Platforms
---

### Post by markerman on 2007-11-27
Hello all,
    I am new to Ubuntu but an experienced Microsoft Systems Engineer. I am trying to setup an Ubuntu LAMPS 6.10 server as an AntiSpam/AntiVirus email gateway server. Mailboxes are hosted on an Exchange 2003 server. The Exchange server is also an Active Directory Domain Controller, DNS/DHCP server. This server is running Intelligent Message Filter (AntiSpam) and Trend Scanmail (AntiVirus). Current production mailflow below...

(inbound)
Firewall---smtp-->exchange
(outbound)
Firewall<---smtp---Exchange

What I would like is...

(Inbound)
Firewall--smtp-->emailgateway---smtp--->exchange

(outbound)
Firewall<---smtp---emailgateway<----smtp---exchange

where 1st level of antispam/antivirus processing of inbound messages is handled on the emailgateway then is forwarded to the exchange server for additional antispam/antiviru processing with IMF & Scanmail. 


I have the ubuntu lamps server setup, spammassassin & postfix installed. I can telnet into postfix port 25 and sucessfully send email outbound to my external account. But sending email to my mailbox hosted on my exchange server results in the following bounceback..
***************************************************
This is the mail system at host mail.mydomain.net.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<james@mydomain.net>: Host or domain name not found. Name service error
    for name=mydomain.net type=A: Host found but no data record of
    requested type
******************************************************
I have an internal MX record setup pointing to mail.mydomain.net which is my exchange server. (of course I substituted "Mydomain" for my real domain name). I can ping mail.mydomain.net from the ubuntu server. 

My main.cf file non default settings...(again "Mydomain replaces my real domain name) 

2bounce_notice_recipient  [email]james@mydomain.net[/email]  
alias_maps  hash:/etc/aliases  
append_dot_mydomain  no  
biff  no  
bounce_notice_recipient  [email]james@mydomain.net[/email]  
delay_notice_recipient  [email]james@mydomain.net[/email]  
disable_vrfy_command  yes  
error_notice_recipient  [email]james@mydomain.net[/email]  
mailbox_command  procmail -a "$EXTENSION"  
mailbox_size_limit  0  
mydestination  mydomain.net , ubuntulamps.mydomain.loc , localhost.mydomain.loc , localhost  
mydomain  mydomain.net  
myhostname  mail.mydomain.net  
mynetworks  192.168.1.0/24 , 172.0.0.0/8  
myorigin  $mydomain  
recipient_delimiter  +  
smtp_tls_session_cache_database  btree:${queue_directory}/smtp_scache  
smtpd_recipient_limit  10  
smtpd_tls_cert_file  /etc/ssl/certs/ssl-cert-snakeoil.pem  
smtpd_tls_key_file  /etc/ssl/private/ssl-cert-snakeoil.key  
smtpd_tls_session_cache_database  btree:${queue_directory}/smtpd_scache  
smtpd_use_tls  yes  


any suggestions?

---

### Post by MJN on 2007-11-27
Given you've obfuscated your domain names (is it not theraaymakers.net?) this could be tricky, particularly given we're looking at what is likely a naming issue.
 
No matter, let's crack on regardless...
 
Your Postfix machine, called mail.mydomain.net is configured to be the final destination for mydomain.net hence when you use it to send a message to [EMAIL="james@mydomain.net"]james@mydomain.net[/EMAIL] how is the message even reaching the Exchange server?
 
Post your config as-is - hiding the domain name makes it a million times harder to debug.
 
Mathew

---

### Post by markerman on 2007-11-27
2bounce_notice_recipient  [email]james@theraaymakers.net[/email]  
alias_maps  hash:/etc/aliases  
append_dot_mydomain  no  
biff  no  
bounce_notice_recipient  [email]james@theraaymakers.net[/email]  
delay_notice_recipient  [email]james@theraaymakers.net[/email]  
disable_vrfy_command  yes  
error_notice_recipient  [email]james@theraaymakers.net[/email]  
mailbox_command  procmail -a "$EXTENSION"  
mailbox_size_limit  0  
mydestination  theraaymakers.net , ubuntulamps.theraaymakers.loc , localhost.theraaymakers.loc , localhost  
mydomain  theraaymakers.net  
myhostname  mail.theraaymakers.net  
mynetworks  192.168.1.0/24 , 172.0.0.0/8  
myorigin  $mydomain  
recipient_delimiter  +  
smtp_tls_session_cache_database  btree:${queue_directory}/smtp_scache  
smtpd_recipient_limit  10  
smtpd_tls_cert_file  /etc/ssl/certs/ssl-cert-snakeoil.pem  
smtpd_tls_key_file  /etc/ssl/private/ssl-cert-snakeoil.key  
smtpd_tls_session_cache_database  btree:${queue_directory}/smtpd_scache  
smtpd_use_tls  yes

---

### Post by markerman on 2007-11-27
This is being installed an active directory environment which requires a correctly configured dns.

---

### Post by MJN on 2007-11-27
Thanks. What are your machines called? Post your DNS config too if has a different internal view than the Internet perspective.
 
Can your Postfix machine perform a successfull DNS lookup for the MX record for theraaymakers.net? (the error suggests not so post the dig output, preferably with +trace)
 
Mathew

---

### Post by markerman on 2007-11-27
It's ms active directory integrated DNS. Domains are called zones. The Active Directory integrated zone is theraaymakers.loc. The public zone is theraaymakers.net.

I have host alias names for the servers configured in the public dns zone.

ubuntulamps server = outbound.theraaymakers.net & inbound.theraaymakers.net. The exchange server is mail.theraaymakers.net network config in the ubuntu lamps server has dns pointed to my ms dns server.

---

### Post by MJN on 2007-11-27
You've told Postfix that *it* is mail.theraaymakers.net - howcome?
 
I added a bit to my post about checking the DNS from the perspective of the Postfix server, e.g. **dig theraaymakers.net. MX +trace** - can you post the output? The reason I ask is that the Postfix error is suggesting a DNS failure - it mentions an A record lookup however that is likely because the MX lookup is first failing.
 
Mathew

---

### Post by MJN on 2007-11-27
Incidentally, I note you haven't got any relay_ directives hence you haven't actually told Postfix to relay mail to your Exchange server. Hence, as far as Postfix is concerned it is the final destination for theraaymakers.net.
 
Or am I missing something?
 
Mathew

---

### Post by markerman on 2007-11-27
I was using webmin to configure postfix. I did not see a configuration for relay_directives. Guess the webmin console is limited in that respect. What should I put into the main.cf? Also I realized that since my internal MX record points mail.theraaymakers.net which is my exchange server, and I had my postfix configured "myhostname mail.theraaymakers.net" which is wrong. I reconfigured it to "myhostname inbound.theraaymakers.net". Tested but got this new new error....

220 inbound.theraaymakers.net ESMTP Postfix
helo mango.saccounty.net
250 inbound.theraaymakers.net
mail from: [email]raaymakersj@saccounty.net[/email]
250 2.1.0 Ok
rcpt to: [email]james@theraaymakers.net[/email]
550 5.1.1 <james@theraaymakers.net>: Recipient address rejected: User unknown in
 local recipient table

---

### Post by markerman on 2007-11-27
P.S. I guess outbound message traffic from the exchange server does not have top go thru the posyfix server. So there can be one way traffic from external thru the firewall, to the postfix to the exchange server. That would be simpler.

---

### Post by HermanAB on 2007-11-27
Just go to the postfix web site.  There are example howto guides for setting up a mail proxy filter with SpamAssassin and ClamAV.

---

### Post by MJN on 2007-11-27
Probably best do as the good man says (unless it's '*install Citadel*' - just kidding Herman! ;))

You have just discovered the limitations of GUI-based config tools (particularly Webmin) - they all too often don't support the full feature set of the underlying application hence the lack of relay_ directives.

Try the guides and if you get seriously stuck post back. Good to see your naming sounds more sorted - this is critical to get right given you effectively have two machines sharing different aspects of the same service - each needs to know where its boundaries of responsibilities lie. As things stand Postfix knows not of your Exchange server and effectively thinks it is the 'end of the line' hence is attempting to delivery the message locally (but cannot given the lack of a table mapping users to mailboxes).

Good luck!

Mathew

---

### Post by HermanAB on 2007-11-27
Hey, Citadel and some iptables port redirection and Bob's your Uncle in about 1 hour flat...
:)

---

### Post by MJN on 2007-11-27
So you keep telling me! :)

Seriously, after your 50th recommendation I thought I ought to take a look to see what all the fuss was about and I must admit I was very impressed with what it could do...

However, in a way I was kind of *too* impressed insofar that it seemed to be doing too much for my liking. Being a man of logic I think part of the attraction of Linux for me is how a lot of things are broken down into smaller parts - effectively splitting a complex system into smaller more manageable sub-systems if you like. A case in point is the command line and piping/redirection.... Each element/tool in itself is designed to do a specific job and it does that job extremely well - you can then combine these tools in an infinite number of ways to achieve things limited only by your imagination.

So, back to my point, I view Citadel as doing too much - if all I want is a mail server I prefer to only install a mail server and will choose the best one I can. If I need additional functionality then I'll cherry pick the best of the best elements to perform those roles (e.g. virus scanning, IMAP mailbox access etc). If I then want anbulletin board I'd prefer to choose what board that is depending on my specific requirements (and indeed will also choose the underlying web server on similar grounds). To me Citadel is making all these choices for me so I can't help feel it is unlikely to be optimum for *my* needs. Furthermore, it carries a whole load of things I don't even want and I don't like carrying excess baggage (for want of a better, kinder sounding, phrase) around.

It certainly sounds like it's easier than an easy thing to setup.... however at the back of my mind I'm thinking *at what cost*?

Perhaps my perspective is skewed given I am equally interested in learning how to build a server just as much as benefiting from the end of result*.*

Horses for courses I suppose.

Just my 2c worth (and probably overpriced at that!).

Mathew

---

### Post by markerman on 2007-11-27
Thanks guys. And I'll look at Cidadel. But I'm not going to take the easy way out. I need to learn this.

---

### Post by KCPokes on 2007-11-27
Citadel, from looking at the site, looks inline with what Zimbra brings to the table, an all-in-one collaboration suite.  Great products that do exactly what they intend.  They may not give you the sense of pride from figuring it all out yourself, but frees up your time to figure out other of the world's questions.  I've ran Zimbra for a past year or so and it just works, and works well.

---

### Post by HermanAB on 2007-11-27
If you just need a proxy/filter then Citadel is the wrong tool for the job.  It would be like using a sledge hammer to swat a fly.

However, if you don't have time to waste on installing and managing a mail server, then it is just the ticket, as it installs ina jiffy and is zero maintenance.  Also, if you are presently running MS Exchange, then you should seriously consider switching to Citadel, since it can handle a much bigger load - it is more efficient and can store terabytes of mail, so it scales much better than Exchange.

I used postfix for many years - it works well, but I eventually got fed up with it, since it is a high maintenance system.

---

