---
title: "SMTP server not relaying properly..."
date: 2012-01-26
forum: Server Platforms
---

### Post by gunthr on 2012-01-26
Greetings!

I'm getting an error when trying to relay mail via No-IP's SMTP relay (I have a dynamic IP address).

```
Jan 26 17:43:14 horde postfix/smtp[9856]: 3B2A9821F1: to=<me@gmail.com>, relay=smtp-auth.no-ip.com[8.23.224.63]:587, delay=1.7, delays=0.8/0.02/0.74/0.1, dsn=5.7.1, status=bounced (host smtp-auth.no-ip.com[8.23.224.63] said: 554 5.7.1 <me@gmail.com>: Relay access denied (in reply to RCPT TO command))
```

No-IP uses SMTP authentication, so I assume this is where the problem lies. I know that I can authenticate against this server because my webmail sends fine. However, anything not sent from the localhost can't send and gets that error, whether on the local network or a public network.

I commented out the *relayhost = smtp-auth.no-ip.com:587* parameter in /etc/postfix/main.cf and the mail server relays just fine.

Did I miss something where I needed to tell Postfix to use saslauthd when relaying for non-localhost clients? Any other ideas for what my problems is?

Thanks,
Mike

---

### Post by SeijiSensei on 2012-01-27
Is it possible that GMail doesn't accept messages sent from no-ip.com servers?  The IP address you show, 8.23.224.63, is listed at [SORBS]("http://www.sorbs.net/lookup.shtml"), for instance.  I would think services like no-ip attract a number of spammers.

---

### Post by gunthr on 2012-01-27
Thank you for the response.

I'm able to send mail via No-IP's relay service with the webmail interface, so I know that GMail is willing to accept mail from them. In the email header from mail sent via webmail, Google's server states > google.com: 8.23.224.61 is neither permitted nor denied by best guess record for domain of... So it appears that they don't care.

The reason I'm using No-IP's service is go get around the reverse DNS lookup issues associated with using a dynamic IP address. If I send without using the relay, GMail slams the mail into my spam folder.

In my (somewhat limited) mind, it appears that Postfix is relaying the mail using my smtpauth credentials from the client app versus using its own credentials. Therefore, failing to authenticate.

Thanks again for the response.

---

