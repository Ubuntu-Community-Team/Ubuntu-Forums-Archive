---
title: "Apache RewriteRule not checking cookie value"
date: 2011-08-08
forum: Server Platforms
---

### Post by tr333 on 2011-08-08
I'm setting a cookie value using RewriteRule statements in .htaccess for checking if my site should not redirect from the main desktop site to the mobile site (when accessed via iphone browser).  The problem occurs when the first RewriteRule sets "mobile=desktop" in the cookie (from detecting "?desktop=true" in the querystring), the third RewriteRule fails to detect the new cookie value and redirect.  If I reload the page again (without any querystring for "?desktop=true"), then the third RewriteRule redirects successfully.

Can anyone tell me why the third RewriteRule fails to detect the cookie value straight after it is set in the first rule?  How can I fix this to work properly?

```
# set cookie if true querystring
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{QUERY_STRING} (.*)desktop=true(.*)$
RewriteRule ^(.*) - [CO=mobile:desktop:example.com]

# unset cookie if false querystring
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{QUERY_STRING} (.*)desktop=false(.*)$
RewriteRule ^(.*) - [CO=mobile:mobile:example.com]

# Redirect iPhone users to mobile website
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{HTTP_COOKIE} !mobile=desktop
RewriteRule ^(.*) http://m.example.com/$1 [L,R]

```

---

### Post by ruffEdgz on 2011-08-08
Well, have you tried placing more flags at the 'RewriteRule' conditions? So for example:
```

...
RewriteRule ^(.*) - [CO=mobile:desktop:example.com] [NC]
...
RewriteRule ^(.*) - [CO=mobile:mobile:example.com] [NC]
...
RewriteRule ^(.*) http://m.example.com/$1 [L,R]

```
Also, I could be wrong but I have never seen the flag [NC] on the 'RewriteCond' variable in a configuration but I could be wrong. 

You might know about these but here are two links for RewriteCond and RewriteRule:

[http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewritecond](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewritecond)
[http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewriterule](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewriterule)

Hope this helps.

---

### Post by tr333 on 2011-08-08
The [NC] flag just does case-insensitive matching, and it appears to work on the RewriteCond lines as the actual querystring contains "iPhone" or "iPod" with the uppercase "P".  I'm not sure what you mean by placing more flags at the RewriteRule conditions?

---

### Post by tr333 on 2011-08-09
It seems that the cookie value can't be set and then read in the same request, so I fixed it by checking the querystring at the same time as the cookie.

```
# set cookie if true querystring
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{QUERY_STRING} (.*)d=true(.*)$
RewriteRule ^(.*) - [CO=mobile:desktop:example.com]

# unset cookie if false querystring
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{QUERY_STRING} (.*)d=false(.*)$
RewriteRule ^(.*) - [CO=mobile:mobile:example.com]

# Redirect iPhone users to mobile website
# if ?d != true AND cookie unset
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{QUERY_STRING} !(.*)d=true(.*)$
RewriteCond %{HTTP_COOKIE} !mobile=desktop
RewriteRule ^(.*) http://m.example.com/$1 [L,R]

# Redirect iPhone users to mobile website
# if ?d != true AND ?d = false
RewriteCond %{HTTP_USER_AGENT} (iphone|ipod) [NC]
RewriteCond %{QUERY_STRING} !(.*)d=true(.*)$
RewriteCond %{QUERY_STRING} (.*)d=false(.*)$
RewriteRule ^(.*) http://m.example.com/$1 [L,R]
```

---

### Post by kingpin393 on 2011-08-16
@tr333 Thanks for that - was trying to figure that out for hours.

---

