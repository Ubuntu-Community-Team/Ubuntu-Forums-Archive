---
title: "Need help configuring smtpd_sender_restrictions in postfix"
date: 2012-03-05
forum: Server Platforms
---

### Post by omael on 2012-03-05
Hello everyone,

i'm a little lost since this is my first server i've configured using postfix/spamassassin/clamav (i followed [this guide]("http://flurdy.com/docs/postfix/") and is using the mysql queries for the users and domain lists)

What i'm trying to do is to allow only my users to send mail through my server. The problem arised when hotmail blocked my server because it was blacklisted in symantec. After some research i found that someone was infected by a spambot and is sending fake mails:
```
[INDENT]Mar  3 23:48:20 www postfix/qmgr[19564]: F09F7C0A1E3: from=<[EMAIL="byys@yahoo.com.mx"]byys@yahoo.com.mx[/EMAIL]>, size=283, nrcpt=8 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: F0093C0A1B0: from=<[EMAIL="oquz@hi5.com"]oquz@hi5.com[/EMAIL]>, size=280, nrcpt=2 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: B9DC4C0A1C8: from=<[EMAIL="vuvm@axtel.net"]vuvm@axtel.net[/EMAIL]>, size=281, nrcpt=5 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: BADFDC0A1BA: from=<>, size=2570, nrcpt=1 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: B8B4CC0A1DD: from=<>, size=5114, nrcpt=1 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: BDBDFC0A1D8: from=<[EMAIL="ixcetkfn@prodigy.net.mx"]ixcetkfn@prodigy.net.mx[/EMAIL]>, size=282, nrcpt=9 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 8F3C1C0A200: from=<>, size=3034, nrcpt=1 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 42E6FC0A1F2: from=<[EMAIL="hardeqxh@cablevision.com.mx"]hardeqxh@cablevision.com.mx[/EMAIL]>, size=280, nrcpt=8 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 055D1C0A1CE: from=<>, size=4495, nrcpt=1 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 0A016C0A1EA: from=<[EMAIL="qyrrrw@yahoo.com"]qyrrrw@yahoo.com[/EMAIL]>, size=282, nrcpt=8 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 05949C0A1BC: from=<[EMAIL="icxkozk@hotmail.com"]icxkozk@hotmail.com[/EMAIL]>, size=282, nrcpt=4 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 1627AC0A1DB: from=<>, size=2645, nrcpt=1 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 17FBDC0A191: from=<[EMAIL="gstgpsm@mercadolibre.com.mx"]gstgpsm@mercadolibre.com.mx[/EMAIL]>, size=281, nrcpt=8 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 10855C0A1E1: from=<[EMAIL="kdthrsh@hotmail.com"]kdthrsh@hotmail.com[/EMAIL]>, size=282, nrcpt=9 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 1C561C0A1C5: from=<[EMAIL="hwxrv@cablevision.com.mx"]hwxrv@cablevision.com.mx[/EMAIL]>, size=281, nrcpt=8 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: D6B22C0A1DF: from=<[EMAIL="wbhoejek@hotmail.com"]wbhoejek@hotmail.com[/EMAIL]>, size=283, nrcpt=6 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: D1CC5C0A1E9: from=<[EMAIL="kkmdsd@gmail.com"]kkmdsd@gmail.com[/EMAIL]>, size=282, nrcpt=8 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 7A85FC0A1E4: from=<[EMAIL="vkbhmysa@facebookmail.com"]vkbhmysa@facebookmail.com[/EMAIL]>, size=282, nrcpt=4 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 61C73C0A1EF: from=<[EMAIL="zstpr@prodigy.net.mx"]zstpr@prodigy.net.mx[/EMAIL]>, size=282, nrcpt=3 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 98C73C0A1BE: from=<[EMAIL="rplatm@prodigy.net.mx"]rplatm@prodigy.net.mx[/EMAIL]>, size=282, nrcpt=6 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 964F2C0A201: from=<>, size=3656, nrcpt=1 (queue active)
Mar  3 23:48:20 www postfix/qmgr[19564]: 2D4BFC0A1D5: from=<[EMAIL="jmvgkwh@yahoo.com.mx"]jmvgkwh@yahoo.com.mx[/EMAIL]>, size=280, nrcpt=9 (queue active)
[/INDENT]
```So first i need to drop all the mail that doesn't have a sender and then i need to reject everything that isn't in my domain list and if needed add a new query to the mysql database to check which domains or which e-mail the message can come from. The main problem is that i think i need to still allow *@hotmail.com as the sender if i which to receive mail from them. Since this is a production environment i can't do a lot of test, i still have configured another little server to conduct my tests but it doesn't reflect everything, specially the block done by hotmail.

