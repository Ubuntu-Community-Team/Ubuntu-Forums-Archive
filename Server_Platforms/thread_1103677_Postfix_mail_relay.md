---
title: "Postfix mail relay"
date: 2009-03-22
forum: Server Platforms
---

### Post by das7002 on 2009-03-22
I have two options that I can do and both are not working

Option 1: Configure postfix to relay mail to my Google Apps Account and then deliver from there

Option 2: Configure postfix to relay mail to another internal mail server that then sends it to Google for delivery (this one does not require any authentication)

Please can you assists I have spent hours trying to figure this out and have little experience in getting mail servers working since this is the first time I am having to do it any help is greatly appreciated

OS Intrepid Ibex 32bit

---

### Post by hyper_ch on 2009-03-23
I have this on one server to relay through the ISP there:

main.cf
```

smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
smtp_always_send_ehlo = yes
relayhost = [smtpauth.bluewin.ch]:587

```
Mail needs to be sent to port 587 that's why the ISP smtp server is in brackets.

Then saslpasswd looks like
```

smtpauth.bluewin.ch     USERNAME@EMAILDOMAIN.COM:PASSWORD

```

As this is a hashfile, you'll need to run
```

postmap saslpasswd

```

For google I think you need to get a certificate also.

---

### Post by windependence on 2009-03-23
> **das7002 said:**
> I have two options that I can do and both are not working

Option 1: Configure postfix to relay mail to my Google Apps Account and then deliver from there

Option 2: Configure postfix to relay mail to another internal mail server that then sends it to Google for delivery (this one does not require any authentication)

Please can you assists I have spent hours trying to figure this out and have little experience in getting mail servers working since this is the first time I am having to do it any help is greatly appreciated

OS Intrepid Ibex 32bit
I may not be able to help you here but I am very curious as to why you want to do this? Can you not get your mail from Google? And can't you just send mail straight from your mail server instead of relaying it through their SMTP servers? Help me to understand why anyone would want to do this.

-Tim

---

