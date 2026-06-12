---
title: "Subverion and Apache - 301 error on redirect"
date: 2007-09-22
forum: Server Platforms
---

### Post by jdemarco on 2007-09-22
I am having some difficulty with a subversion/apache2 install.

Everything seems to be set up correctly, and I have successfully created a repository.

I created a redirect page from a hosted site to my server IP. -> [http://projectname/mysite.com:8080/svn](http://projectname/mysite.com:8080/svn)

I can access the SVN with a browser via the named redirect or the IP address of my server.

When using eclipse or tortoise I can only access the SVN via the IP address.

When I attempt to check out/in with the redirected URL I get
error 301 PROPFIND "permanently moved to" http://mysite.com"

what could the issue be?
What other information should I provide?

---

### Post by jdemarco on 2007-09-23
The answer that seems to be the correct onet after asking arround is that subversion does not support HTTP redirect.

Oh well. What can I do about the dynamic IP?

---

