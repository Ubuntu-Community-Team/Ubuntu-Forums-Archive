---
title: "rewrite works, but errors written?"
date: 2006-12-09
forum: Server Platforms
---

### Post by JackDog on 2006-12-09
Sounds backwards but its true. 

I have mod_rewrite working properly on a system, however errors are being written to the apache logs like they aren't. Almost seems like apache is processing the rewrite after first trying to load the page. An error gets written and then before the response is sent, the rewrite rule fires and the proper page is retrieved and returned...

Any ideas?
](*,)

---

### Post by JackDog on 2006-12-11
bump

---

### Post by moorezilla on 2007-04-24
I think I may have a similar error. I just updated to Feisty and now my apache error.log is filling up with:

[Tue Apr 24 07:56:32 2007] [warn] RewriteCond: NoCase option for non-regex pattern '-f' is not supported and will be ignored.
[Tue Apr 24 07:56:32 2007] [warn] RewriteCond: NoCase option for non-regex pattern '-d' is not supported and will be ignored.

even though the rewrite is working. I have an .htaccess file with this in it:

options +FollowSymLinks
RewriteEngine on
RewriteBase /

# 301 Redirect all requests that don't contain a dot or trailing slash to
# include a trailing slash
RewriteCond %{REQUEST_URI} !/$
RewriteCond %{REQUEST_URI} !\.
RewriteRule ^(.*) %{REQUEST_URI}/ [R=301,L]

# Rewrites urls in the form of /parent/child/
# but only rewrites if the requested URL is not a file or directory
RewriteCond %{REQUEST_FILENAME} !-f [NC]
RewriteCond %{REQUEST_FILENAME} !-d [NC]
RewriteRule ^(.+)$ chs/index.php?page=$1 [QSA]

Any ideas how I can get Apache to stop seeing this as an error and filling up its error.log with the two lines:

[Tue Apr 24 07:56:32 2007] [warn] RewriteCond: NoCase option for non-regex pattern '-f' is not supported and will be ignored.
[Tue Apr 24 07:56:32 2007] [warn] RewriteCond: NoCase option for non-regex pattern '-d' is not supported and will be ignored.

Thanks,
am

---

### Post by jtc on 2007-04-24
Well, perhaps it is just me, but it seems as if Apache is telling you exactly what the problem is.

Hint: What does [NC] stand for, and why would you need it where you've put it?

---

### Post by moorezilla on 2007-04-24
gahhh... sorry... thanks.

---

