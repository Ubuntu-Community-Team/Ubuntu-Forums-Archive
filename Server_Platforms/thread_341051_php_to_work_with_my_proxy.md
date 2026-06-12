---
title: "php to work with my proxy"
date: 2007-01-18
forum: Server Platforms
---

### Post by denday on 2007-01-18
Hi
I run apache/php on my server all working fine but my internet connection is over a proxy server. PHP Scripts that i have wrote i.e ( RSS News Feeder etc ) Require outbound internet access for the xml files etc.

How can i get php to work with my proxy so it all works correctly a setting in the php.ini ?

Thanks

---

### Post by asimonetta on 2008-02-26
I don't understand what you mean, but perhaps I can tell you my experience with a MS ISA proxy (It was harder to skip!). In this case is very very usefull the ntlmaps proxy server ([http://ntlmaps.sourceforge.net/](http://ntlmaps.sourceforge.net/)) that talk correctly with the MS proxy and the feeder php program ([http://www.wp-plugins-db.org/plugin/feeder/](http://www.wp-plugins-db.org/plugin/feeder/)).
You have only to change the connection mode because it use the file() function instead the curl one.
If interest you I can post my feeder.php.

---

### Post by faulkes on 2008-02-26
> **denday said:**
> Hi
I run apache/php on my server all working fine but my internet connection is over a proxy server. PHP Scripts that i have wrote i.e ( RSS News Feeder etc ) Require outbound internet access for the xml files etc.

How can i get php to work with my proxy so it all works correctly a setting in the php.ini ?

Thanks

PHP works on the local system, when you execute php code and it requests
somthing offsite (url, ftp, etc..) you are invoking methods/functions within
php.  

There is, to my knowledge no php.ini setting which will allow you to 
specify a proxy server to use, as it's not the intended purpose of php.

PHP does however have specific programming functions to access
urls / data through a proxy server.

[http://ca3.php.net/manual/en/http.request.options.php](http://ca3.php.net/manual/en/http.request.options.php)

This question is more suitable to a php based group rather than the 
Server Platforms as it is programming related.

Faulkes

---

