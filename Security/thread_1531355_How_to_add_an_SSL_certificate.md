---
title: "How to add an SSL certificate?"
date: 2010-07-14
forum: Security
---

### Post by bdk6m2007 on 2010-07-14
I've been trying to track down the standard way to add new SSL certificates to a ubuntu server.  Through googling I'm pretty confused if it's OK just to drop a file in /etc/ssl/certs or if I need to use the ca-certificates package to add in my certificate so that the system knows it's there.  Can someone clarify a bit for me?

---

### Post by Bachstelze on 2010-07-14
"The system", whatever you mean by that, doesn't need to know about your certificate.  Only the actual server (i.e. daemon) does, and all of them have a directive in their config files where you can enter the path to the SSL cert.

---

### Post by anomie on 2010-07-15
[QUOTE=bdk6m2007]Can someone clarify a bit for me?[/QUOTE]

What are you doing, exactly? Is this for Apache, Squid, or something else?

---

### Post by bdk6m2007 on 2010-07-15
I'm just trying to install a public certificate for a browser to use for https authentication.  Figured it out.  In my case I'm using a webkit derivative and there's a way to tell it where to find certificates via a config file.

So in short, I can just put my file in /etc/ssl/certs and all is good.

---

### Post by anomie on 2010-07-15
I see. So you have a CA cert that was not included in your web browser. And now you've added it. 

In addition to the method you used, I believe most browsers will allow you import the CA cert.

---

