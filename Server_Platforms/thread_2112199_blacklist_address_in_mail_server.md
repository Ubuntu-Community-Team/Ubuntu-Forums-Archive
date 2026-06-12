---
title: "blacklist address in mail server"
date: 2013-02-04
forum: Server Platforms
---

### Post by Elnison on 2013-02-04
hey guys
i'm just wondering if no-ip.org is blacklisted in yahoo or gmail.
because when I tried to send an email I get this message on /var/log/mail.log
```
mail postfix/smtp[3076]: 1493D1002E8: to=<user@yahoo.com>, relay=none, delay=3205, delays=3048/0.25/156/0, dsn=4.4.1, status=deferred (connect to mta5.am0.yahoodns.net[98.138.112.38]:25: Connection timed out)
```
thanks!

---

### Post by SlugSlug on 2013-02-04
Are you sending emails straight out to DNS or using a relay?

If your on a home internet (normally DHCP) then most email servers will block you. You need to use your ISP's email relay if they allow it or find an alternative.

I've used authsmtp in the past

---

### Post by volkswagner on 2013-02-04
As SlugSlug pointed out if your internet connection is a dynamic ip you may be blacklisted.

Check [mxtoolbox.com]("http://www.mxtoolbox.com/") against your domain name.

For example my dynamic ip is listed on SORBS list.  


From mxtoolbox.com:
> ...SORBS also lists servers with dynamically allocated IP addresses

---

### Post by Elnison on 2013-02-08
i've already bought a domain name at godaddy.com
and my ip address is static but still connection timed out appears

---

### Post by SlugSlug on 2013-02-08
Do go daddy offer email relay often called smart host.
You'll need to relay your mail through a trusted server

---

### Post by volkswagner on 2013-02-08
> **Elnison said:**
> i've already bought a domain name at godaddy.com
and my ip address is static but still connection timed out appears

Did you check your domain and static ip using the mxtoolbox.com mentioned above?  What were the results?

Even if you have a static ip, the previous user of that ip could have caused the black listing.

You also need to verify your reverse dns is setup.  You can use [dnsgoodies.com]("http://www.dnsgoodies.com/") for this.  Your reverse dns should show the FQDN of your mail server.

When you run the host and dig command on your domain do you get expected results?

---

### Post by Elnison on 2013-02-10
how can I change the reverse dns? it shows in [dnsgoodies.com]("dnsgoodies.com") that I have 199.15.255.232

---

