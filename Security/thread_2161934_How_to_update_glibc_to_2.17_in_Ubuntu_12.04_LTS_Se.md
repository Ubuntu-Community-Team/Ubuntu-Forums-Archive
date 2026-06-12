---
title: "How to update glibc to 2.17 in Ubuntu 12.04 LTS Server?"
date: 2013-07-12
forum: Security
---

### Post by LightRain on 2013-07-12
crypt(3)'s crypt_blowfish in Ubuntu 12.04 LTS server has an old implementation of generating a blowfish password hash. This implementation is [insecure]("http://seclists.org/oss-sec/2011/q2/632"). The newer versions of crypt_blowfish uses an ID $2y$.

The problem is I have a web application which uses the OS's crypt(3) to generate password hashes (blowfish in particular), and I would prefer to use the newer implementation than the current old one.

I think the crypt library lives in glibc, but 12.04 server only supports up to glibc 2.15. Is there a way to update this to glibc 2.17 without creating havoc in my system? I know that Raring has the newer glibc, but I want to stay on LTS.

---

