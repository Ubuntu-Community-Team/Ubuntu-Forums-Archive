---
title: "lsof misses file opened in gedit"
date: 2015-09-11
forum: Ubuntu Application Development
---

### Post by sajeesh-cs on 2015-09-11
It has been found that lsof misses the files opened in gedit. In fact this is not the problem with lsof. It is absent in the links of /proc/<p-id>/fd, where <p-id> is the process id of gedit.
Can anybody plz tell the reason behind this . gedit is just an example. There may be other editors or programs , which open the files , but go unnoticed by lsof.  Can anybody plz suggest a solution for this ?

---

