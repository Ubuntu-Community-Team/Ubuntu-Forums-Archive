---
title: "Posftix : local mail and external"
date: 2015-05-08
forum: Server Platforms
---

### Post by jean-pierre2 on 2015-05-08
Hello,

I want to configure my home ubuntu server (named srv0) to send emails to local users AND to external internet address.
Note that I do not want to receive emails from internet. 

First, I made a configuration for a local user to send to a local user and it works fine :
```
# main.cf 
...
myhostname = localhost
mydomain = localdomain
relayhost =
...
```


Second configuration works for a local user to send an email to an internet address (azerty@gmail.com for ex) as I use the provider of my web site :
```
# main.cf
...
myhostname = srv0.xyz.net
mydomain = xyz.net
myorigin = $mydomain
relayhost = [ssl0.ovh.net]
...
#SASL config...
```

But from now, a local user cannot send any more an email to another local user. Postfix uses the relayhost and append my domain in the address (as configured).

I tried to change some config (from different posts) but it does not work and I do not understand. 

Is it possible to do as I intend ? How postfix can simply send email to local user and uses the relay when needed ?

Regards.

JP

---

### Post by jean-pierre2 on 2015-05-08
I should have added this for both configs : ```
mydestination = $myhostname, localhost.$mydomain, localhost
```

In mail.log, the common error is : ```
552 sorry, your envelope sender domain must exist [mail188] (#5.7.1) (in reply to MAIL FROM command))
```
From what I understand :
- for local mail, I must not have a domain for the user, otherwise it goes outside
- to internet mail, local user must have a valid domain name, to be allowed to send email by my provider
How ?!?

---

### Post by darkod on 2015-05-08
Why do you intend to use relayhost? Local postfix even if it's in home network behind your isp router is able to send emails outside. It will not be able to receive unless you do necessary config for that but you say you are not interested in sending.

---

### Post by SeijiSensei on 2015-05-08
Most providers of residential Internet services block outbound traffic to port 25 to thwart spambots on their networks.  He may be required to use the relay server.

---

### Post by jean-pierre2 on 2015-05-09
I re-read Posfix documentation.
And what I have not understood or configured badly first time, then it worked !

```
# main.cf
smtp_generic_maps = hash:/etc/postfix/generic
myhostname = srv0.localdomain.local
mydomain = localdomain.local
myorigin = $myhostname
```

```
# generic
user1@srv0.localdomain.local             extuser@xxxxxx.net
```

Then, run commands :
```
postmap /etc/postfix/generic
service postfix restart
```

Thanks.

JP

@darkod : yes, relayhost is required in my config

---

