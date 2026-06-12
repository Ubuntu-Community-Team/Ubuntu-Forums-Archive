---
title: "Problem Postfix"
date: 2013-06-18
forum: Server Platforms
---

### Post by Tres_Iqus on 2013-06-18
I have problems receiving emails with some customers

In this example because the client sending mail from prueba.com and is using google mail services.
```

Jun  17 09:08:57 mail postfix/policyd-weight[25932]: weighted check:   NOT_IN_SBL_XBL_SPAMHAUS=-1.5 NOT_IN_SPAMCOP=-1.5 BL_NJABL=SKIP(-1.5)
IN_IPv6_RBL=4.25 CL_IP_EQ_HELO_IP=-2 
(check from: .prueba. - helo:  .mail-oa0-f47.google. - helo-domain: .google.)   
FROM/MX_MATCHES_NOT_HELO(DOMAIN)=2.062 CLIENT_NOT_MX/A_FROM_DOMAIN=5.75  CLIENT/24_NOT_MX/A_FROM_DOMAIN=5.75;
 <client=209.XXX.XXX.XXX>  <helo=mail-oa0-f47.google.com> <from=user@prueba.com>  <to=myuser@mydomain.com>; rate: 11.312

```

my main.cf
```

smtpd_helo_required          = yes

smtpd_helo_restrictions      = permit_mynetworks,
                               permit_sasl_authenticated,
                               reject_invalid_helo_hostname,
                               reject_non_fqdn_helo_hostname

smtpd_sender_restrictions    = reject_non_fqdn_sender,
                               reject_unknown_sender_domain,
                               permit_mynetworks,
                               permit_sasl_authenticated

smtpd_recipient_restrictions = reject_non_fqdn_recipient,
                               reject_unknown_recipient_domain,
                               permit_mynetworks,
                               permit_sasl_authenticated,
                               reject_unauth_destination,
                               reject_unlisted_recipient,
                    check_client_access hash:/etc/postfix/policyd_whitelist,
                               check_policy_service inet:127.0.0.1:12525,
                               check_policy_service inet:127.0.0.1:10023,
                               permit

```

thanks for you help.

best regards.

---

### Post by Tres_Iqus on 2013-06-18
Example mail.log 

```

Jun 18 17:56:41 mail postfix/smtp[28114]: 184B2126005F: to=<cliente@emisordecorreo.com>, relay=ASPMX.L.GOOGLE.com[74.125.140.26]:25, delay=4.6, delays=0.06/0.06/3.1/1.4, dsn=2.0.0, status=sent (250 2.0.0 OK 1371592480 g4si3954948yhd.336 - gsmtp)

Jun 18 17:57:34 mail postfix/policyd-weight[25932]: weighted check:  NOT_IN_SBL_XBL_SPAMHAUS=-1.5 NOT_IN_SPAMCOP=-1.5 BL_NJABL=ERR(-1.5) IN_IPv6_RBL=4.25 CL_IP_EQ_HELO_IP=-2 (check from: .emisordecorreo. - helo: .mail-wg0-f52.google. - helo-domain: .google.)  FROM/MX_MATCHES_NOT_HELO(DOMAIN)=2.062 CLIENT_NOT_MX/A_FROM_DOMAIN=5.75 CLIENT/24_NOT_MX/A_FROM_DOMAIN=5.75; <client=74.125.82.52> <helo=mail-wg0-f52.google.com> <from=cliente@emisordecorreo.com> <to=receptor@mi-servidor.correo.com1>; rate: 11.312

Jun 18 17:57:34 mail postfix/policyd-weight[25932]: decided action=550 Mail appeared to be SPAM or forged. Ask your Mail/DNS-Administrator to correct HELO and DNS MX settings or to get removed from DNSBLs; please relay via your ISP (emisordecorreo.com); <client=74.125.82.52> <helo=mail-wg0-f52.google.com> <from=cliente@emisordecorreo.com> <to=receptor@mi-servidor.correo.com>; delay: 7s

Jun 18 17:57:34 mail postfix/smtpd[28119]: NOQUEUE: reject: RCPT from mail-wg0-f52.google.com[74.125.82.52]: 550 5.7.1 <receptor@mi-servidor.correo.com>: Recipient address rejected: Mail appeared to be SPAM or forged. Ask your Mail/DNS-Administrator to correct HELO and DNS MX settings or to get removed from DNSBLs; please relay via your ISP (emisordecorreo.com); from=<cliente@emisordecorreo.com> to=<receptor@mi-servidor.correo.com> proto=ESMTP helo=<mail-wg0-f52.google.com>


```

---

### Post by lisati on 2013-06-18
Does emisordecorreo.com have proper DNS records? As far as I can tell, it doesn't, and that is causing policyd-weight to object.

---

### Post by Tres_Iqus on 2013-06-19
Apparently the sender of the mail clients have problems but they are valid, adding it to the whitelist should skip the policyd-weight?

---

### Post by Tres_Iqus on 2013-06-19
Other example:

mail.emisordecorreo.com    201.XXX.XXX.1
smtp.emisordecorreo.com   201.XXX.XXX.2

```

Jun 19 12:26:01 mail postfix/smtp[9743]: 0B71B126005F: to=<cliente@emisordecorreo.com>, 
        relay=smtp.emisordecorreo.com[201.XXX.XXX.2]:25, delay=3.4, 
        delays=0.54/0.01/0.04/2.8, dsn=2.0.0, 
        status=sent (250 Ok: queued as 90B6F2CA4F9)

Jun 19 12:27:06 mail postfix/policyd-weight[22342]: decided action=550 [cached]  Mail appeared to be SPAM or forged. Ask your Mail/DNS-Administrator to correct HELO and DNS MX settings or to get removed from DNSBLs - retrying too fast. penalty: 30 seconds x 0 retries.; <client=201.XXX.XXX.1> <helo=svexch1.dvma.local> <from=cliente@emisordecorreo.com> <to=receptor@miservidor.com>; delay: 0s

```

in this case my client has a domain and IP as SMTP and other domain and ip for mail

---

