---
title: "Problems with /etc/hosts"
date: 2011-03-09
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-09
Hi everyone,

I am trying to use PHP mail function, so I've installed sendmail (ubuntu 10.10 server) - It worked but very very slow. I found many messages in forums with same problem, but few answers.

One of these answer was modificate /etc/hosts, and instead of two lines, write only one, like this:

127.0.0.1    localhost localhost.localdomain nameofserver

I did, and now doesnt works. I tried to write same as it was:

127.0.0.1 locahost
127.0.1.1 nameofserver

But neither.

Any idea about:
1. reset /etc/hosts file?
2. make sendmail (or other MTA, I tried with postfix) works

Thanks in advance! :p

---

### Post by Iker Etxebarria on 2011-03-09
Try this
127.0.0.1 localhost
IPAddress FQDomainName

Where IPAddress is the IP address of your server an FQDomainName the DNS name of your server i.e. ([www.myserver.com](www.myserver.com))

---

