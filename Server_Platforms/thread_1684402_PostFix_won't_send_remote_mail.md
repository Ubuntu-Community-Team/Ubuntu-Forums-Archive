---
title: "PostFix won't send remote mail"
date: 2011-02-09
forum: Server Platforms
---

### Post by Oxid3! on 2011-02-09
Hi,

I have spent the last 24 hours searching the internet for an issue to resolve my problem. I have tried the verious solutions posted by people and followed endless amounts of tutorials

In the end i followed [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) line by line

This allowed me to recieve email fine, but only send email locally.

I either get a "Relay access denied" message, or as of last night is is now "Recipient Address Rejected"

Below is a link to my Main.cf file, please tell me what im doing wrong!!

[http://squishyfruit.com/main.cf](http://squishyfruit.com/main.cf)

Regards.

Dave.

---

### Post by elico on 2011-02-09
try to lower you restrictions such in this section to none at all and add one by one.
by the way take off the php info in your root index.php \index.html file.

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
 # Requirements for the sender details 
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
# Requirement for the recipient address 
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject
smtpd_data_restrictions = permit_sasl_authenticated
#mydestination = squishyfruit.com
# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes


if you can do some
tail -f /var/log/mail.log and give us logs it will be more useful.

if you will not manage i will send you working settings file.

---

### Post by Oxid3! on 2011-02-09
Thanks for this, my problem was because I didnt have SASL installed so it couldnt authorize it properly

Thanks for helping.

---

### Post by elico on 2011-02-09
hooo thats one of the common problems.

happy you got it.
im using the dovecot auth so im good.

---

