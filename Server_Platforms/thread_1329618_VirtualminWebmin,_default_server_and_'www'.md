---
title: "Virtualmin/Webmin, default server and 'www'"
date: 2009-11-17
forum: Server Platforms
---

### Post by crystalgold on 2009-11-17
Hello,

I have a dedicated server with  Ubuntu 8.06 LTS running on it.
I installed virtualmin/webmin on the server to manage it easier.

I created a virtual server 'mydomain.com'.
Apache created the virtualhost which matches the virtual server.

The issue is that [www.mydomain.com](www.mydomain.com) points to the first virtualhost found alphabetically.
For example, if I create a virtualhost named 'hello.mydomaine.com', 'www' will point to it instead of mydomain.com.

The first thing I did to fix that was adding the directive 'ServerAlias' to my main virtualhost, but It did not work.

Apache logs dont say errors or misconfiguration.

Have you already had this issue?

Thank you for helping me out.

---

