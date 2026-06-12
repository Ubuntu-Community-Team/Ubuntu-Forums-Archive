---
title: "MariaDB TLS version from official repos [18.04]"
date: 2019-06-11
forum: Security
---

### Post by simernes on 2019-06-11
Hi,

sorry to post this very basic question but I'm wondering if someone can help me clarify the version of TLS included from the official 18.04 repos for mariadb.

AFAIK TLS is somewhat broken up to (not inclusive) TLS 1.2. The MariaDB that is included in the repos is compiled with YaSSL version 2.4.4, but I'm having difficulties pinning down exactly the TLS version that my server is running.

On the official website of YaSSL [https://www.wolfssl.com/products/yassl/](https://www.wolfssl.com/products/yassl/) it says it supports TLS up to version 1.1, but this is for version 2.4.2, from 2016, while there has been a newer version, the 2.4.4 which is installed on my system released on 08/08/2017, but the release notes I've been able to dig up are rather scarce.

Can anyone verify whether or not this version only has TLS 1.1? I'm just wondering if it's worth the effort to use a version that's not in the official repo.

---

### Post by norobro on 2019-06-11
Looks like mariadb-10.1 is hard coded to use <= TLS 1.1 

From the mariadb source code here: [https://github.com/MariaDB/server/blob/10.1/extra/yassl/src/handshake.cpp#L789](https://github.com/MariaDB/server/blob/10.1/extra/yassl/src/handshake.cpp#L789)
```
[COLOR=#000000][FONT=monospace]           [COLOR=#880000][FONT=inherit]/*
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]              According to RFC 4346 (see "7.4.1.3. Server Hello"), the Server Hello
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]             packet needs to specify the highest supported TLS version, but not
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]              higher than what client requests. YaSSL highest supported version is
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]              TLSv1.1 (=3.2) - if the client requests a higher version, downgrade it
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]              here to 3.2.
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]              See also Appendix E of RFC 5246 (TLS 1.2)
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#880000][FONT=inherit]            */
[/FONT][/COLOR][/FONT][/COLOR]
```HTH

---

### Post by simernes on 2019-06-12
Is this implementation affected by any security vulnerabilities? I'm reading all over the internet that TLS 1.1 should be updated so I'm just wondering why this is kept in the Ubuntu repos.

---

### Post by norobro on 2019-06-12
I don't know much about this. Your post piqued my curiosity so I took a peek at the source code and found the above information.

Upstream, Mariadb 10.4.5 is a release candidate and uses wolfssl which supports <= TLS 1.3. 
[https://github.com/MariaDB/server/tree/10.4/extra/wolfssl](https://github.com/MariaDB/server/tree/10.4/extra/wolfssl)
[https://github.com/wolfSSL/wolfssl/blob/master/README.md](https://github.com/wolfSSL/wolfssl/blob/master/README.md)

There's no telling when 10.4.5 will be released and then incorporated into Ubuntu. The Disco Dingo (19.04) repo contains Mariadb-10.3.

There is a 10.4.5 Deb package available from Mariadb: [https://downloads.mariadb.org/mariadb/10.4.5/#os_group=deb_package](https://downloads.mariadb.org/mariadb/10.4.5/#os_group=deb_package)

---

### Post by simernes on 2019-06-13
Thanks norobro, I didn't find that deb right away when I was looking and  it's a good alternative to using a repo in terms of maintaining it as  at least for me they appear a little easier to remove than installing  from source in some cases.

---

