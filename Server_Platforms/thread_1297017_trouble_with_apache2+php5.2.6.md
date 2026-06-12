---
title: "trouble with apache2+php5.2.6?"
date: 2009-10-21
forum: Server Platforms
---

### Post by yilin on 2009-10-21
I'm running ubuntu 9.04 upgraded from 8.10 on my d630 laptop as a developer box.

The apache2+php5 system is kind of working (phpmyadmin runs ok on it), but for the following script, it behaves quite differently than my win2003 server + php5.2.5 and redhat + php5.1:

[COLOR="Gray"]<?php
// ck.php
$ckVar = $_COOKIE['test'];
if(isset($ckVar)) {
  echo "cookieValue is ",$ckVar;
} else {
  echo "cookie is not set";
}
SetCookie('test','123',time()+12,'/');
?>[/COLOR]

The response of it to the request [http://localhost/ck.php](http://localhost/ck.php) is

[COLOR="Red"]cookie is not set
Warning: Cannot modify header information - headers already sent by (output started at /home/www/htdocs/ck.php:7) in /home/www/htdocs/ck.php on line 8[/COLOR]

and reload the page will not change the output.

While for my other systems, the same script will return a page saying 'cookieValue is 123' after a reloading. 

I know any setting to header should be done before content. But why my other systems can tolenrate this and automatically handle this correctly?

Could anyone help me understand how to fix my developer system? Or let me know where to find the solution? 

Thanks a lot.

The anorying thing is that my developer box breaks my ad image generating code in the same way!

---

### Post by cdenley on 2009-10-21
Your other server probably had output buffering turned on.
```

cdenley@ubuntu:~$ grep -B 7 ^output_buffering /etc/php5/apache2/php.ini
; Output buffering allows you to send header lines (including cookies) even
; after you send body content, at the price of slowing PHP's output layer a
; bit.  You can enable output buffering during runtime by calling the output
; buffering functions.  You can also enable output buffering for all files by
; setting this directive to On.  If you wish to limit the size of the buffer
; to a certain size - you can use a maximum number of bytes instead of 'On', as
; a value for this directive (e.g., output_buffering=4096).
output_buffering = Off

```

---

### Post by yilin on 2009-10-21
> **cdenley said:**
> Your other server probably had output buffering turned on.

Yes! That's the difference! Thanks a lot Cdenley

---

