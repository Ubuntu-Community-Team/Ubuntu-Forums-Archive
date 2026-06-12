---
title: "Courier-imap and maildrop recompilation"
date: 2013-01-29
forum: Server Platforms
---

### Post by Wombacik on 2013-01-29
I need to enable quota for trash folders. [Here]("http://www.courier-mta.org/imap/README.maildirquota.html") i found that i need use ```
--with-trashquota
``` to compile maildrop and courier-imap.

I did some research and found [This]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/").

Downloaded sources and executed: 
```
DEB_BUILD_OPTIONS="--with-trashquota" fakeroot debian/rules binary
```
for both packages. After all finished i have installed produced packages and restarted system. 

I cant see change, trash folder still has unlimited space - what i did wrong?

---

