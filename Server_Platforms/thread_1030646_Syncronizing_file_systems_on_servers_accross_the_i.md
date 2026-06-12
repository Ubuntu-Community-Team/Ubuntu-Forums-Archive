---
title: "Syncronizing file systems on servers accross the internet"
date: 2009-01-04
forum: Server Platforms
---

### Post by infecticide on 2009-01-04
Hey folks,

I need to setup a second web/mail/mysql server to provide fail over in case the first server becomes unavailable.

These two machines will be located separate from each other in the same city/different isp's.

I understand how to provide fail-over with DNS, what I need is some way to keep the hard drives sync'd across the internet so the content is never different.

I am using Ubuntu Server if that helps.

---

### Post by TestDummy! on 2009-01-04
What about rsync?

---

### Post by eldaria on 2009-01-04
Another solution is ChironFS.
Not sure how it would preform over Internet link, you would probably need some kind of VPN going.
[http://www.linux.com/feature/137516](http://www.linux.com/feature/137516)

---

