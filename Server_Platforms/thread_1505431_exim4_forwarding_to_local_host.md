---
title: "exim4 forwarding to local host"
date: 2010-06-09
forum: Server Platforms
---

### Post by Nunners on 2010-06-09
I've recently had to rebuild our mail server - after the old one over heated - and I've realised I never backed up the config files for exim... so now tyring to work out how the hell to configure what I had....

The setup isn't the most straight forward, so I'll try and explain what happens...

- all emails @longdomain.com are received by an hosted server on the internet
- they are then forwarded to @shortdomain.com, the IP for which is our internet connection which fowards port 25 traffic to the exim server
- the exim server then spam and virus checks the emails and forwards them to an exchange server (sorry but it works well for us)....

I've installed exim4/spamassassin/clamav successfully, and it's setup to receive emails for the relevant domains and relay from the hosted server on the internet (and some local addresses).

Can anyone remind me how I then setup exim4 to foward all emails on the relevant domains to the exchange server?  That's where I'm stuck...

Cheers
Nunners

---

### Post by nbkr on 2010-06-09
According to an howto i founc at [http://www.tgunkel.de/docs/exim_smarthosts.de](http://www.tgunkel.de/docs/exim_smarthosts.de) (German website) you can forward emails to another mailserver according to their sender address. I'm not sure, but I think you can modify the following configuration to match the address to the recipents address.

```
smarthost_alpha:
   condition = ${if eq {${lc:$sender_address_domain}} {example.com} {true} fail }
   driver = domainlist
   transport = remote_smtp
   route_list = "* mail.example.com bydns_a"
```

HTH
nbkr

---

### Post by Nunners on 2010-06-09
Thanks for the link... but unfortunately my german isn't up to much - in fact nothing at all...

Where would the smarthost_alpha line need to go?

---

### Post by Nunners on 2010-06-09
I think one of the confusing things is I'm using the update-exim4.conf setup... and my solution isn't going to be that straight forward?

So I'm probably going to need to edit all the conf.d/main files?

Again, any help gratefully received....

---

### Post by nbkr on 2010-06-09
There should be a exim4.conf. The code needs to get into that file.

---

### Post by Nunners on 2010-06-09
I'm fairly certain that because of the way I've installed it - using apt-get - and also because I've included clamav and spamassassin, there is an automatic configurator... which has things working so far....!

---

### Post by warlockvix on 2010-07-02
I too lost my sa and clamav server and am trying to bring it back up. Same setup as you have as well. Did the "smarthost_alpha" work for you or did you use the automatic configuration utility you spoke of?

And depending on which one worked, what did you do? 

Thanks!

---

