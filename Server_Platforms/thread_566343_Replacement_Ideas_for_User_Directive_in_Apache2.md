---
title: "Replacement Ideas for User Directive in Apache2?"
date: 2007-10-03
forum: Server Platforms
---

### Post by TCarr on 2007-10-03
I'm setting up a CGI server for hosting multiple sites. The Virtual Host configuration used to be something like this (in another distro which I don't know which right now) :

```

<Virtual Host *>
User "#100"
Group "#1001"
ServerAdmin postmaster@somedomain.com
ServerName somedomain.com
ServerAlias cgi.somedomain.com
Document Root /var/www/domains/somedomain.com
ScriptAlias /cgi-bin/ /var/www/domains/somedomain.com/cgi-bin/
</Virtual Host>
```

When I try to do it this way in Ubuntu (see sig for version), I get an error saying that the User and Group directives are not valid within Virtual Host.

What is an alternative method to this?

---

### Post by MJN on 2007-10-03
You need the suExec wrapper installed (see [http://httpd.apache.org/docs/2.0/suexec.html](http://httpd.apache.org/docs/2.0/suexec.html) for details).
 
I've not used it myself but I believe the module is already shipped so can be enabled with **sudo a2enmod suexec**.
 
Edit: I guess you were using Apache 1.3 as I see from [http://httpd.apache.org/docs/2.0/mod/mpm_common.html#user](http://httpd.apache.org/docs/2.0/mod/mpm_common.html#user) that the directive is no longer supported inside <VirtualHost> containers from 2.0 onwards, even with the suEXEC wrapper, so you must instead now use the **suexecusergroup** directive (see [http://httpd.apache.org/docs/2.0/mod/mod_suexec.html#suexecusergroup](http://httpd.apache.org/docs/2.0/mod/mod_suexec.html#suexecusergroup) - note you will still need the suexec module loaded).
 
Mathew

---

### Post by TCarr on 2007-10-04
Thank you. This information gave me what I needed to fix the problem. :KS

---

