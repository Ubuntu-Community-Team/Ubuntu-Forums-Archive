---
title: "Lucid server: (mailgraph+dspam) X suexec"
date: 2010-06-17
forum: Server Platforms
---

### Post by mmerlone on 2010-06-17
Hi all,

I am setting a Lucid mail server, and got dspam and mailgraph installed. dspam requires suexec module for apache, but it breaks mailgraph with "500 Internal Server Error":

/var/log/apache2/error.log
```
[Thu Jun 17 09:53:18 2010] [error] [client 127.0.1.1] suexec policy violation: see suexec log for more details, referer: http://haumea.a1.ind.br/cgi-bin/mailgraph.cgi
[Thu Jun 17 09:53:18 2010] [error] [client 127.0.1.1] Premature end of script headers: mailgraph.cgi, referer: http://haumea.a1.ind.br/cgi-bin/mailgraph.cgi
```

/var/log/apache2/suexec.log:
```
[2010-06-17 09:31:30]: uid: (119/dspam) gid: (128/dspam) cmd: mailgraph.cgi
[2010-06-17 09:31:30]: command not in docroot (/usr/lib/cgi-bin/mailgraph.cgi)
```


How can I work around it? Should I open a bug?

---

### Post by mmerlone on 2010-06-17
Bump! Can't anybody help me, pls?

> **mmerlone said:**
> Hi all,

I am setting a Lucid mail server, and got dspam and mailgraph installed. dspam requires suexec module for apache, but it breaks mailgraph with "500 Internal Server Error":

/var/log/apache2/error.log
```
[Thu Jun 17 09:53:18 2010] [error] [client 127.0.1.1] suexec policy violation: see suexec log for more details, referer: http://haumea.a1.ind.br/cgi-bin/mailgraph.cgi
[Thu Jun 17 09:53:18 2010] [error] [client 127.0.1.1] Premature end of script headers: mailgraph.cgi, referer: http://haumea.a1.ind.br/cgi-bin/mailgraph.cgi
```

/var/log/apache2/suexec.log:
```
[2010-06-17 09:31:30]: uid: (119/dspam) gid: (128/dspam) cmd: mailgraph.cgi
[2010-06-17 09:31:30]: command not in docroot (/usr/lib/cgi-bin/mailgraph.cgi)
```


How can I work around it? Should I open a bug?

---

