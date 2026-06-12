---
title: "[SOLVED] New POP/IMAP-server installation"
date: 2008-02-28
forum: Server Platforms
---

### Post by qrwe on 2008-02-28
Hello!

I'm configuring a new server. As I've used Gentoo before and wanted to change environment, I decided to give Ubuntu Server a try.
Last time, I used [this guide from the Gentoo community]("http://www.gentoo.org/doc/en/virt-mail-howto.xml") to configure the server. My problem now is when I come to section "4. Cyrus-sasl", there is no (or should I say too many) downloads available with that name. Does anyone know which one is the correct for my needs?
Thanks!

---

### Post by ruy_lopez on 2008-02-28
I had trouble finding an ubuntu cyrus-sasl package. In the end, I installed it from source. It doesn't have too many dependencies. You should give the source a try. Get it [here.]("ftp://ftp.andrew.cmu.edu/pub/cyrus-mail")

---

### Post by qrwe on 2008-02-28
Thank you, but it's very strange that they have made cyrus-sasl unavailable. If I try e.g. cyrus-sasl-common, it says that the package is referred to another place. Is it unsecure or what?

---

### Post by Poleh on 2008-03-02
have you checked your repo's ? The package may be in a repo that you haven't enabled and hence can't be found. I find that this is most often the case when I get the old "this packaged is referred to by another package/in another place"

---

### Post by qrwe on 2008-03-07
Ah, that was it; thank you both!

---

