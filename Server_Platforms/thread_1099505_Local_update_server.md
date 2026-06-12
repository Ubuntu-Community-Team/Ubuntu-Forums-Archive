---
title: "Local update server"
date: 2009-03-18
forum: Server Platforms
---

### Post by Gerritvm on 2009-03-18
Hi guys,

I would like to setup a local update server for all the ubuntu servers/workstations in our company network.

How do I go about doing this?

Thanks.

---

### Post by primaxx on 2009-03-18
> **Gerritvm said:**
> Hi guys,

I would like to setup a local update server for all the ubuntu servers/workstations in our company network.

How do I go about doing this?

Thanks.

Hi, 

maybe this answers your question:

[http://ubuntuforums.org/showthread.php?t=857749](http://ubuntuforums.org/showthread.php?t=857749)

Good luck! :)

---

### Post by lykwydchykyn on 2009-03-18
Check this out:
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

I've something similar set up at my office.  Works great, except that doing release upgrades (e.g. from 8.04 to 8.10) did not work with it without some tinkering (and even then it didn't always work).

---

### Post by HermanAB on 2009-03-18
If it is just a network load issue, then the easiest way to handle updates is to add a Squid-Cache proxy server.  Then you don't have to worry about it - Squid will cache all the downloads for you automatically.

Cheers,

Herman

---

### Post by Gerritvm on 2009-03-20
> **HermanAB said:**
> If it is just a network load issue, then the easiest way to handle updates is to add a Squid-Cache proxy server.  Then you don't have to worry about it - Squid will cache all the downloads for you automatically.

Cheers,

Herman

Thanks for the replies. Why did I not think about Squid!

---

