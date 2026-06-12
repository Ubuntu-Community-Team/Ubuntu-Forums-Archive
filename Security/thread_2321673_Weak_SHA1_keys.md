---
title: "Weak SHA1 keys"
date: 2016-04-23
forum: Security
---

### Post by dean-westray on 2016-04-23
I have come across an issue when I have added the repositories from Oracle (for Virtualbox) and Google (for Chrome) to my new 16.04LTS install.   When I've run the apt-get update command, I'm getting this message advising the following (truncated to avoid displaying the key finger print).

[B]> W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key (removed) uses weak digest algorithm (SHA1) 


[/B]Please can some one advise me it if this a major security issue with both Oracle and Google using old or invalid gpg keys, or false positives due to security changes within 16.04LTS itself? 

Note I've un-installed both Chrome and Virtualbox respectively, and now only using the edition of Virtualbox from Canonical's own repositories.

---

### Post by PaulW2U on 2016-04-24
> **dean-westray said:**
> Please can some one advise me it if this a major security issue with both Oracle and Google using old or invalid gpg keys, or false positives due to security changes within 16.04LTS itself?
I think it's more to do with Ubuntu 16.04 LTS being supported until 2021 and the fact that a lot can change before support stops.

The following blog post explains why you are seeing these warnings: [Dropping SHA-1 support in APT](https://juliank.wordpress.com/2016/03/14/dropping-sha-1-support-in-apt/).

---

### Post by dean-westray on 2016-04-25
Thanks for your reply Paul.  
If I ask a further question (after reading the blog post).  Is it fair to say that I should hold fire installing Virtualbox & Chrome until both Oracle and Google have updated to using SHA256, or indeed SHA512 gpg keys?

---

