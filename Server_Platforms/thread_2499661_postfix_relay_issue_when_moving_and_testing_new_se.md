---
title: "postfix relay issue when moving and testing new server"
date: 2024-08-06
forum: Server Platforms
---

### Post by lister171254 on 2024-08-06
I'm running postfix 3.8.6 on Ubuntu 24.04 LTS and am in the process of moving my existing postfix/dovecot mail server to a different machine.
During testing I'm running the two servers in parallel (stopping dovecot and postfix on the old server)

While I managed to configure dovecot on the new machine, I found a problem with getting postfix to send emails.

Please note that the ip address of the old server in this example and log is yyy.yyy.yyy.yyy while the new server is xxx.xxx.xxx.xxx

Part of my main.cf file looks like this;

```
newhostname = newhost.mydomain.com
mydomain = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $newhostname, localhost.$mydomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 127.0.0.1, ::1, yyy.yyy.yyy.yyy
inet_protocols = all

non_smtpd_milters = inet:localhost:11332

smtp_dns_support_level = dnssec
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtpd_client_restrictions = permit_mynetworks
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks
        reject_invalid_helo_hostname
        reject_non_fqdn_helo_hostname
smtpd_milters = inet:localhost:11332
smtpd_relay_restrictions = reject_non_fqdn_recipient
        reject_unknown_recipient_domain
        permit_mynetworks
        reject_unauth_destination
virtual_transport = lmtp:unix:private/dovecot-lmtp
```

The log shows that the new server receives emails:
```
2024-08-06T07:04:36.486230+00:00 newhost postfix/postscreen[7551]: CONNECT from [209.85.160.181]:50323 to [xxx.xxx.xxx.xxx]:25
2024-08-06T07:04:42.485271+00:00 newhost postfix/postscreen[7551]: PASS NEW [209.85.160.181]:50323
2024-08-06T07:04:42.761013+00:00 newhost postfix/smtpd[7552]: connect from mail-qt1-f181.google.com[209.85.160.181]
2024-08-06T07:04:43.559162+00:00 newhost postfix/smtpd[7552]: 876924C1230: client=mail-qt1-f181.google.com[209.85.160.181]
2024-08-06T07:04:43.591415+00:00 newhost postfix/cleanup[7559]: 876924C1230: message-id=<CADNR+cBh=ac8_pG+abT33Gzt69FqRJg1eWM9T-wHkhPOP+cY0A@mail.gmail.com>
2024-08-06T07:04:45.127966+00:00 newhost postfix/qmgr[7361]: 876924C1230: from=<bob@gmail.com>, size=2969, nrcpt=1 (queue active)
2024-08-06T07:04:45.211336+00:00 newhost postfix/smtpd[7552]: disconnect from mail-qt1-f181.google.com[209.85.160.181] ehlo=2 starttls=1 mail=1 rcpt=1 bdat=1 quit=1 commands=7
2024-08-06T07:04:45.347032+00:00 newhost postfix/lmtp[7561]: 876924C1230: to=<adm@mydomain.com>, relay=newhost.mydomain.com[private/dovecot-lmtp], delay=1.9, delays=1.6/0.04/0.09/0.11, dsn=2.0.0, status=sent (250 2.0.0 <adm@mydomain.com> +molDg3LsWaKHQAAqrKISg Saved)
2024-08-06T07:04:45.348091+00:00 newhost postfix/qmgr[7361]: 876924C1230: removed
```

This log shows the relay failure and it maybe obvious as to why; the connect comes from the old server address.
Not sure why that is?
```
2024-08-06T07:15:15.601428+00:00 newhost postfix/submission/smtpd[7678]: connect from yyy-yyy-yyy-yyy.b49608.syd.static.aussiebb.net[yyy.yyy.yyy.yyy]
2024-08-06T07:15:23.670486+00:00 newhost postfix/submission/smtpd[7678]: NOQUEUE: reject: RCPT from yyy-yyy-yyy-yyy.b49608.syd.static.aussiebb.net[yyy.yyy.yyy.yyy]: 554 5.7.1 <leoinaustria54@gmail.com>: Relay access denied; from=<adm@mydomain.com> to=<leoinaustria54@gmail.com> proto=ESMTP helo=<[192.168.1.9]>
2024-08-06T07:15:23.994373+00:00 newhost postfix/submission/smtpd[7678]: lost connection after RCPT from yyy-yyy-yyy-yyy.b49608.syd.static.aussiebb.net[yyy.yyy.yyy.yyy]
2024-08-06T07:15:24.004039+00:00 newhost postfix/submission/smtpd[7678]: disconnect from yyy-yyy-yyy-yyy.b49608.syd.static.aussiebb.net[yyy.yyy.yyy.yyy] ehlo=2 starttls=1 auth=1 mail=1 rcpt=0/1 commands=5/6
```

---

### Post by lister171254 on 2024-08-06
On further investigation it turns out the yyy... is my service provider

---

### Post by lister171254 on 2024-08-06
I changed smtpd_relay_restrictions
```
smtpd_relay_restrictions = reject_unknown_recipient_domain
        permit_mynetworks
        permit_sasl_authenticated
        reject_unauth_destination

```

and sending emails now works

---

