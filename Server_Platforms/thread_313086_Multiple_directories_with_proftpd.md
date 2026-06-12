---
title: "Multiple directories with proftpd"
date: 2006-12-05
forum: Server Platforms
---

### Post by lordgibbness on 2006-12-05
I have recently set up an ftp server using proftpd with some info gathered from sites such as [this one]("http://www.ubuntuforums.org/showthread.php?t=79588")

I have created a user called ftp who is chrooted into his home directory (/home/ftp/) by adding "DefaultRoot ~" to my proftpd.conf file.

However, I now want this user to be able to access certain other directories on my system. One example of this is I want to allow access to my music on my network (mounted to /mnt/music/).

I have tried creating a symlink to /mnt/music/ but I have not been able to get this to work as required. When I used to use serv-u I could create virtual paths or something along those lines...

Has anyone got an ideas.

BTW, for anyone having slow browsing issues when using proftpd try adding these two lines to the config:

```
UseReverseDNS off
IdentLookups off
```

(I thought it may be useful!)

Rob.

---

