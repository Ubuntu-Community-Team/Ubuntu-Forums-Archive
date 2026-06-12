---
title: "Apache2 ssl rewrite rule conflict"
date: 2008-12-10
forum: Server Platforms
---

### Post by vitalyb on 2008-12-10
Ok, so I'm trying to set up mod_rewrite rules on apache to serve a few pages from https but the rest over http.  However Im getting a loop error.  I want all /accounts/* & /admin/* pages to be over https but everything else to redirect back to http.

How would be the best way to set this up?  Here is my config for the rules:

RewriteEngine   on
RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     ^/accounts/(.*)$ https://%{SERVER_NAME}/accounts/$1 [L,R]

RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     ^/admin/(.*)$ https://%{SERVER_NAME}/admin/$1 [L,R]

#RewriteCond     %{SERVER_PORT} ^443$
#RewriteRule     ^/(.*)$ http://%{SERVER_NAME}/$1 [L,R]


THanks in advance.

---

### Post by MJN on 2008-12-10
With that exact config what's the exact error (and for what URL)?

Mathew

---

### Post by vitalyb on 2008-12-10
on [http://siteurl.com/accounts/](http://siteurl.com/accounts/)

Page Load Error

Redirect Loop
Firefox has detected that the server is redirecting the request for this address in a way that will never complete.

---

### Post by MJN on 2008-12-11
I'm not sure why it's not working to be honest.
 
Try enabling [logging](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewritelog) to see what is being rewritten and to what.
 
Mathew

---

### Post by vitalyb on 2008-12-12
Fixed the issue with these rules:

in my  <VirtualHost mywebsite:80>

RewriteEngine   on
RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     ^/accounts/(.*)$ https://%{SERVER_NAME}/accounts/$1 [L,R]
RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     ^/admin/(.*)$ https://%{SERVER_NAME}/admin/$1 [L,R]


in my  <VirtualHost mywebsite:443>

RewriteEngine   on
RewriteCond     %{SERVER_PORT} ^443$
RewriteCond %{REQUEST_FILENAME} !admin(.*)
RewriteCond %{REQUEST_FILENAME} !accounts(.*)
RewriteRule ^/(.*)$ http://%{SERVER_NAME}/$1 [R]

---

### Post by MJN on 2008-12-13
I'm not sure I can see what the difference is!

Oh well, as long as you're now up-and-running!

Mathew

---

### Post by kongo09 on 2011-05-22
Difference seems to be that in the second case, rewriting of SSL requests for the secured directories is excluded from being put back to port 80 on http

In the first case, a call to the admin directory over http gets caught and redirected to https. However, then the rules are processed again (after all, it is a new request) and then this gets caught by the third rule and redirected back to http. And then the game starts over. An endless loop.

If you use the Live Http Headers plugin in Firefox, you can actually see it.

---

