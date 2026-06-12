---
title: "MTA Question"
date: 2011-01-25
forum: Server Platforms
---

### Post by nevyndweomer on 2011-01-25
I  have been running an EXIM4 email server for a number of years now and have never really managed to get to grips with it. 
This partially due to lack of time and partially due to the fact my brain just does not compute the configuration language of Exim. So I get spammed to death and I seem to to struggle to get my mail server accepted by some filters from the virtual domains I am running. 

A bit of background...
The MTA serves the mail for 6 domains each with only a handful of addresses. 

I am now at a cross roads.  

The server is a little long in the tooth (6.06.2 LTS) 

so I am thinking to upgrade and try once and for all to sort the MTA out 

I have seen what looks like a rather good how-to on setting up Postfix [http://ubuntuforums.org/showthread.php?t=185913](http://ubuntuforums.org/showthread.php?t=185913)

and I wonder if this MTA will be easier for me to fathom than my current one? 

I have been a member of the Exim mailing list for a while but I find the guys there are a little anti-debian and also a bit too busy to help someone like e who has tried to read the manuals but just can't get it. 

I am not thick but my background is networks and security and so the uber-geekness required to understand the exim documentation is a little beyond my field of expertise


Any suggestions welcome 

Choice:  

1  Stay with Exim and persevere to get it working how I want it 
2 Move to Postfix and try to get it working from scratch

---

### Post by James78 on 2011-01-25
I suggest using Postfix. I use it and have had no problems that weren't user error. Granted you will have to relearn a lot of stuff, but I think it'll be worthit. To get you started on a security configuration, I'll post my config. My security configuration blocks about 90% of spam, so almost nothing gets through. :) You might want to install and configure spamassassin as well for spam that does get through. As a small tidbit, in case you don't know anything about Postfix yet, you want to configure your domains to use virtual domains.

/etc/postfix/main.cf
```
# Security related config
smtpd_helo_required = yes
disable_vrfy_command = yes
smtpd_helo_restrictions =
    permit_mynetworks,
    reject_non_fqdn_hostname,
    reject_invalid_hostname
smtpd_recipient_restrictions =
    permit_mynetworks,
    permit_sasl_authenticated,
    reject_unauth_destination,
    reject_invalid_hostname,
    reject_unauth_pipelining,
    reject_non_fqdn_hostname,
    reject_non_fqdn_sender,
    reject_unknown_sender_domain,
    reject_non_fqdn_recipient,
    reject_unknown_recipient_domain,
    reject_rbl_client bl.spamcop.net,
    reject_rbl_client zen.spamhaus.org,
    reject_rbl_client combined.njabl.org,
    reject_rbl_client bhnc.njabl.org,
    reject_rhsbl_client rhsbl.sorbs.net,
    reject_rbl_client dul.dnsbl.sorbs.net,
    reject_rbl_client web.dnsbl.sorbs.net,
    reject_rbl_client zombie.dnsbl.sorbs.net,
    reject_rbl_client dnsbl.ahbl.org,
    reject_rhsbl_client rhsbl.ahbl.org,
    permit

# clamsmtp email virus scanning
content_filter = scan:127.0.0.1:10026
receive_override_options = no_address_mappings
```
At the end, the clamsmtp thing you see is email virus scanning by ClamAV. You can see how to set it up [here]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter"). I'd recommend more tutorial and documentation sources for you, however you found the jackpot, and all you'll ever need. Good luck!

---

### Post by nevyndweomer on 2011-01-27
Hi   There 
Thanks for your reply.  I will certainly take a look at the suggested links. 

is it possible for postfix to deliver directly to the ./Maildir of the recipient or do I have to pass the messages to another daemon for delivery? 

Exim has the mail processing and delivery routers in one so I just need to be clear. 

Nev

---

### Post by James78 on 2011-01-27
> **nevyndweomer said:**
> Hi   There 
Thanks for your reply.  I will certainly take a look at the suggested links. 

is it possible for postfix to deliver directly to the ./Maildir of the recipient or do I have to pass the messages to another daemon for delivery? 

Exim has the mail processing and delivery routers in one so I just need to be clear. 

Nev
If I remember right on how my system is setup, it has to be passed to another daemon. Procmail I believe.

---

