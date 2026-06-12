---
title: "Apache : child pid ***** exit signal Segmentation fault (11)"
date: 2005-03-07
forum: Server Platforms
---

### Post by EcliptuX on 2005-03-07
Hi,

I'd just installed Apache2 on my Warty.
When I try to go on [http://localhost](http://localhost), the browser works indefinitely and nothing appears.
There, the error.log :
 ```
[Mon Mar 07 10:29:46 2005] [notice] Apache/2.0.53 (Debian GNU/Linux) DAV/2 SVN/1.1.3 mod_jk2/2.0.4 mod_python/3.1.3 Python/2.3.4 proxy_html/2.4 mod_ruby/1.2.4 Ruby/1.8.2(2005-01-10) mod_perl/1.999.20 Perl/v5.8.4 configured -- resuming normal operations 
[Mon Mar 07 10:29:47 2005] [notice] caught SIGTERM, shutting down 
[Mon Mar 07 10:29:48 2005] [notice] mod_python: Creating 32 session mutexes based on 6 max processes and 25 max threads. 
[Mon Mar 07 10:29:48 2005] [notice] Apache/2.0.53 (Debian GNU/Linux) DAV/2 SVN/1.1.3 mod_jk2/2.0.4 mod_python/3.1.3 Python/2.3.4 proxy_html/2.4 mod_ruby/1.2.4 Ruby/1.8.2(2005-01-10) mod_perl/1.999.20 Perl/v5.8.4 configured -- resuming normal operations 
[Mon Mar 07 10:29:49 2005] [notice] child pid 20038 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:49 2005] [notice] child pid 20040 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:50 2005] [notice] child pid 20042 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:52 2005] [notice] child pid 20045 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:52 2005] [notice] child pid 20047 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:53 2005] [notice] child pid 20049 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:53 2005] [notice] child pid 20051 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:53 2005] [notice] child pid 20053 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:53 2005] [notice] child pid 20054 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:54 2005] [notice] child pid 20057 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:54 2005] [notice] child pid 20059 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:55 2005] [notice] child pid 20061 exit signal Segmentation fault (11) 
[Mon Mar 07 10:29:55 2005] [notice] child pid 20063 exit signal Segmentation fault (11)
```
What is the problem ?

---

### Post by EcliptuX on 2005-03-07
OK the pb comes from an apache module (which?). After disinstall a lot of unused modules, the error disapears

---

### Post by alastair on 2005-03-07
I don't think I've ever seen so many modules loaded in Apache!

I guess you could do a binary search - disable 50%, test, etc.

---

### Post by kc9aop on 2007-09-02
I simply removed the python.conf from /etc/httpd/conf.d and that solved the problem with the seg faults.  (Actually I created a directory named /etc/httpd/conf.d/hold  and moved it there)

I agree the Apache server is fairly bloated, but the python module was the culprit for me.

---