The relevant part of my main.cf is:

```



# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit, reject_unknown_helo_hostname
# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

# require proper helo at connections 
smtpd_helo_required = yes
#smtpd_helo_required = no 
# waste spammers time before rejecting them permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_delay_reject = yes
disable_vrfy_command = yes



```Could you help me out here?

---

### Post by nsnidanko on 2012-03-06
It would be better if you post whole config file. If I understand your setup correctly;

Postfix should only relay email for "your" domains. Why does it relay email for hotmail.com, yahoo.com etc? It seems like there is a problem with your relay_domains.

As for preventing infected computers getting you blacklisted again: look into limiting rate of emails postfix will accept from one client. That could be also a problem if someone uses mass mailers to relay via your server.

---

### Post by omael on 2012-03-06
Thanks, i'll post it here.
There should be a problem in my configuration about the relay_domains, i don't want to be able to telnet localhost 25 and mail something from hotmail.com.
How can i limit the number of mails sent?

---

### Post by omael on 2012-03-06
```

myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP
biff = no

append_dot_mydomain = no

unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 1d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 32
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12


readme_directory = no

smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_data_restrictions = reject_unauth_pipelining

myhostname = www.pcsmexico.com
myorigin = /etc/mailname
mydestination =
local_repicient_maps =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 201.161.22.21/32 189.141.43.125/32 201.0.0.0/8 200.0.0.0/8 187.0.0.0/8 188.0.0.0/8 189.0.0.0/8 189.227.90.163/32
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host



smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit, reject_unknown_helo_hostname
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

smtpd_helo_required = yes
permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

message_size_limit = 20000000
mailbox_transport = virtual
virtual_minimum_uid = 1000
virtual_create_maildirsize = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_quota.cf
virtual_mailbox_limit_inbox = yes
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "El usuario que esta tratando de contactar ha excedido su limite de correo."
virtual_overquota_bounce = yes
virtual_maildir_extended = yes

smtpd_recipient_restrictions = permit_mynetworks, reject_non_fqdn_recipient, check_client_access hash:/etc/postfix/pop-before-smtp, reject_unauth_destination

```

---

### Post by omael on 2012-03-09
*bump*

can anyone help configure the smtpd to reject mails if the sender is mailing them too fast? as in more than a couple each minute.

---

### Post by nsnidanko on 2012-03-09
Sorry for late reply;

Your config is extremely messy, everything is configured backwards.

Firts, fix your "mynetworks" because 201.0.0.0/8 200.0.0.0/8 187.0.0.0/8 188.0.0.0/8 189.0.0.0/8 opens up a lot of different hosts. 
Put there only trusted networks, which you control.

Second fix your


-> smtpd_client_restriction You should start it with permit_sasl_authenticated and permit_mynetworks 
followed  by rejecting via blacklist. Don't forget to put permit at the end.

-> Fix smtpd_helo_restrictions by having permit at the end

-> smtpd_recipient_restrictions - looks ok but you need to fix mynetworks, 
since such a huge scope opens a server for alot of spammers.

To limit number of connections from the same server as well as number of 
open connections enable anvil service in your master.cf as well as add the following options:

anvil_rate_time_unit = rate in seconds
smtpd_client_connection_count_limit = number of open connections
smtpd_client_connection_rate_limit = number of connections per rate

---

### Post by omael on 2012-03-09
> **nsnidanko said:**
> 
To limit number of connections from the same server as well as number of 
open connections enable anvil service in your master.cf as well as add the following options:

anvil_rate_time_unit = rate in seconds
smtpd_client_connection_count_limit = number of open connections
smtpd_client_connection_rate_limit = number of connections per rate

Thanks, is anvil any additional software i need to configure as amavis? am i getting it right: anvil_rate is how long a connection can last in seconds and rate limit is how many connections in that limit?

edit: shouldn't the lines above be in main.cf?

---

