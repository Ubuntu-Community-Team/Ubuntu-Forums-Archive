---
title: "Install uses local mirror instead main."
date: 2024-01-16
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-01-16
Today i installed from the new ISO and the install ended in error [https://bugs.launchpad.net/subiquity/+bug/2049491](https://bugs.launchpad.net/subiquity/+bug/2049491)
same error on bub: [https://bugs.launchpad.net/subiquity/+bug/2049486](https://bugs.launchpad.net/subiquity/+bug/2049486)
because installer uses the Italian mirror instead the main and the Italian mirror was syncing.

Jeremy Bicha wrote:

I looked through the attached logs and found that apt-get update has an error. (Same for the duplicate bugs except that the duplicate is using an Italian mirror instead of Iceland.)
E: Failed to fetch [http://is.archive.ubuntu.com/ubuntu/dists/noble/universe/binary-amd64/Packages](http://is.archive.ubuntu.com/ubuntu/dists/noble/universe/binary-amd64/Packages) File has unexpected size (15427304 != 15428288). Mirror sync in progress? [IP: 176.57.227.242 443]
Jan 16 06:48:21 ubuntu subiquity_log.2363[6528]: E: Some index files failed to download. They have been ignored, or old ones used instead.

so why installer uses the local mirror instead the main one?

---

### Post by jbicha on 2024-01-16
I believe Ubuntu's installer has used a local version of the Ubuntu archives for many years.

---

### Post by corradoventu on 2024-01-16
it has always been done this way is not a good reason to continue in a way that easily produces errors

---

### Post by jbicha on 2024-01-16
> **corradoventu said:**
> it has always been done this way is not a good reason to continue in a way that easily produces errors

I don't think the error you saw is more common with local mirrors.

---

