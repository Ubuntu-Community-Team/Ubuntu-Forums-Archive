---
title: "Postfix warning: Illegal address syntax"
date: 2010-12-06
forum: Server Platforms
---

### Post by redelek on 2010-12-06
Hi,

For several days I have a problem with postfix I have these messages in the logs
Dec 3 2:32:16 p.m. mail postfix / smtpd [21282]: warning: Illegal address syntax from
ip-93.159.XX.XXX.static.crowley.pl [93.159.XX.XXX] in RCPT command: <'marketing@bluemedia.pl'>

My clients are the restrictions for such
smtpd_recipient_restrictions =
 reject_non_fqdn_recipient,
 reject_unknown_recipient_domain,
 permit_mynetworks,
 permit_sasl_authenticated,
 reject_unauth_pipelining,
 reject_unauth_destination
 reject_sender_login_mismatch,
 reject_unauth_destination
 reject_unknown_helo_hostname,
 reject_non_fqdn_helo_hostname,
 check_policy_service inet: 127.0.0.1:60000,
 permit

Something is wrong with the address of the client but I can not find the cause and do not know where to improve. My system is Ubuntu-server 10.04TLS

I will be grateful for the help

Best Regards
Redelek

---

### Post by SeijiSensei on 2010-12-06
> **redelek said:**
> Illegal address syntax from
ip-93.159.XX.XXX.static.crowley.pl [93.159.XX.XXX] in RCPT command: <'marketing@bluemedia.pl'>

Are those single quotes in the actual sender address?  They're illegal.  It should read <marketing@bluemedia.pl>.

---

