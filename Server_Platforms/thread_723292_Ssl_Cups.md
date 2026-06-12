---
title: "Ssl Cups"
date: 2008-03-13
forum: Server Platforms
---

### Post by burnclouds on 2008-03-13
I have cups setup and configured for my local network. I'd like to be able to forward port 631 (or similar) from the internet to my CUPS server. Then setup my windows/linux laptops to be able to print from anywhere in the world (yes, I have static IP and a domain name). My trouble is that I have know idea how to modify cusd.conf for ssl and how to create the ssl certs and then configure my clients. Does any one know how to do this?

---

### Post by burnclouds on 2008-03-13
bump

---

### Post by burnclouds on 2008-03-13
finally found my answer.
the key was held at:
[http://www.cse.ust.hk/~lkmpoon/linux/ubuntu-hkust.html]("http://www.cse.ust.hk/~lkmpoon/linux/ubuntu-hkust.html")

I have made a shorter, updated and more general HOWTO:
[http://www.burnclouds.net/linux?blogid=0027]("http://www.burnclouds.net/linux?blogid=0027")

---

