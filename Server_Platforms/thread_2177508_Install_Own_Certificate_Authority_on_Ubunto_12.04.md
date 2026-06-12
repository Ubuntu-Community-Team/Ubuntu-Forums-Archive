---
title: "Install Own Certificate Authority on Ubunto 12.04"
date: 2013-09-29
forum: Server Platforms
---

### Post by roeeshimrit on 2013-09-29
How can I Install my Own Certificate Authority on Ubunto 12.04 ?

thanks
ROee

---

### Post by TheFu on 2013-09-29
There is a script - CAcert.... something.
There are many different purposes to running a CA. Managing certs is the hard part.

If you say your purpose, then we might be able to recommend specific tools to help manage those certs.  Is this for HTTPS, gpg, openVPN, signing java packages  .... what is the purpose?  If the end users are highly technical, then you don't need as fancy an interface either.

I've seen the CAcert script installed ... I think it comes with openssl's installation and that is the back-end stuff you need to be a "CA", but far from being easy to use if you want/need to create more than a few certs.

---

### Post by sandyd on 2013-09-29
> **roeeshimrit said:**
> How can I Install my Own Certificate Authority on Ubunto 12.04 ?

thanks
ROee

Check out easy-rsa - contains all the scripts you need to setup and maintain a CA

---

### Post by hawkmage on 2013-09-30
There is a bit more to running your own CA than just signing certificates for clients.  First of all, how are you going to use them.  Second is who will need to trust them.  Third is how are you going to manage the private keys of your CA?  Forth, do you plan to have hierarchy CA certificates like most public CA's which usually include a Root, intermediary and issuing/sighing CA cert.

Personally in my home network I just use OpenSSL and do things manually but I do not need to worry about a bunch of clients or systems that need to trust and renew certificates.

---

