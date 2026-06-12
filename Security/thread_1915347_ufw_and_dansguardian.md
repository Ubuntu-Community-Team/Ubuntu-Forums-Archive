---
title: "ufw and dansguardian"
date: 2012-01-26
forum: Security
---

### Post by sythe on 2012-01-26
Hello,

I want to use dansguardian as a content filter with squid. I also want to block all outgoing internet traffic except on port 8080, so that users cannot circumvent the content filter by turning off the proxy settings in their browser. However, when I do this using ufw it basically blocks all outgoing internet traffic even if I allow specific ports. Here is the result of ufw status verbose:

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
25,53,110,443,8080/tcp     ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere

What exactly am I missing here? Thanks in advance for any help.

---

### Post by bodhi.zazen on 2012-01-26
See:

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

You will need to adjust to your network and proxy configuration, but that should point you in the right direction.

---

### Post by sythe on 2012-01-27
Thank you for the reply. For some reason, when I go to the links that you posted I get a blank page. However, I did go to the following web page and that was able to help me out nicely. Thanks again!

[http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)

---

### Post by bodhi.zazen on 2012-01-27
/me checks server - my pages are up here, sorry you had a problem with it.

---

### Post by sythe on 2012-01-29
No problem. Those are great howto's by the way!

---

### Post by bodhi.zazen on 2012-01-30
> **sythe said:**
> No problem. Those are great howto's by the way!

Thank you , hope you are up and running now.

---

