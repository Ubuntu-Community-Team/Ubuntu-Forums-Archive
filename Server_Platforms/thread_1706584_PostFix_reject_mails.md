---
title: "PostFix reject mails"
date: 2011-03-14
forum: Server Platforms
---

### Post by axel50397 on 2011-03-14
Hi everybody,

I'm new to this forum.

I have the exact same problem as: [http://ubuntuforums.org/showthread.php?t=477590](http://ubuntuforums.org/showthread.php?t=477590)
My production server is rejecting mails, yesterday everything was ok :(

Here is my postconf -n:
```
peach:/home/max13# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_at_myorigin = yes
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
inet_interfaces = all
local_destination_recipient_limit = 1
local_recipient_maps = unix:passwd.byname $alias_database
local_transport = local
mail_spool_directory = /var/mail
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 0
mydestination = $myhostname, $mydomain
mydomain = peach.virtual-info.eu.local
myhostname = peach.virtual-info.eu
mynetworks_style = host
myorigin = $myhostname
recipient_delimiter = +
setgid_group = postdrop
smtpd_banner = $myhostname ESMTP ispCP 1.0.7 OMEGA Managed
smtpd_data_restrictions = reject_multi_recipient_bounce,                               reject_unauth_pipelining
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks,                               permit_sasl_authenticated,                               reject_invalid_helo_hostname,                               reject_non_fqdn_helo_hostname
smtpd_recipient_restrictions = reject_non_fqdn_recipient,                               reject_unknown_recipient_domain,                               permit_mynetworks,                               permit_sasl_authenticated,                               reject_unauth_destination,                               reject_unlisted_recipient,                               check_policy_service inet:127.0.0.1:12525,                               check_policy_service inet:127.0.0.1:10025,                               permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = reject_non_fqdn_sender,                               reject_unknown_sender_domain,                               permit_mynetworks,                               permit_sasl_authenticated
transport_maps = hash:/etc/postfix/ispcp/transport
virtual_alias_maps = hash:/etc/postfix/ispcp/aliases
virtual_gid_maps = static:8
virtual_mailbox_base = /var/mail/virtual
virtual_mailbox_domains = hash:/etc/postfix/ispcp/domains
virtual_mailbox_limit = 0
virtual_mailbox_maps = hash:/etc/postfix/ispcp/mailboxes
virtual_minimum_uid = 1002
virtual_transport = virtual
virtual_uid_maps = static:1002
```

Does anyone have an idea ?

Thanks for your help.

---

### Post by abix_adam_pl on 2011-03-14
Please, show any log, which can show, that your server is rejecting mail. This coud be for exmaple bounce mail.... there is exactly written, why your server is rejecting mail.

```
mydomain = peach.virtual-info.eu.local
```
should be
```
mydomain = peach.virtual-info.eu

```

I'm sending test mail to see the bounce:
> 
                  The mail system

<test@peach.virtual-info.eu>: host peach.virtual-info.eu[91.121.88.208] said:
    550 5.1.1 <test@peach.virtual-info.eu>: Recipient address rejected: User
    unknown in local recipient table (in reply to RCPT TO command)

Another test - to root account:

> 
Mar 14 09:51:58 cs postfix/smtp[24369]: D2324D22234: to=<root@peach.virtual-info.eu>, relay=peach.virtual-info.eu[91.121.88.208]:25, delay=25, delays=0.2/0/0.23/25, dsn=4.3.5, status=deferred (host peach.virtual-info.eu[91.121.88.208] said: 451 4.3.5 Server configuration problem (in reply to RCPT TO command))


So, change mydomain and then test once again.
Adam

---

### Post by axel50397 on 2011-03-14
Hum...

It's curious because our postfix conf didn't change from 2 years :P

Anyway, these mailboxes don't exist, can you test for example with [email]max13@tag-team.fr[/email] please ? (Cause I don't know how to do what you've just done ^^'

I've restarted postfix since my first post.
Now it doesn't reject ALL, but from the webmail, no emails received and I can't delete or move any email :/

---

### Post by abix_adam_pl on 2011-03-14
Looks OK.

> cs:~# cat  /var/log/mail.info | grep @tag-team
Mar 14 21:46:03 cs postfix/smtp[21541]: A8067D22232: to=<max13@tag-team.fr>, relay=mail.tag-team.fr[91.121.88.208]:25, delay=4, delays=0.18/0/3.7/0.16, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 54B9FC3807E)

Above code is log from my own hosting server.

And 2nd thing - webmail has nothing to postfix. So, if you have trouble with webmail, then I think there is something wrong with  your server at all.

Adam

---

### Post by falko on 2011-03-15
Are there any errors in /var/log/mail.log?

---

### Post by lister171254 on 2011-06-07
I have the same problem. Everything has and for most part still is ok, but one message today was rejected. Nothing changed on the server. The email that worked contains the details about the one that bounced. There are no errors logged on the server. Other emails are getting through, but I have no way of knowing if this applies to all of them

------------ Excerpts of the email-------------------
Begin forwarded message:

From: [email]postmaster@mac.com[/email]
> 
> Date: 7 June 2011 1:20:07 PM AEST
> 
> To: [email]denistebbutt@mac.com[/email]
> 
> Subject: Delivery Notification: Delivery has failed
> 
> 
> This report relates to a message you sent with the following header fields:
> 
>  Message-id: <AE2D3494-EBD3-441B-927C-121E58C8032E@mac.com>
>  Date: Tue, 07 Jun 2011 12:19:33 +1000
>  From: Denis Tebbutt <denistebbutt@mac.com>
>  To: Leo List <poldi@zudiewiener.com>,
>  Subject: Fwd: Scientific proof !
> 
> Your message cannot be delivered to the following recipients:
> 
>  Recipient address: [email]poldi@zudiewiener.com[/email]
>  Reason: Remote SMTP server has rejected address
>  Diagnostic code: smtp;550 5.1.1 <poldi@zudiewiener.com>: Recipient address rejected: User unknown in relay recipient table
>  Remote system: dns;mail1.no-ip.com (TCP|17.148.16.103|45561|204.16.252.100|25) (mail1.no-ip.com ESMTP)
> 
> Reporting-MTA: dns;asmtp028-bge351000.mac.com (tcp-daemon)
> Arrival-date: Mon, 06 Jun 2011 19:19:37 -0700 (PDT)
> 
> Original-recipient: rfc822;poldi@zudiewiener.com
> Final-recipient: rfc822;poldi@zudiewiener.com
> Action: failed
> Status: 5.1.1 (Remote SMTP server has rejected address)
> Remote-MTA: dns;mail1.no-ip.com (TCP|17.148.16.103|45561|204.16.252.100|25)
> (mail1.no-ip.com ESMTP)
> Diagnostic-code: smtp;550 5.1.1 <poldi@zudiewiener.com>: Recipient address
> rejected: User unknown in relay recipient table
> 


---------------------------------------

Appreciate any theories or solutions

Thanks

---

