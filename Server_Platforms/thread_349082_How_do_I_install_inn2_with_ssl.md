---
title: "How do I install inn2 with ssl?"
date: 2007-01-29
forum: Server Platforms
---

### Post by fellgoog on 2007-01-29
Hello fellow ubuntu users,
(disclaimer: I'm fairly new to linux. Please don't flame :)

I have a fresh install of ubuntu 6.06 server with the packages inn2, inn2-ssl and all dependencies. What I want to set up is the following:

- have an isolated news server (inn2) that accepts only ssl connections
- limit access to users with some username and password combo
- do NOT pull any news from other servers

When I installed the packages, the server itself worked fine except for the encryption. After reading some man pages and scouring the ubuntu forums and howtos, I'm still lost at this point:

- how do I get inn2-ssl started and running?
- do I have to install inetd in order to start ssl connections?

Thanks for any answers!

---

### Post by fellgoog on 2007-02-06
Okay, in case anyone else wants to know:

- the ssl component (nnrpd-ssl) is either started as a daemon with the "-D" flag, from the command line or an rc script of your liking
- it can also be started by inet.d, just have a look at /usr/share/doc/inn2-ssl/README.Debian

- getting the encryption to work requires generating a certificate file, dropping it somewhere (perferably /etc/news) and then directing /etc/sasl.conf there, like

tls_ca_path:    /etc/news
tls_cert_file:  /etc/news/cert.pem
tls_key_file:   /etc/news/cert.pem

At this point, ssl connections to the news server will work, yet still without authentification.
Cheers

---

