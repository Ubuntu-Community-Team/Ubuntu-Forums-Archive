---
title: "Joining active directory"
date: 2011-11-09
forum: Server Platforms
---

### Post by druhboruch on 2011-11-09
What is the best way to join ubuntu to active directory?

There are so many possibilities.

Please explain...

Thanks for your help.

---

### Post by HermanAB on 2011-11-10
There is really only one way:
Samba with Winbind:
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

or Likewise (which is the same thing, as the name implies):
[https://help.ubuntu.com/10.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/10.04/serverguide/C/likewise-open.html)

Six of one and half a dozen of the other...

---

### Post by druhboruch on 2011-11-10
How about Centrify DirectControl Express?
It is in the partner repository.

---

