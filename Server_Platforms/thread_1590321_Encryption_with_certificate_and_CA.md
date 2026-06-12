---
title: "Encryption with certificate and CA"
date: 2010-10-07
forum: Server Platforms
---

### Post by megabuffen on 2010-10-07
I have a server with Apache2 and I would like to use encryption to prevent eavesdropping POST requests and similar. I've had success using SSL with a self-signed certificate, but this will of course generate huge warnings from the web browser. It's no problem for me when I'm connecting to the server as I know what to expect, but any other user who sees such a warning will surely leave the site unless I have personally explained the procedure.

Is there really no way to encrypt HTTP without having to use certificates? I know that this is supposed to provide security by identifying the server, but my point is that an encrypted connection without a CA would in no way be inferior to one that sends passwords as plain text. All I want to do is prevent people who are using programs such as Cain or any other packet sniffer from getting their hands on my passwords. I'm not exactly running an online bank system here. Can this be done? Why does it have to be so complicated?

---

### Post by druhboruch on 2010-10-07
CAcert.org allows you to get free certificates.
There is a but... these certificates are not trusted by all browsers.

---

### Post by BkkBonanza on 2010-10-08
[Startcom]("http://www.startssl.com/") also has free certificates and they are actually recognized by browsers whereas CACert aren't (I've used both).

The cheapest place I've seen for full paid certificates is [Servertastic]("https://www.servertastic.com/rapidssl/") at $13.95. I bought one of these without problems.

You don't really have a choice other than using certificates they way things are set up now. You could probably concoct something but it wouldn't be easy for users and probably worse than using self-signed certificates.

---

### Post by megabuffen on 2010-10-08
I've tried Startcom, the problem is that I have a subdomain, which isn't supported. It seems I'll just have to stick with my self-signed certificate. At least I can add an exeption in my browser so that I can access phpMyAdmin securely.

---

