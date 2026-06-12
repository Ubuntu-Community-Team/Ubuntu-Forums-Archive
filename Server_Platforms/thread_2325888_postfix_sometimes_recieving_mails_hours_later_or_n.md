---
title: "postfix: sometimes recieving mails hours later or not at all"
date: 2016-05-26
forum: Server Platforms
---

### Post by lukas34 on 2016-05-26
Hiho,
sometimes when sending to one of my email accounts, the mail is received hours later or not at all. In both cases mail.log tells me:
```
to=<ulrich.wiener@marketstrategy.de>, relay=none, delay=2.7, delays=2.7/0.01/0/0, dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
```

Sometimes I get this error as well:
```
... postfix/smtp[10816]: 8F7E1462745: to=<www-data@hetzner.marketstrategy.de>, relay=none, delay=0.05, delays=0.04/0/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=hetzner.marketstrategy.de type=AAAA: Host not found)
```

mail.err shows nothing.
hetzner.marketstrategy.de is my fqdn, its set in hostfile and in main.cf correctly
99% of mails are received correctly in time. I really don't know where to start...

luggie

---

