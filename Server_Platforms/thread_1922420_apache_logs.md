---
title: "apache logs"
date: 2012-02-08
forum: Server Platforms
---

### Post by hyuk48 on 2012-02-08
HI everybody~
I'm running apache-tomcat server on ubuntu 9.10.
As you can see below, last 2 numbers mean %I, %O.
%...I          Bytes received, including request and headers, cannot be         zero. 
%...O          Bytes sent, including headers, cannot be zero.


- - - [08/Feb/2012:22:53:15 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 1621
- - - [08/Feb/2012:22:53:20 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 0
- - - [08/Feb/2012:22:53:30 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 0
- - - [08/Feb/2012:22:53:25 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 0
- - - [08/Feb/2012:22:54:02 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 1621
- - - [08/Feb/2012:22:54:07 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 1621
- - - [08/Feb/2012:22:54:12 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 1621
- - - [08/Feb/2012:22:54:17 +0000] "GET /admin/jsp/login.jsp HTTP/1.1" 200 1238 "-" "-" 77 1621


But sometimes, I can see that the %O is ZERO. there is no problem on  apache thread or tomcat thread. 
I'm appreciate If you can explain this.

thanks for reading.

---

