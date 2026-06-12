---
title: "Getting 500 Internal Error after placing secure.domain.com"
date: 2010-11-04
forum: Server Platforms
---

### Post by kustomjs on 2010-11-04
Hi Guys
I am using ubuntu server 9.04 and I have secure.domain.com I get 500 internal error but when I take out the secure.domain.com from virtual host it works but when I put back in secure.domain.com I get that 500 internal error and when I look at the apache2 error log this what I get:
[Thu Nov 04 14:27:31 2010] [error] [client ] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.

how do I fix this issue?

---

### Post by koenn on 2010-11-10
> [Thu Nov 04 14:27:31 2010] [error] [client ] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.it's a configuration error. Since it only happens with secure... enabled, you probably best post the config for that vhost.

Also, set loglevel debug in your apache conf or the vhost conf, as suggested by the error msg. It will increase log output, which usually helps to diagnose a problem. (reload after changes to config)

---

