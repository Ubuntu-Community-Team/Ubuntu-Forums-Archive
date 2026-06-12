---
title: "Updating &quot;openssl&quot; on Ubuntu 10.04.4 LTS ?"
date: 2013-11-24
forum: Server Platforms
---

### Post by ajung on 2013-11-24
We are running Ubuntu 10.04.4 LTS with OpenSSL 0.9.8k 25 Mar 2009.

In my understanding we need a much never OpenSSL version in order to support more advanced ciphers in Apache in order get
rid of the RC4 cipher support and in order to provide up-to-date encryption support.

Is this correct?

What is the recommended way to update OpenSSL to a more recent version like 1.0.1e?

---

### Post by ian-weisser on 2013-11-26
You have several upgrade options...but you may not like any of them.

1) You usually CAN'T install a .deb package from a later release of Ubuntu or Debian. Those are compiled against newer dependencies than you have. Upgrading all the dependencies introduces precisely the risk you are trying to avoid by running an LTS release. I haven't checked the OpenSSL dependencies - maybe you can.

2) You can compile from source, using the dependencies you already have installed.

3) You can upgrade your entire system to 12.04 LTS (or in April 2014: 14.04 LTS). The upgrade will include the latest versions of many packages, including OpenSSL. Depending on what you are serving, this migration may introduce risk, too.

Obviously you shouldn't try any of these changes on your production server until you have experimented with them on a testing system first.

---

