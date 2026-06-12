---
title: "One domain redirect to another on the background"
date: 2014-12-16
forum: Server Platforms
---

### Post by rastacongo on 2014-12-16
Hello,

I've got 2 domains, the long.domain.com and the short.com.

I would like when the user type on the browser short.com/ID(a code like df6g8df) to redirect to [COLOR=#2E8B57][FONT=Monaco]https://long.domain.com/public.php?service=shorty_relay&id=$1

[/FONT][/COLOR]I know I have to use the mod_proxy.

By using this lines in my httpd.conf, I was able to redirect on the root of the long.domain.com

> <VirtualHost *:80>
    ServerAdmin [EMAIL="email@address.com"]email@address.com[/EMAIL]
    DocumentRoot /var/www/dir/public_html
    ServerName [www.short.com]("http://www.short.com")
    ServerAlias short.com
    [FONT=Consolas]ProxyPass / [https://www.long.domain.com](https://www.long.domain.com)
[/FONT][FONT=Consolas]    ProxyPassReverse / [https://www.long.domain.com](https://www.long.domain.com)[/FONT]    
    ErrorLog /var/www/dir/error.log
</VirtualHost>
But the only functionality I need form the short domain is to redirect here: [COLOR=#2E8B57][FONT=Monaco]https://long.domain.com/public.php?service=shorty_relay&id=$1 [/FONT][/COLOR]only when the ID at the end is valid, e.x: short.com/dfg79df8

I know I have to use somehow this regex here: [FONT=Menlo]ProxyPassMatch ^/([A-Za-z0-9]{4,12})$ https://www.long.domain.com/public.php?service=shorty_relay&id=$1[/FONT]

[FONT=Menlo]But I dont know how to combine ProxyPass and ProxyPassMatch, to get the result I need. Every combination I've tried failed.

Any ideas?[/FONT]

---

### Post by koenn on 2014-12-19
you can't do this with mod_proxy, as you want to do more that simply map one domain name onto another. 
you'll need to instruct your web(proxy)server to construct a new URL based on specific parts of the original request.
You need mod-rewrite for that

this should get you started : [http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

---

