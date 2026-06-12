---
title: "Start a prorgram at boot"
date: 2011-11-17
forum: Server Platforms
---

### Post by securitymeddler on 2011-11-17
How would I go about getting an application to start at re-boot as a specific user? 

e.g. I want apache to start at "john" rather than root as boot?

---

### Post by Lars Noodén on 2011-11-17
There are the run-time directives [User](http://httpd.apache.org/docs/trunk/mod/mod_unixd.html#user) and [Group](http://httpd.apache.org/docs/trunk/mod/mod_unixd.html#group).  Those are normally set to 'www-data'.  

If you mean before that, then Apache needs to start as root in order to use port 80.  If you are using a port above 1024, then you might be able to do it.  In that case, you'll need to make the change in /etc/init.d/apache2

---

