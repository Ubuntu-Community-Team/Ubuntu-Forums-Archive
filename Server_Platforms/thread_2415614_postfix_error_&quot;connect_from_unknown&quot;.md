---
title: "postfix error &quot;connect from unknown&quot;"
date: 2019-03-28
forum: Server Platforms
---

### Post by tomdf on 2019-03-28
Hello guys,

i have many error messages from postfix : 
```

connect from unknown [ip address]

```
i am running ubuntu 18.04

i think its spam.
can anyone  give me an idea how to stop this spam?

i read already to change main.cf 
```

smtpd_sender_reststricitons = reject_unknown_revers_client_hostname 

```

but it does not work 

maybe anyone can help me with this issue

thanks a lot

Tom

---

### Post by SeijiSensei on 2019-03-28
Is "revers" just a typo, or is it also spelled incorrectly in main.cf?

---

### Post by tomdf on 2019-03-29
hi, oh yes its just a typo my main.cf is this:

```

[COLOR=#202124][FONT=Roboto]smtpd_helo_required = yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]smtpd_helo_restrictions = permit_sasl_authenticated, permit_mynetworks, check_helo_access regexp:/etc/postfix/helo_access, reject_invalid_hostname, reject_non_fqdn_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostname, check_helo_access regexp:/etc/postfix/blacklist_helo[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]smtpd_sender_restrictions = check_sender_access regexp:/etc/postfix/tag_as_originating.re , permit_mynetworks, permit_sasl_authenticated, reject_unknown_reverse_client_hostname, check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf, check_sender_access regexp:/etc/postfix/tag_as_foreign.re[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]smtpd_client_message_rate_limit = 100[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]maildrop_destination_concurrency_limit = 1[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]maildrop_destination_recipient_limit = 1[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]virtual_transport = dovecot[/FONT][/COLOR]

```

and the error message is this:

```

[COLOR=#202124][FONT=Roboto]Mar 29 18:17:22 server1 postfix/smtpd[14983]: warning: unknown[91.212.150.158]: SASL LOGIN authentication failed: UGFzc3dvcmQ6[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:17:22 server1 postfix/smtpd[14983]: disconnect from unknown[91.212.150.158] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:17:34 server1 postfix/smtpd[14996]: connect from unknown[93.157.63.30][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:17:46 server1 postfix/smtpd[14996]: warning: unknown[93.157.63.30]: SASL LOGIN authentication failed: UGFzc3dvcmQ6[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:17:46 server1 postfix/smtpd[14996]: disconnect from unknown[93.157.63.30] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:18:02 server1 postfix/smtpd[14983]: connect from unknown[91.212.150.158][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:18:14 server1 postfix/smtpd[14983]: warning: unknown[91.212.150.158]: SASL LOGIN authentication failed: UGFzc3dvcmQ6[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:18:15 server1 postfix/smtpd[14983]: disconnect from unknown[91.212.150.158] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:18:41 server1 postfix/smtpd[14996]: warning: hostname [/FONT][/COLOR][myort.net]("http://myort.net/")[COLOR=#202124][FONT=Roboto] does not resolve to address 93.157.63.6[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Mar 29 18:18:41 server1 postfix/smtpd[14996]: connect from unknown[93.157.63.6][/FONT][/COLOR]


```

i started postfix new

maybe you have any idea?
thanks so much for your help

---

