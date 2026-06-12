---
title: "Automatical redirection to a site that I don't know"
date: 2012-12-07
forum: Security
---

### Post by ZZBottom on 2012-12-07
Hi,

I'm Ubuntu user and at the moment worrying about the following incident:

I was on YouTube when I accidentally mistyped the address [www.youtube.com/](www.youtube.com/)... (was something like [www.syoutube.com/](www.syoutube.com/)...). Hereupon I was redirected to a site called "searchremagnifiedDOTcom" (I don't want anybody to accidentally click on the link, so I don't write it down)

After that I started to catch up on that site, and entered its URL at [http://sitecheck.sucuri.net/scanner/](http://sitecheck.sucuri.net/scanner/)
The result can be seen under
[http://sitecheck.sucuri.net/results/searchremagnified.com/](http://sitecheck.sucuri.net/results/searchremagnified.com/)
It has been blacklisted by some users of McAfee because of malware that's alledgly distributed by that site:
[http://www.siteadvisor.com/sites/searchremagnified.com/msgpage](http://www.siteadvisor.com/sites/searchremagnified.com/msgpage)
Google confirms this although they haven't blacklisted the site:
[http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=searchremagnified.com](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=searchremagnified.com)

So should I be worried? Should I reinstall everything?

Kind regards

---

### Post by chadk5utc on 2012-12-07
Thats a good question and first theng I would do is start searching the logfiles to see what if anything has happened or changed??

---

### Post by OpSecShellshock on 2012-12-07
I mistyped youtube in the same way and got the redirect to that domain. It was a blank page, but I have scripts blocked. Those kinds of typosquat domains could serve anything, but my best guess is it's a page with a bunch of third party ad content. That is often a means of delivering malware to Windows systems, but the risk for a desktop Linux user is low.

---

