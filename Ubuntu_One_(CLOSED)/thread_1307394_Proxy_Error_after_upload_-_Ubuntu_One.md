---
title: "Proxy Error after upload - Ubuntu One"
date: 2009-10-31
forum: Ubuntu One (CLOSED)
---

### Post by vinohymi@gmail.com on 2009-10-31
Hi,

I tried to upload 2 MB file, where it taken 5 min to upload. After sometime i got the below error.

**Proxy Error**

 The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request *[POST /upload/]("https://files.one.ubuntu.com/upload/")*.
 Reason: **Error reading from remote server**
  Apache/2.2.8 (Ubuntu) mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.8 OpenSSL/0.9.8g Server at files.one.ubuntu.com Port 443

I confirmed the file uploaded by opening in new tab browser.

Is this the actual behavior?

Vino:KS

---

### Post by vinohymi@gmail.com on 2009-10-31
I tired again to replicate the same issue. But failed.

May be it is a intermittent issue;)

---

### Post by joshuahoover on 2009-11-02
> **vinohymi@gmail.com said:**
> I tired again to replicate the same issue. But failed.

May be it is a intermittent issue;)

This is a server side error that you should not get. If it happens again, please report a bug here: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug) We've been enhancing the server side but apparently still have a few bugs to work out, even if they are intermittent. 

Thank you,

Joshua

---

### Post by oppih on 2010-03-13
I have quesiton about Ubuntuone and proxy. Dose Ubuntuone support proxy connection? I'm currently in a ntework that have to use proxy to connect to outside. When I started Ubuntuone the first time, it took a long time to give me a message : Connection failed. And I cannot find where I can use proxy for Ubuntuone, except Preferences --> Network Proxy.

---

### Post by joshuahoover on 2010-03-15
> **oppih said:**
> I have quesiton about Ubuntuone and proxy. Dose Ubuntuone support proxy connection? I'm currently in a ntework that have to use proxy to connect to outside. When I started Ubuntuone the first time, it took a long time to give me a message : Connection failed. And I cannot find where I can use proxy for Ubuntuone, except Preferences --> Network Proxy.

This is a popular question/request. I thought we had an FAQ for it already but it turns out we don't, so I added one: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/1006](https://answers.edge.launchpad.net/ubuntuone-client/+faq/1006) Short answer: no proxy support. Slightly longer answer: We're looking at adding support for 10.10. Depending on how difficult it is, we might be able to get it into our PPA version sooner than that. I'm making no promised on that one though. :-)

Thank you,

Joshua

---

