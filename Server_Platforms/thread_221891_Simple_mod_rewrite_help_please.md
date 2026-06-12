---
title: "Simple mod_rewrite help please"
date: 2006-07-24
forum: Server Platforms
---

### Post by hagen00 on 2006-07-24
Hi 

I need some mod rewrite help...I've been searching around, but can't find an example of what I want to do. 

Very simple. I just want to redirect any [http://www.site.com](http://www.site.com) requests to [https://www.site.com](https://www.site.com)

Please can someone tell me how to do that. And I can put the rules into my <VirtualHost> directive right?

Thanks

H

---

### Post by hagen00 on 2006-07-24
Ok, figured it out by myself...

In my Virtual Host file

I put in 
<Directory>
Options +FollowSymlinks

RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteRule (.*) [https://mydomain.com/](https://mydomain.com/) [R]

</Directory>

I tried a couple of other alternatives, but this one is the only one i got working.

---

### Post by LordHunter317 on 2006-07-24
The far simpler solution is just:```
Redirect / https://www.site.com/
```In the non-SSL vhost and nothing in the SSL vhost.

---

### Post by hagen00 on 2006-07-24
Ah, thanks...I changed it to that. Much simpler!

---

