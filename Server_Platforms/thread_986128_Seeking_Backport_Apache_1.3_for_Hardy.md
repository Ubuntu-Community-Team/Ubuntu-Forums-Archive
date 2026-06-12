---
title: "Seeking Backport: Apache 1.3 for Hardy"
date: 2008-11-18
forum: Server Platforms
---

### Post by DJ_Cyberdance on 2008-11-18
Hi!
Obviously the apache packages have been abandoned in Hardy, and even if I uncomment the hardy-backports repository and do a apt-get update, there are no apache packages at all.

I definitely cannot use apache2 as I am setting up a testing environment which should be the same as the production system. I also want to avoid to install apache from source, I'd prefer installing apache via apt-get.

Any ideas?

---

### Post by cdenley on 2008-11-18
I don't think that would be a backport, maybe a forwardport. I would suggest either using Debian or Ubuntu dapper.

[http://www.debian.org/CD/](http://www.debian.org/CD/)
[http://mirrors.us.kernel.org/ubuntu-releases/6.06/](http://mirrors.us.kernel.org/ubuntu-releases/6.06/)

---

### Post by DJ_Cyberdance on 2008-11-19
Thanks for the hint, but unfortunately that is not possible. I got to install Apache 1.3 on a Hardy system

---

