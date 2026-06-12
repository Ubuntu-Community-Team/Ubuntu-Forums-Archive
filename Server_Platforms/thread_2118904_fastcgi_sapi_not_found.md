---
title: "fastcgi sapi not found"
date: 2013-02-22
forum: Server Platforms
---

### Post by kr651129 on 2013-02-22
I'm trying to install the PHP/Java Bridge for tomcat 6.  I installed tomcat6 via apt-get.  I deployed the war and I'm getting the following error:

```

java.io.IOException: No suitable php fastcgi sapi found. Install PHP as either "/usr/bin/php-cgi" or "c:/Program Files/PHP/php-cgi.exe" or "/var/lib/tomcat6/webapps/JavaBridge/WEB-INF/cgi/php-cgi-amd64-linux". See also "php_exec" in your WEB-INF/web.xml. 
Reason follows:
	php.java.servlet.fastcgi.FastCGIServlet.handle(FastCGIServlet.java:909)
	php.java.servlet.fastcgi.FastCGIServlet.doGet(FastCGIServlet.java:945)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:617)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	php.java.servlet.PhpCGIFilter.doFilter(PhpCGIFilter.java:126)

```

I've googled this and can't find any fix.  Has anyone here ran into this before?

---

### Post by kr651129 on 2013-02-22
```
sudo apt-get install php5-cgi
sudo service tomcat6 restart
```

solved my problem

---

