---
title: "strange characters in CLI"
date: 2013-03-07
forum: Server Platforms
---

### Post by TeamScience on 2013-03-07
Hi

I just got a new remote server and am doing the initial set-up and admin. I get strange characters when doing apt-get upgrade:

E.g.

Fetched 6Â*525 kB in 2s (2Â*794 kB/s)
Get:3 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) quantal-updates/main libperl5.14 amd64 5.14.2-13ubuntu0.1 [1Â*226 B]

I'm not sure what this could be caused by. You can see the **6Â and 2Â and 1Â** in the above examples. As this is going to be a production hosting server I need to make sure that this isn't something that may bite me in the a** later on in the set-up and install. In the CLI there are no * as shown above, so not sure why a copy and paste would place them there.

Any pointers would be greatly appreciated.
Brenton

---

### Post by schragge on 2013-03-07
Software on the remote server doesn't use Unicode (UTF-8), but the terminal you ssh from does, or vice versa. Maybe [luit]("http://manpages.ubuntu.com/manpages/precise/en/man1/luit.1.html") from the package *x11-utils* will help:
```
LC_ALL=C luit ssh legacy-machine
``` *Â** is crippled thousands separator.

---

### Post by CharlesA on 2013-03-07
schragge pretty much nailed it.

If you are using Putty on Windows, it defaults to Latin-1 instead of UTF-8. You can change that from Window > Translation.

---

