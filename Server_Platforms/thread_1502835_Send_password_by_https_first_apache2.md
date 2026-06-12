---
title: "Send password by https first apache2"
date: 2010-06-06
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2010-06-06
So, I run an apache2 server on port 80 and 443. I have a folder that is password protected, but I know people will try accessing it via http and not https, 
So I tried this
```
RewriteEngine On 
RewriteCond %{SERVER_PORT} 80 
RewriteCond %{REQUEST_URI} mov
RewriteRule ^(.*)$ https://mysite/folder/ [R,L]

AuthUserFile /home/administrator/blahblah/
AuthGroupFile /dev/null
AuthName "Password Protected Area"
AuthType Basic


<limit GET POST>
require valid-user
</limit>

```

But it encryts the folder AFTER they entered the password, any ideas?
I mean I have it set so that if they try accessing it on http they get a 403 error... but that's not exactly cool.

---

### Post by JigglyWiggly_ on 2010-06-06
Oh wait just solved it, a bit redundant what I did...
I denied all requests to the page through http.
I changed the error handling inside the folder, for the 403 error. I made it so if they had that, it will send them to the https
page.

Perfect :P

---

