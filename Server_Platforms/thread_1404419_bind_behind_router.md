---
title: "bind behind router"
date: 2010-02-11
forum: Server Platforms
---

### Post by vasilev on 2010-02-11
hello , 
i see one tread here , but i dont see an answer :) 
so .. this is my problem :

I have real Ip and paid domain name . 
I have router , i have set port forwarding (port 53) to the internal ip of my server . 
I have read this : 

[http://www.mutinydesign.co.uk/scripts/configure-automatic-subdomains-with-apache/](http://www.mutinydesign.co.uk/scripts/configure-automatic-subdomains-with-apache/)

and from the server when i type in firefox for example test.domain.com - it opens domain.com . But from external (from other pc , other network) it doesn't . 

Can you help me .. Where I am wrong ? and where to put the rewrite rule :

	RewriteEngine on 
	RewriteCond %{HTTP_HOST} !^[www.*](www.*) [NC] 
	RewriteCond %{HTTP_HOST} ^(.*)\.domain.com
	RewriteCond /var/www/localhost/%1 -d 

in /var/www/.htaccess or in other place .

thank you . 

	RewriteRule ^(.*) /%1/$1 [L]

---

### Post by doas777 on 2010-02-11
is your domain name on the registrars dns servers set to point to your server?

---

### Post by vasilev on 2010-02-11
yes .. the domain name points to real ip adress .

this write in error.lof of apache , when i type test.domain.com from the server :


[client IP] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.

and the page that was opened says:
Internal Server Error


The server encountered an internal error or misconfiguration and was unable to complete your request.

In .htaccess i write this :

RewriteEngine on 
RewriteCond %{ENV:rwdone} !^yes$ 
RewriteCond  %{HTTP_HOST} !www\.example\.com 
RewriteCond %{HTTP_HOST}  ^(www\.)?([a-z0-9\-]+)\.example\.com 
RewriteRule (.*) /%2/subdomain  [E=rwdone:yes,L]

---