### Post by lisati on 2012-03-09
Just as an aside before I get ready for "real life" activities, I'd advise against completely blocking the null sender "<>", because it has valid uses such as non-delivery reports from your own server.

---

### Post by omael on 2012-03-09
> **lisati said:**
> Just as an aside before I get ready for "real life" activities, I'd advise against completely blocking the null sender "<>", because it has valid uses such as non-delivery reports from your own server.
didn't know that, thanks, shouldn't this be a security breach or something?

---

### Post by nsnidanko on 2012-03-13
> **omael said:**
> Thanks, is anvil any additional software i need to configure as amavis? am i getting it right: anvil_rate is how long a connection can last in seconds and rate limit is how many connections in that limit?

edit: shouldn't the lines above be in main.cf?

No not exactly anvil_rate_time_unit is the "time frame" variable so to say. Rate limit is number of connections, which one host can establish within a time frame you set in anvil_rate_limit

Yes these lines should go main.cf, I did not express myself clear enough in my earlier post. Anvil should be installed by default, try **man anvil** to see the manual page.

---

### Post by omael on 2012-03-13
```

anvil_rate_time_unit = 30
smtpd_client_connection_count_limit = 3
smtpd_client_connection_rate_limit = 3


```

I added this, but i don't see them working. I tried to send 4 mails under 30 second but it didn't rejected any, and i received them without a problem. Am i missing something? i do have anvil installed as you told me.

---

### Post by nsnidanko on 2012-03-13
Check if it is enabled in your master.cf file. You should see something like

```
anvil     unix  -       -       n       -       1       anvil
```

Also do you anvil logs in your mail.log?

---

### Post by omael on 2012-03-13
> **nsnidanko said:**
> Check if it is enabled in your master.cf file. You should see something like

```
anvil     unix  -       -       n       -       1       anvil
```Also do you anvil logs in your mail.log?
i have that exact line in master.cf, i don't have anvil logs, how should i enable them?

---

### Post by nsnidanko on 2012-03-13
> **omael said:**
> i have that exact line in master.cf, i don't have anvil logs, how should i enable them?
This is very odd... It is hard to guess what else could cause it (that line needs to be uncommented to enable it, so no # at the start of the line)

You should see something along the following in your mail.log file:

 postfix/*anvil*[18954].....

---

### Post by omael on 2012-03-15
I checked and i have this kind of logs after greping for anvil, but i don't see the connection is dropped, i put there the limit to be 3 connections in 30 seconds: 
```
Mar 15 10:00:40 www postfix/anvil[29213]: statistics: max connection rate 3/30s for (smtp:216.220.51.211) at Mar 15 09:52:54
Mar 15 10:00:40 www postfix/anvil[29213]: statistics: max connection count 1 for (smtp:120.165.55.237) at Mar 15 09:50:50
Mar 15 10:00:40 www postfix/anvil[29213]: statistics: max cache size 4 at Mar 15 09:56:33
Mar 15 10:10:40 www postfix/anvil[29213]: statistics: max connection rate 1/30s for (smtp:213.199.154.209) at Mar 15 10:00:57
Mar 15 10:10:40 www postfix/anvil[29213]: statistics: max connection count 1 for (smtp:213.199.154.209) at Mar 15 10:00:57
Mar 15 10:10:40 www postfix/anvil[29213]: statistics: max cache size 4 at Mar 15 10:01:45
Mar 15 10:16:14 www postfix/anvil[29213]: statistics: max connection rate 1/30s for (smtp:69.64.157.17) at Mar 15 10:10:55
Mar 15 10:16:14 www postfix/anvil[29213]: statistics: max connection count 1 for (smtp:69.64.157.17) at Mar 15 10:10:55
Mar 15 10:16:14 www postfix/anvil[29213]: statistics: max cache size 3 at Mar 15 10:11:38

```
As i understand in the fourth mail sent in 30 seconds it should reply with a postmaster error message, right?

---

### Post by webservervideos on 2012-03-16
look through your config for all the errors, those missing commas really seemed to have helped me out in the past.  postfix has a built in error counter to stop people. Properly configured those mails slamming you will just bounce off.  the order in which you add items REALLY matters. I would do the rbl and rhsbl after mostly everything.  look at the postfix site and look at the smtpd client, helo, recipient restrictions and add a lot of them.  smtpd delay yes is needed for some and a great way to see massive rejects in your log...happy days.

---

