---
title: "ssl cert just for me"
date: 2011-06-09
forum: Server Platforms
---

### Post by wlraider70 on 2011-06-09
when I access my router config from the internet I use https.mydyndns.org

Every time it tells me that I need to add the exception or something like that. I have to do this every time I visit the page.

Can I issue my own cert so that I don't have to do that every time?

---

### Post by jramshu on 2011-06-09
Sounds like it's not saving the exception for some reason. I got the warning once when I first logged on to my server and haven't got it since, using a self signed certificate. It's stored in my preferences.

---

### Post by wlraider70 on 2011-06-09
Hats what I think. I'm wondering if it's because I have no cert right now. So it's not saving anything. 

How do I make a cert.

---

### Post by ZuOverture on 2011-06-09
Try this:
[http://tldp.org/HOWTO/SSL-Certificates-HOWTO/index.html](http://tldp.org/HOWTO/SSL-Certificates-HOWTO/index.html)

---

### Post by Lars Noodén on 2011-06-09
You can get a free of charge certificate from [CAcert.org](http://www.cacert.org/)

---

### Post by jramshu on 2011-06-09
Interesting enough I get a certificate warning from that site. lol

> [www.cacert.org](www.cacert.org) uses an invalid security certificate.

The certificate is not trusted because the issuer certificate is unknown.

(Error code: sec_error_unknown_issuer)


So it seems he would get the same issues if they are not in the recognized cert list of the browser.

OP, have you tried to manually add it?

---

### Post by wlraider70 on 2011-06-09
I like the CA cert cite.

Here's my next issue that I didn't really think through at first. How do I get the ssl cert server up. Since I'm accessing the router (with limited options) does the router have to server the cert?

@jramshu no, do you think that would fix it? I have said add this exception and save or keep or whatever every time I get asked.

---

### Post by ZuOverture on 2011-06-10
> **wlraider70 said:**
> Since I'm accessing the router (with limited options) does the router have to server the cert?
This way could involve messing with router firmware. Look for certificate authority data - it may be either dyndns or router manufacturer related. Then you'll know who offers you encrypted connection. Both cases, of course, will require more complex solutions, than finding a way to store certificates.

---

### Post by wlraider70 on 2011-06-10
I'm familiar with dd-wrt and others but I don't really want to change my firmware.

Can you explain a little more for me.

Let me be clear on my setup just in case I haven't been.



I access my home router through a dyndns address. I told the router to connect though https (which I want to keep) However when I connect to the router through the internet it complains about the ssl cert. (there is NO cert)

*Now I see where I can get a cert, but what do I do with it when I have it.

---

