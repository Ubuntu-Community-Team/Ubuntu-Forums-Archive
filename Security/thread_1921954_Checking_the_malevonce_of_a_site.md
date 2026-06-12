---
title: "Checking the malevonce of a site"
date: 2012-02-07
forum: Security
---

### Post by Resplendent Raven on 2012-02-07
Yesterday on Facebook i clicked a link however as soon as i clicked it i got secondthoughts about it, the link was taking quite long to load and i closed the window. The irony was that i was about to install NoScript and did soon after. Is there a way i can check if the site itself was malicious? The site was ho4l.info but i wouldn't recommend clicking it since i'm uncertain of it's nature

---

### Post by hansdown on 2012-02-07
Hi, Resplendent Raven.

It's actually 

link.ly

I would stay away, just my preference.

If you are using firefox, install

```
ghostery
```

---

### Post by OpSecShellshock on 2012-02-08
Yeah, any time a site asks you to sign on with another site's credentials, run away.

---

### Post by mr-woof on 2012-02-08
This seems to be a good site to check other sites :)

[http://www.urlvoid.com/](http://www.urlvoid.com/)

It seems to take a while to scan though.

---

### Post by unspawn on 2012-02-11
> **mr-woof said:**
> This seems to be a good site to check other sites :)
[http://www.urlvoid.com/](http://www.urlvoid.com/)
Good one. Next to that there's a host of sites that can run checks like
 
http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site={fqdn}
http://www.siteadvisor.com/sites/{fqdn}/summary/
http://www.projecthoneypot.org/search_ip.php?vid={ip}
http://www.pagesinventory.com/ip/{ip}.html
http://www.mywot.com/en/scorecard/{fqdn}
http://fspamlist.com/checkspammers/index.php?name=&email=&ip={ip}&submit=check
[http://www.unmaskparasites.com/](http://www.unmaskparasites.com/)
[http://www.maliciousnetworks.org/index.php](http://www.maliciousnetworks.org/index.php)
[http://www.stopbadware.org/home/reportsearch](http://www.stopbadware.org/home/reportsearch)

...but they're quite disparate in terms of data "freshness", what slice of the 'net they cover, what checks are performed and such. For instance I trust projecthoneypot to be more accurate than any WOT-like sites (because they allow input by people who aren't experts). OTOH while google covers a lot of the 'net it doesn't mean I trust it or siteadvisor blindly.

---

