---
title: "Mail sent by apache-php gets sent in SPAM"
date: 2007-08-12
forum: Server Platforms
---

### Post by prodsacnetworking on 2007-08-12
Hi,

I have a couple of web servers AND two mail servers.

All servers are Ubuntu 6.06.1 LTS.

WEb: apache 2, PHP5.
Mail: Postfix .2.10-1ubuntu0.1: amd64

Every email that get sent by Apache-PHP5 finishes in spam (hotmail, gmail, etc)... Some clients don't even receive it at all.

What can I do?
the domains have SPF records, my IPs and server nameand dns are not in Blacklists.

thanks..

---

### Post by gnaunited on 2007-08-12
See if the headers reveal any information about why it was marked as spam.

---

### Post by heimo on 2007-08-12
Run your example mail through spamassassin and see what parts of it cause spam score to to raise.

---

### Post by prodsacnetworking on 2007-08-13
here is the header:
is it because there is no: 

X-IP: 69.156.23.23
X-URI: /site/test/test2.php
X-ID: 2451728

Return-Path: <sender@localdomain.com>
X-Original-To: [email]recipient@remotedomain.com[/email]
Delivered-To: [email]sender@localdomain.com[/email]
Received: from localhost (localhost [127.0.0.1])
            by mail.prodsacnetworking.com (Postfix) with ESMTP id 9A657D9C674
            for <recipient@remotedomain.com>; Sun, 12 Aug 2007 17:31:17 -0400 (EDT)
Received: from mail.prodsacnetworking.com ([127.0.0.1])
            by localhost (morpheus.prodsacnetworking.com [127.0.0.1]) (amavisd-new, port 10024)
            with ESMTP id 19880-10 for <recipient@remotedomain.com>;
            Sun, 12 Aug 2007 17:31:17 -0400 (EDT)
Received: from smith (smith.prodsacnetworking.com [66.152.78.3])
            by mail.prodsacnetworking.com (Postfix) with SMTP id 75234D9C5AE
            for <recipient@remotedomain.com>; Sun, 12 Aug 2007 17:31:16 -0400 (EDT)
Received: by smith (sSMTP sendmail emulation); Sun, 12 Aug 2007 17:27:46 -0400
Date: Sun, 12 Aug 2007 17:27:46 -0400
To: [email]recipient@remotedomain.com[/email]
Subject: Information
MIME-Version: 1.0
Content-type:text/html;charset=iso-8859-1
From: Himself <sender@localdomain.com>,
            [email]rnTo@mmail.prodsacnetworking.com:recipient@remotedomain.com[/email] <recipient@remotedomain.com>,
            [email]rn@mmail.prodsacnetworking.com[/email]
Message-Id: <20070812213116.75234D9C5AE@mail.prodsacnetworking.com>

---

### Post by Mr. C. on 2007-08-14
I believe the OP is asking about why his email to remote server's ends up being tagged as spam.  Local checking of email will not help.

Your IP is listed in SORBS and APEWS_L2.  See:

