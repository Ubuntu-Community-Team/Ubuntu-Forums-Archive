---
title: "amavis-new and dkim woes"
date: 2013-08-30
forum: Server Platforms
---

### Post by CharlesA on 2013-08-30
Hello,

I have set up my mail server with spamassassin/clamav and amavis-new. I can send mail just fine and it passes thru the filter and checks for spam and viruses just fine.

My problem is that I am having problems getting amavis to sign outgoing messages with the DKIM key.

I followed [this tutorial]("https://help.ubuntu.com/12.04/serverguide/mail-filtering.html") when I setup spamassassin and such, and most of the stuff I have found online tell you to do something like this:
[http://www.linuxquestions.org/questions/linux-server-73/how-to-dkim-sign-emails-by-amavisd-new-839526/#post4273746](http://www.linuxquestions.org/questions/linux-server-73/how-to-dkim-sign-emails-by-amavisd-new-839526/#post4273746)

The only thing is - I am not sure how that would work with my configuration, as I am using port 10024 and 10025 to pass mail to amavis.

Any help is appreciated. So far I think I have hit a dead end, or I don't know enough about amavis to know what each configuration option does.

EDIT: So far I have added:

```
$enable_dkim_verification = 1;
$enable_dkim_signing = 1;
dkim_key("charlesa.net", "dkim", "/var/lib/amavis/dkim/charlesa.net.pem");
@dkim_signature_options_bysender_maps = (
    { '.' => { ttl => 21*24*3600, c => 'relaxed/simple' } } );
@dkim_signature_options_bysender_maps = (
    { '.' => { ttl => 21*24*3600, c => 'relaxed/simple' } } );
  @mynetworks = qw(0.0.0.0/8 127.0.0.0);  # list your internal network
```

To 50-user in amavis, but so far I have had little luck.

```
amavisd-new testkeys
TESTING#1: dkim._domainkey.charlesa.net      => pass

```

This works too, but it worked before adding anything extra to user-50. Not really sure what is going on.

---

### Post by CharlesA on 2013-09-01
Well, after much testing I found the answer/fix to the problem. I'm not sure if it's really the fix, but it gets amavis to sign outgoing mail with the DKIM key.

I found it off a french Debian wiki, here:
[https://www.isalo.org/wiki.debian-fr/Amavisd-new_et_DKIM](https://www.isalo.org/wiki.debian-fr/Amavisd-new_et_DKIM)

As far as I can tell the problem with mail not being sign was amavis didn't know where it was originating from, so it refused to do anything.

---

