---
title: "Should i install Tripwire offline or online?"
date: 2016-01-25
forum: Security
---

### Post by patrikmellq on 2016-01-25
Hello, i am going to make a fresh installation of Ubuntu LTS system.
And will install Tripwire from scratch.

1) is it safe to connect to internet for just a couple of seconds to run the command "apt-get install tripwire" and then brake the connection to internet when the tripwire package is downloaded.
2) or should i download source package and install tripwire that way.


Cheers

---

### Post by newbie-user on 2016-01-25
It is safe to connect to the Internet. Ubuntu doesn't have any open ports on a fresh install, except maybe ssh, but you should protect that with ssh keys anyway.

---

### Post by Habitual on 2016-01-26
I'd do that.
Connect, install, disco...

---