[http://openrbl.org/client/#69.156.23.23](http://openrbl.org/client/#69.156.23.23)

You'll have to examine mail on those remote servers to evaluate the headers present.  It is not because there are not X-ID, etc. headers; these headers would be optional.

Since you've obfuscated your email address and domain, I can't check further.  You'll have to show actual headers to gain more information.  You can send them to me via PM if you are concerned about revealing information.

I see your mail was sent via sSMTP, yet you have postfix installed.  Why are you using ssmtp ?

MrC

---

### Post by heimo on 2007-08-14
> **Mr. C. said:**
> I believe the OP is asking about why his email to remote server's ends up being tagged as spam.  Local checking of email will not help.

Yes, if he can see what causes mail to get tagged as spam, it'll be easier to fix, I agree. And if log or other information isn't available, running it through a good spam filter may give hints what might be wrong. My first guess was that what ever script is sending messages, doesn't follow standards too well - bad headers for instance.

---

### Post by prodsacnetworking on 2007-08-26
ok. 

Locally, it's not tagged as spam... 

Is it a SFP problem?
Is it a DNS, postfix config problem?

I'm beginning to be in a real dead line issue now... 

thanks..

---

### Post by prodsacnetworking on 2007-08-26
Here are my files:

> 
root@morpheus:~# cat /etc/postfix/main.cf 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/postfix/postfix.cert
smtpd_tls_key_file=/etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.prodsacnetworking.com
#alias_maps = hash:/etc/aliases
#alias_database = hash:/etc/aliases
myorigin = /etc/mailname
local_recipient_maps =
mydestination = 
relayhost = 
mynetworks = XXXXXXXXX, XXXXXXXXX, 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
message_size_limit = 15000000

# Delais et utilisation des relais
delay_warning_time = 4h 
unknown_local_recipient_reject_code = 450 
maximal_queue_lifetime = 7d 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 
smtp_helo_timeout = 60s 
smtpd_recipient_limit = 16 
smtpd_soft_error_limit = 3 
smtpd_hard_error_limit = 12

# Restriction et filtrage
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#smtpd_sender_restrictions = check_client_access hash:/etc/postfix/pop-before-smtp, permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sender_restrictions = check_client_access hash:/etc/postfix/pop-before-smtp, permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
smtpd_recipient_restrictions = check_client_access hash:/etc/postfix/pop-before-smtp, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit


smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

# Connexion a la BD MySQL
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps =  mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

content_filter = amavis:[127.0.0.1]:10024
#receieve_override_options = no_address_mappings


---

### Post by Mr. C. on 2007-08-27
Please re-read my posts.  You haven 't responded to them.

Without the data, there's not much we can do but guess.  You've been assuming that if you simply change *your* postfix setup, that *other* mail servers will stop tagging as spam the mail you send to them.  This is an invalid assumption.  You need to discover *why* your mail is being tagged as spam before applying solutions.

MrC

---

### Post by prodsacnetworking on 2007-08-27
Mr.C

Ok, thanks. Sorry, I passed over you other post I guess.

Here's the setup.
Client connects on php page.
Click on send:

here the script:
> 
<?php
$email = "email@hotmail.com";
$subject = "Test email";
$message = "Test email";
mail($email, $subject, $message);
echo "Message envoyé.";
?>

php sends to the local smtp sender (ssmtp and I tried now ti a local postfix with a smart host: mail.prodsacnetworking.com)

The IP that had a entry in the RBL site you gave was the client IP. I tried from other IPs and still got the same problem..

Here's a message's header:
> 
X-Message-Delivery: Vj0zLjQuMDt1cz0wO2k9MDtsPTA7YT0w
X-Message-Status: n:0
X-SID-PRA: [email]apache@www.prodsacnetworking.com[/email]
X-Message-Info: 6sSXyD95QpWZfiCvHe74CMPk9j/vAsLnMrjAluUKkTwTSY11ciBkwSRufzbugvLx6IRIZRoAvR4=
Received: from smith.prodsacnetworking.com ([66.152.78.3]) by bay0-mc3-f7.bay0.hotmail.com with Microsoft SMTPSVC(6.0.3790.2668);
	 Sun, 26 Aug 2007 18:44:31 -0700
Received: by smith.prodsacnetworking.com (Postfix, from userid 80)
	id 1E1B51023EB; Sun, 26 Aug 2007 21:44:27 -0400 (EDT)
To: [email]email@hotmail.com[/email]
Subject: Test - email
Message-Id: <20070827014427.1E1B51023EB@smith.prodsacnetworking.com>
Date: Sun, 26 Aug 2007 21:44:27 -0400 (EDT)
From: [email]apache@www.prodsacnetworking.com[/email]
Return-Path: [email]apache@www.prodsacnetworking.com[/email]
X-OriginalArrivalTime: 27 Aug 2007 01:44:31.0696 (UTC) FILETIME=[D0395D00:01C7E84B]


On this one, the local postfix on the www servers sends it himself... but it's the same thing with a smarthost...

thanks

---

### Post by Mr. C. on 2007-08-27
So we can see there are no spam-related headers in the message.  Was it filed in your hotmail spam folder ?

I don't use hotmail, but I assume they have settings that allow you to whitelist your server for your account.  Since there are no clues in the headers below, you'll have to review hotmail's policy on how and why they file mail as spam.  If you discover that being on the SORBS list is a problem with hotmail, you'll have to request de-listing, find a new (acceptable) IP, and/or request that hotmail place you on a sender's whitelist.

MrC

---

### Post by yurtboy on 2007-11-03
Same problems here

---

