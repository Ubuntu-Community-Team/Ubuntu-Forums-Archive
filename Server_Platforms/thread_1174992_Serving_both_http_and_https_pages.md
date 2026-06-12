---
title: "Serving both http and https pages"
date: 2009-05-31
forum: Server Platforms
---

### Post by Trismegister on 2009-05-31
Followed many helpful pages giving apache2 advice - fantastic! So I have a working https server .... AND an HTTP server.
Still left with acouple of questions ---- do I need both?
I would prefer to have just one and to have peoples' http requests establish a secure connection automatically and henceforward converse via https. i.e not REQUIRE users to type in https to start with.
So obviously I would like to have just the one server (directory root)... do I need a rewrite rule? (Don't really understand what that is.) ... to turn new visitors' http requests into https request?
You can see I don't fully understand issues ... just want to give my client a secure website that responds without security alerts to PayPal callback pages etc.
(Plus - when we go live, site will go from my Apache2 server to their IIS server ... so only want the one set of files to migrate)
Can you help?

---

### Post by eth1 on 2009-06-01
A mod_rewrite rules as given below will redirect requests if on HTTP:// to HTTP:// automatically, 

```
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
```


You need to make sure mod_rewrite is in the list of loaded modules for Apache.

---

### Post by Smartin on 2009-06-04
> **eth1 said:**
> A mod_rewrite rules as given below will redirect requests if on HTTP:// to HTTP:// automatically, 

```
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
```


You need to make sure mod_rewrite is in the list of loaded modules for Apache.

eth1,

I'm a newb so sorry if this is basic...

This looks like a cool trick... can you expand a little...?

1) Which file do I make the above changes to? /etc/apache2/httpd.conf?

2) Does this mean that any page served behind http:// would be served behind https:// just by adding the 's' in https:// in the browser's URL bar?

3) What is the best way of serving a page *only* behind [https://?](https://?) A 'redirect'. However that works... :-)

Simon

---

