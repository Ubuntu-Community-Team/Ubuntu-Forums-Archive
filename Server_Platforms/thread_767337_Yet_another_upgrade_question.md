---
title: "Yet another upgrade question"
date: 2008-04-25
forum: Server Platforms
---

### Post by teqsun on 2008-04-25
I cannot upgrade using the ```
sudo do-release-upgrade --devel-release
``` method.

I have downloaded the CD onto my server and was wondering if it was possible to mount it and upgrade from the CD instead of using the command.

I reaaaaaaaaaly dont want to reinstall from scratch.


HELP!

---

### Post by Rohan Kapoor on 2008-04-25
It is possible but only if you have the alternate install cd.

---

### Post by teqsun on 2008-04-25
I have 'ubuntu-8.04-server-amd64.iso' does this qualify?

---

### Post by Rohan Kapoor on 2008-04-25
I believe so,

use ```
gksu "sh /cdrom/cdromupgrade"

```

to upgrade from it. See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by teqsun on 2008-04-25
sorry... I was using the method outlined in the first post and it just started working.

---

### Post by Rohan Kapoor on 2008-04-25
allright then. good for you.

---

