---
title: "Postfix Configuration: How to restrict use of CC"
date: 2011-01-17
forum: Server Platforms
---

### Post by balia on 2011-01-17
I have configured postfix on my server.

telnet mydomain.com 25
helo validdomain.com
mail from: validaddress@yahoo.com
rcpt to: validuser@mydomain.com
data
From: validaddress@validdomain.com
To: validuser@mydomain.com
CC: user1@domain1.com,user2@domain2.com
Subject: Testing postfix
Message body

When I run this test, the email is delivered to valid user but also my server shoots an email to user1 and user2.
I have implemented client, helo and recipient restrictions as below.
How do I prevent the malicious use of CC as described here?
Thank you


Snap of main.cf
-------------------
smtpd_client_restrictions = permit_mynetworks,
                                reject_invalid_hostname,
                                reject_rbl_client zen.spamhaus.org,
                                reject_unknown_client,
                                permit

smtpd_helo_restrictions = permit_mynetworks,
                                check_helo_access hash:/etc/postfix/helo_access,
                                reject_unauth_pipelining,
                                reject_non_fqdn_hostname,
                                reject_invalid_hostname,
                                warn_if_reject reject_unknown_hostname,
                                permit

smtpd_recipient_restrictions =  reject_non_fqdn_sender,
                                reject_non_fqdn_recipient,
                                reject_non_fqdn_hostname,
                                reject_invalid_hostname,
                                permit_mynetworks,
                                reject_unauth_pipelining,
                                reject_unknown_sender_domain,
                                reject_unknown_recipient_domain,
                                reject_unauth_destination,
                                reject_unknown_client,
                                permit

smtpd_sender_restrictions =  permit_mynetworks,
                                reject_non_fqdn_sender,
                                reject_unknown_sender_domain,
                                reject_unknown_address

---

### Post by SeijiSensei on 2011-01-17
The Cc: header is part of the message itself.  Mail Transfer Agents like Postfix or sendmail have no control over it.

Think of an email message as akin to a normal letter.  In the "letter" itself you have a From:, a To:, a Subject:, and an optional body.  This letter is placed in an "envelope" that contains a From and a To address generated during the SMTP exchange.  The envelope From may or may not match the letter's From: for various reasons.  However the To field on the the envelope(s) generated are taken from the To:, Cc:, and Bcc: fields in the letter.

The standard for messages, [RFC2822]("http://www.ietf.org/rfc/rfc2822.txt"), specifies that Cc: and Bcc: fields are legitimate parts of a standards-compliant message.  [RFC2821]("http://www.ietf.org/rfc/rfc2821.txt") requires MTAs to strip any Bcc: headers from a message, but not the Cc: fields.

The only way I can see implementing what you want is to write a custom filter of some sort that sits in front of Postfix or some other MTA and strips the Cc: field from every message.  No standards-compliant MTA will do what you want.

---

### Post by balia on 2011-01-17
In the example above, the sender is outside my domain.
Isn't any sort of verification in postfix to disable the CC field when the sender is not in my domain?
If postfix accepts the message (as the sender and the recipient appear legitimate), it seems to me that a spammer could use this postfix behavior to relay spam using the CC field. A spammer would just need to know a valid email for my domain and send spam to the recipients listed in CC.

---

### Post by SeijiSensei on 2011-01-17
This might be of interest.  

[http://www.irbs.net/internet/postfix/0805/0920.html](http://www.irbs.net/internet/postfix/0805/0920.html)

Are you telnetting to the server from the machine itself, or from another machine?  If you're on the same server, I think you have full rights because 127.0.0.1 is (usually) in "my_networks" and you have "permit_mynetworks" specified in the rules above.  

If this machine is only used to send mail from automated processes, or to handle mail for a well-defined set of local networks, you shouldn't need to worry about external exploitation.  If you're accepting mail from outside senders, I suspect you need some additional armor.  I'm not a Postix user, so beyond that I can't say. I think this part of the email posting above may provide a glimmer of a solution: 

"We use a
virtual_alias_map = hash:/etc/postfix-internal/virtual

Which lists all of our accounts and email aliases, so this kicks in
with reject_unlisted_sender."

But I could easily be wrong.

---

### Post by James78 on 2011-01-17
You could create a security related configuration for Postfix to stop most known malicious users. This is my config, and it also catches 95% of spam as well. Also, it scans the emails for viruses using ClamSMTP (see [this]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter")).
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

---

### Post by balia on 2011-01-18
Yes I did make the telnet test from a remote machine.

What I am concerned is that in the test, the email is legitimate, except for the CC field; the postfix server receives an email for a local recipient and delivers it correctly.
What I wasn't expecting was that postfix would 'relay' the message to the CC recipients!

I looked at James configuration, and it seems to address the spam issue. James, would you mind checking if you can replicate my test with your configuration?

---

