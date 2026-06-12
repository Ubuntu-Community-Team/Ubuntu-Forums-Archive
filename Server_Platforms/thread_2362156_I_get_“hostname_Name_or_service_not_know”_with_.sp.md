---
title: "I get “hostname: Name or service not know” with .space TLD"
date: 2017-05-24
forum: Server Platforms
---

### Post by surfblue714 on 2017-05-24
Hello,
My apologies first off if this is the incorrect forum, however I categorize this somewhere between Ubuntu Server 16.04 or Networking. So hopefully the former over the latter is closer. My issue in question is that I am attempting to install Virtualmin on Ubuntu Server 16.04.2, which requires a FQDN, however  before I can even begin the installation it requires setting the  hostname to said FQDN. I currently set it to sub.domain.space but it  seems to return "hostname: Name or service not know", are new TLDs just  not supported or a bad idea? Thanks to all those who reply / highest  gratitude to all those who offer assistance!
:D

---

### Post by bullet2021 on 2017-05-24
Hey,

You may have to set it to a hostname during the installation and then later change it via /etc/hosts.
Here is a link on how to do it, its old but should still apply.
[https://www.digitalocean.com/community/questions/how-to-set-fqdn-in-ubuntu](https://www.digitalocean.com/community/questions/how-to-set-fqdn-in-ubuntu)
Otherwise, there are plenty of other links on google :).

---

