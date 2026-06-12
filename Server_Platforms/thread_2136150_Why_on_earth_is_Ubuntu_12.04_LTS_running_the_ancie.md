---
title: "Why on earth is Ubuntu 12.04 LTS running the ancient php version 5.3.10???"
date: 2013-04-16
forum: Server Platforms
---

### Post by sneakyimp on 2013-04-16
I just did apt-get update/upgrade on my server running Ubuntu 12.04 LTS and noticed that PHP is *ancient*.  The latest version of php is 5.4.14.  The latest release of php 5.3 is 5.3.24.  *Why on earth* has canonical (or someone) not provided more up-to-date packages for PHP?  This is kind of ridiculous.

---

### Post by hawkmage on 2013-04-16
When putting together an entire distribution, especially one for long term support, you usually are not on the bleeding edge versions of everything.  For stability you choose versions that are known to work well with all the other versions in the distribution.  Have you ever tried to build the newest version of Apache, OpenSSL, PCRE, ZLib and all of the other dependent parts using the latest versions available?  It is a major pain to get all of the parts to work together, now add in specific patches for the distribution tweaks it can be a nightmare.

---

### Post by Irihapeti on 2013-04-16
Ubuntu is not the only distro doing this. CentOS and Debian Stable, to name just two, have similar policies.

---

