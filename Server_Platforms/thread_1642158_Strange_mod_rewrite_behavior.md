---
title: "Strange mod_rewrite behavior"
date: 2010-12-10
forum: Server Platforms
---

### Post by Nfzgrld on 2010-12-10
I'm porting a php app to my new 10.10 server and am having a strange problem. After moving the files over, I tried the url and got a 404 error when I tried to log in to the site. AH HA! I thought, no rewrite. So I went and turned it on, and still no rewrite! It's basically a standard 10.10/Apache 2.2 install with mod_rewrite. Here's the rewrite directives:

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteOptions Inherit
RewriteBase /
RewriteCond %{SCRIPT_FILENAME} !-f
RewriteCond %{SCRIPT_FILENAME} !-d
RewriteRule ^adm/([a-zA-Z0-9_]+)$ adm/?pri=$1 [L]
RewriteRule ^adm/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)$ adm/?pri=$1&sec=$2 [L]
RewriteRule ^exe/([a-zA-Z0-9_]+)$ exe/$1.php [L]
RewriteRule ^exe/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)$ exe/$1.php?pri=$2 [L]
RewriteRule ^exe/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)$ exe/$1.php?pri=$2&sec=$3 [L]
RewriteRule ^([a-zA-Z0-9_]+)$ ?pri=$1 [L]
RewriteRule ^([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)$ ?pri=$1&sec=$2 [L]
RewriteRule ^([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)$ ?pri=$1&sec=$2&ter=$3 [L]
RewriteRule ^([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)/([a-zA-Z0-9_]+)$ ?pri=$1&sec=$2&ter=$3&qua=$4 [L]

</IfModule>

I've tried it both as a .htaccess and within the conf file. No luck. This worked on the previous 2.0 server, why not 2.2? Is it apache or ubuntu?

---

### Post by Nfzgrld on 2010-12-10
Ok, sorry for the misdirection there. It turns out the problem is not in the rewrite. The problem is somewhere else... cookies perhaps? In my initial var processing I find that everything is translated as it should be, except the "authentication" cookie. Seems like it's not getting set. Isn't that fun?

---

### Post by Nfzgrld on 2010-12-10
Found it! I'm getting the gets/posts/cookies via $_REQUEST in php. For some reason in this configuration the cookies are not getting pulled from the array. I'm assuming at this point it has something to do with a php.ini setting.

---

### Post by Nfzgrld on 2010-12-10
That was it. The request_order setting in php.ini was set to "GP". I use $_REQUEST as the php docs say it supports cookies as well. In this config it does not by default. I changed it to "GPC" and now all is wonderful...

---

