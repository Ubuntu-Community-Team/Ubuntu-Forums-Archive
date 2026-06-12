---
title: "Subversion Problem"
date: 2018-06-15
forum: Server Platforms
---

### Post by ivkoweb on 2018-06-15
Svn service was running okey. But, after i install SSH, and Shoutcast Service, my old SVN doesent work. I recive this error:

[HTML]org.apache.subversion.javahl.ClientException: E210003: connection refused by the server[/HTML]

Does somebody can help me?

---

### Post by Andreyshel on 2018-06-19
Check ports used by svn , ssh and Shoutcast in respective configuration files
Might be a port conflict.

---

