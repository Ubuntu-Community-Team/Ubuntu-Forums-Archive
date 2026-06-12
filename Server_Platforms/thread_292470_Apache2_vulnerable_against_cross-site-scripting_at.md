---
title: "Apache2 vulnerable against cross-site-scripting attacks"
date: 2006-11-03
forum: Server Platforms
---

### Post by JGZimmerle on 2006-11-03
Hi!

Nessus just found the following security hole in my apache2-configuration (ubuntu lamp server). I think this should be fixed in the default configuration of the apache2-package, in a way that the fix is automatically applied to all virtual hosts.




Synopsis :

Debuging functions are enabled on the remote HTTP server.

Description :

The remote webserver supports the TRACE and/or TRACK methods. TRACE and TRACK
are HTTP methods which are used to debug web server connections.   

It has been shown that servers supporting this method are subject to
cross-site-scripting attacks, dubbed XST for "Cross-Site-Tracing", when
used in conjunction with various weaknesses in browsers. 

An attacker may use this flaw to trick your legitimate web users to give
him their credentials. 

Solution :

Disable these methods.

See also :

[http://www.kb.cert.org/vuls/id/867593](http://www.kb.cert.org/vuls/id/867593)


Plugin output :


Solution : 
Add the following lines for each virtual host in your configuration file :

    RewriteEngine on
    RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
    RewriteRule .* - [F]

---

### Post by Dandroid on 2008-03-19
TRACE should not be disabled by default, it is part of the http standard.  From what I've gathered this claim has been rejected by Apache. Quoting from [here]("http://groups.google.com.sg/group/alt.os.linux.suse/browse_frm/thread/63bafdd38c87724d/e07c2d7351ab983?hl=en&lr=&rnum=8&prev=/groups%3Fq%3Ddisable%2BHTTP%2BTRACE%2Bapache%26hl%3Den%26lr%3D%26selm%3D3eccccb4%25241%2540news.isdn.net%26rnum%3D8#e07c2d7351ab983").

> Actually, Apache says it is not a vulnerability, and TRACE cannot be disabled
except in the source code.
-----
No, because it is not a vulnerability.  White Hat's claims are bogus
and have been rejected by every author of the HTTP standard, along
with several reviewers on bugtraq.

Removing TRACE does not in any way reduce exposure to cross-site
scripting bugs in clients since there are other ways to get access
to that information even if the server has disabled TRACE.
In any case, a site that does not use cookie-based authentication
is not vulnerable to cross-site scripting, and those that do are
only vulnerable to this particular issue for an MSIE browser that
has not been patched and is improperly configured to use the
deprecated HTTP-only scripting option.  All other browsers are
no more "vulnerable" with or without TRACE.

The worst solution to this problem would be to run around and
turn off TRACE on all httpd servers -- a feature of HTTP that
depends on it being enabled by default.  If you must disable it,
then you will have to edit the code directly.  We might add a
directive to disable it in the future for performance reasons.

Cheers,

Roy T. Fielding, co-founder, The Apache Software Foundation

---

