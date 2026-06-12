---
title: "Another OpenSSL bug found"
date: 2014-06-06
forum: Security
---

### Post by SeijiSensei on 2014-06-06
[http://bits.blogs.nytimes.com/2014/06/05/new-bug-found-in-widely-used-openssl-encryption/](http://bits.blogs.nytimes.com/2014/06/05/new-bug-found-in-widely-used-openssl-encryption/)

This one can only be exploited by a "man-in-the-middle" attack.  An HTTPS connection from a machine using, say, airport wireless could be intercepted.  

The fix has been "back-ported" to OpenSSL versions running on Ubuntu and to RedHat flavors like CentOS.  While this flaw isn't nearly as serious as Heartbleed, you should update your copies of OpenSSL.

The complete report from the OpenSSL team is here: [https://www.openssl.org/news/secadv_20140605.txt](https://www.openssl.org/news/secadv_20140605.txt)

Ubuntu users should be running 1.0.1f-1ubuntu2.2.

---

### Post by andrew102 on 2014-06-16
Actually there are newer releases.
[https://launchpad.net/ubuntu/+source/openssl](https://launchpad.net/ubuntu/+source/openssl)

Anyone can tell me if all four current/dev on that page are equivalent to openssl-1.0.1h ? [http://git.openssl.org/gitweb/?p=openssl.git;a=blob_plain;f=CHANGES;hb=refs/heads/OpenSSL_1_0_1-stable](http://git.openssl.org/gitweb/?p=openssl.git;a=blob_plain;f=CHANGES;hb=refs/heads/OpenSSL_1_0_1-stable)

It's confusing to be using ubuntu branches 'e' and 'f' when heartbleed was actually fixed in main source 'g'.

---

### Post by deadflowr on 2014-06-16
> **andrew102 said:**
> Actually there are newer releases.
[https://launchpad.net/ubuntu/+source/openssl](https://launchpad.net/ubuntu/+source/openssl)

Anyone can tell me if all four current/dev on that page are equivalent to openssl-1.0.1h ? [http://git.openssl.org/gitweb/?p=openssl.git;a=blob_plain;f=CHANGES;hb=refs/heads/OpenSSL_1_0_1-stable](http://git.openssl.org/gitweb/?p=openssl.git;a=blob_plain;f=CHANGES;hb=refs/heads/OpenSSL_1_0_1-stable)

It's confusing to be using ubuntu branches 'e' and 'f' when heartbleed was actually fixed in main source 'g'.

f is f and h is h.
Version g was built with the fix, were as the versions used by Ubuntu simply got patched.
The patches were of the smallest possible size, so they would fix the bugs, and yet keep the possible damaging effects or changes to the system to a minimum.
Upgrading the whole package version might have had unforeseen consequences, which could have taken a little longer to workout.
If any of that makes sense.

---

