---
title: "How does apt-get determine which version to get from repository?"
date: 2010-09-27
forum: Server Platforms
---

### Post by helloworld1215 on 2010-09-27
I am doing on 9.04 jaunty:

apt-get install libssl-dev 

and it is requesting:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-15ubuntu3.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-15ubuntu3.4_amd64.deb)

How is it determining 3.4 is the version that corresponds to 9.04? How does the number at the location of 3.4 correspond to ubuntu versioning?

The correct url is:

[http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-15ubuntu3.5_amd64.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-15ubuntu3.4_amd64.deb")

How do fix apt-get to get correct version?
Why is it failing in this instance?

**Solution: apt-get update**

---

