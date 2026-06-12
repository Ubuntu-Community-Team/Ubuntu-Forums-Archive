---
title: "IRCD-Hybrid: OpenSSL path not found"
date: 2011-03-13
forum: Server Platforms
---

### Post by Lefke123 on 2011-03-13
I'm having a problem enabling the SSL on an IRCD-Hybrid install on an Ubuntu 10.04 (x86) server, and also on a clean install. Specifically, IRCD-Hybrid doesn't detect the OpenSSL folder.

To reproduce the problem on a clean 10.04 (x86) install:
```

wget -O ircd-hybrid-7.2.3.tar.gz http://downloads.sourceforge.net/project/ircd-hybrid/ircd-hybrid/ircd-hybrid-7.2.3/ircd-hybrid-7.2.3.tgz
tar xzf ircd-hybrid-7.2.3.tar.gz
cd ircd-hybrid-7.2.3/
./configure --enable-openssl=/usr/bin/openssl

```

Output:
```

<snip>
checking for usleep... yes
checking for OpenSSL... not found. Specify a correct path?
checking zlib.h usability... no
<snip>

Compiling ircd-hybrid 7.2.2

Installing into: /usr/local/ircd
Ziplinks ................ no
OpenSSL ................. no
Modules ................. shared
IPv6 support ............ yes
Net I/O implementation .. epoll
EFnet server ............ no (use example.conf)
Halfops support ......... no
Small network ........... no
G-Line voting ........... yes

Configured limits:
NICKLEM ................. 9
TOPICLEM ................ 160

```

'which openssl' pointed to '/usr/bin/openssl' but the directory itself doesn't contain any files.

Has anyone had a problem like this as well? If so, is it fixable or do I need to find another solution to secure the IRC traffic? Thanks in advance!

---

### Post by Maisondouf on 2012-06-15
Dangerous !!!
when saying 

```

ln -s /usr/bin/openssl ./openssl
./configure --enable-openssl=./openssl
```

result is

```
configure: error: invalid value for --enable-syslog: ./openssl
```

Is there a misfit between options ???
So log write over /usr/sbin/openssl ???

---

