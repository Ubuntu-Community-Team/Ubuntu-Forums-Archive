---
title: "Root Certificate"
date: 2011-05-10
forum: Server Platforms
---

### Post by Jibekn on 2011-05-10
Ok, I know there's a simple answer, and I cant find it, maybe I just don't know the proper term to search with. Or ive just been up too late.

I have a mail server.

It works great.

It uses a self signed certificate for TLS

How do i export the root authority cert file that a win machine can import?

this is so when the win box uses TLS, outlook wont complain.

Thank you in advanced.

---

### Post by BkkBonanza on 2011-05-10
You will need to export a PK12 format (public) cert for the one that you used to sign your email server cert. There's quite a few tutorials on this easy to find with google but the command line options can often be confusing to get just right.

I use and recommend TinyCA - this is a gui frontend for openssl that gives you a smart visual manager for running a small CA of your own. It allows you to create a CA cert, create server and client certs and also easily export them in various common formats needed for your email client or browsers.

---

### Post by hawkmage on 2011-05-11
If you have a self signed certificate there is not "ROOT" cert, there is only the host certificate.  If you import and trust the host certificate you should be OK.  One thing you need to be aware of is that the CN in the subject of the certificate has to match the name by which you refer to the host by.

---

