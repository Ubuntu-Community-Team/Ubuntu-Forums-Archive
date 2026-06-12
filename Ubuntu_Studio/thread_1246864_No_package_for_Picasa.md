---
title: "No package for Picasa?"
date: 2009-08-22
forum: Ubuntu Studio
---

### Post by mazadillon on 2009-08-22
I would like to install picasa for linux, is there a reason why it is not available in the ubuntu package repository? If there isn't a valid reason how does one go about adding it?

---

### Post by amac777 on 2009-08-22
I donwnloaded and installed picasa3 from google directly and it works great.

[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by Stochastic on 2009-08-23
> **mazadillon said:**
> I would like to install picasa for linux, is there a reason why it is not available in the ubuntu package repository? If there isn't a valid reason how does one go about adding it?

The reason why it's not in the Ubuntu repositories is because it isn't open source.

Here's a snippet of the Terms of Service from google > 9.1 You acknowledge and agree that Google (or Google’s licensors) own all legal right, title and interest in and to the Services, including any intellectual property rights which subsist in the Services (whether those rights happen to be registered or not, and wherever in the world those rights may exist). You further acknowledge that the Services may contain information which is designated confidential by Google and that you shall not disclose such information without Google’s prior written consent.

9.2 Unless you have agreed otherwise in writing with Google, nothing in the Terms gives you a right to use any of Google’s trade names, trade marks, service marks, logos, domain names, and other distinctive brand features.


Normally though (if it was open sourced) to get a package added the first step is to file a bug in Launchpad.net that request it to be packaged (like these: [https://bugs.launchpad.net/ubuntu/+bugs?field.tag=needs-packaging](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=needs-packaging)).  The second, is to begin packaging it yourself, and for that I'd start reading here: [https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)

---

