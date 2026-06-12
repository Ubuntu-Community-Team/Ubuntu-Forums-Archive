---
title: "[SOLVED] Postfix With SMTP-AUTH And TLS"
date: 2008-07-18
forum: Server Platforms
---

### Post by sp0nge on 2008-07-18
In my continued quest for getting this server set up, I have been working to install and config postfix. I have installed with no problem, but the config should be: 

```
postconf -e 'smtpd_sasl_local_domain ='
postconf -e 'smtpd_sasl_auth_enable = yes'
postconf -e 'smtpd_sasl_security_options = noanonymous'
postconf -e 'broken_sasl_auth_clients = yes'
postconf -e 'smtpd_sasl_authenticated_header = yes'
postconf -e 'smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination'
postconf -e 'inet_interfaces = all'
echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
echo 'mech_list: plain login' >> /etc/postfix/sasl/smtpd.conf
```

But when I do:
```
postconf -e 'smtpd_sasl_local_domain ='
```

the next line looks like this: 
```
>   
```

so I thought I did it right, I continued: 
```
postconf -e 'smtpd_sasl_auth_enable = yes'
```

which returned the error: 
```
postconf: fatal: edit accepts no multi-line input
```

What am I doing wrong?

---

### Post by hyper_ch on 2008-07-19
just add it manually then to the postfix config.

---

### Post by sp0nge on 2008-07-19
FYI- 

This is simply oversight on my part. I was missing something when entering the commands. I was able to ssh into the server and cut and paste the commands to ensure accuracy. I guess staring at the screen all day has taken a toll on my eyes.

---

