---
title: "Postfix: Any way to prevent spam relay with mynetworks open?"
date: 2009-05-10
forum: Server Platforms
---

### Post by tdcdodger on 2009-05-10
Hello and Happy mother's day.

I rent an ubuntu VPS, hosted out in CA somewhere. I want to use this computer as the mail server for my domain (postfix: SMTP and courier: IMAP). It is tricky because this computer is NOT at the 'top' of my network.

Issues arise with the 'mynetworks' parameter of the postfix configuration.

The mail system works fine, however I believe I am exposed to spammers. In order for the mail server to act as a relay server from my mobile clients (my cell phone), I needed to open up the mynetworks parameter to:

mynetworks = 0.0.0.0/256

Unfortunatley, the other mobile clients do NOT have static IPs, so I cannot append their address to this parameter.

I understand that this is highly insecure. I am wondering what other appraoches I can take to opening up relay access to my mobile clients.

Will an implementation of SASL 'lockdown' SMTP?

Thank you in advance.

---

### Post by ejschaefer on 2009-05-10
Hello, 

You will definitely need to implement SASL and remove the mynetworks configuration that you have. Leaving your server as an open relay will ensure that you are blacklisted very quickly. Any mail client that is worth using will support SMTP authentication. 

How Postfix uses SASL authentication information
[http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html)

Let me know if you run into any trouble.

---

### Post by tdcdodger on 2009-05-11
Thank you for your replies, I will look into some form of SASL authentication

---

### Post by adaniels on 2009-05-11
Don't put the whole world in mynetworks. The purpose of that setting is to bypass other security settings like throttling and authentication.

To relay for your network + SASL authenticated clients use something like:
```

smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject

```

To bruteforce attacks make sure you set smtpd_soft_error_limit and smtpd_client_connection_rate_limit. Also look at [http://www.postfix.org/anvil.8.html](http://www.postfix.org/anvil.8.html)

---

### Post by Dr Small on 2009-05-11
You can check out my guide for SASL authentication for securely relaying mail with Postfix:
[http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582)

---

