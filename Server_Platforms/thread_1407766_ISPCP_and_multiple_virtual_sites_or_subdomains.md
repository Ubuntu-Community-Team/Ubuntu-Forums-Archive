---
title: "ISPCP and multiple virtual sites or subdomains"
date: 2010-02-15
forum: Server Platforms
---

### Post by jvmcintyre on 2010-02-15
I am very new to linux. I know enough to get myself in trouble. I have installed ubuntu 9.10 with apache, mysql, phpmyadmin, and ispcp.

Hardware is an IBM X-series 8676. Dual 2.8 Xeon. 2.5GB Ram. 330GB total HDD.

So if I change the virtual host through webmin and point the ispcp to port 8080, then I get the default: It works page.

What I would like to do is have my domain point to a webpage where everyone would go to when you put in my domain and if its someone that I will allow access to ispcp then there will be a link on the first page that will go to ispcp login or if the client just enters something like [www.domain.com/ispcp](www.domain.com/ispcp).


I have beat my head against the wall trying different things, however I am reluctant to make too many changes because I dont want to break my entire box.


Can anyone give me any guidance?

---

### Post by jvmcintyre on 2010-02-15
Lots of views but no replies. Am I missing something simple here?

I deleted all the virtual hosts like a dummy. Now my ispcp admin page is not working. It does display the default "Its Working! page now. So, I am wondering if someone can give me some advice on how I can rebuild the virtual server links through webmin or cli. Or if you know a good resource site where I can see some examples or a tutorial of similar configs.


Thanks in advance!

---

### Post by jvmcintyre on 2010-02-16
*bump*

---

### Post by Satoru-san on 2010-02-17
Hello welcome to the forums.

I was confused by your title.

It seems that you do not want vhosts, instead you want redirects. You can do everything you mentioned above in php. You can have it redirect your main index.php page into /path/to/page.php, in that page it will look at your remote IP (using PHP) and then determine wheather it will print that link to the page.

the index.php code

[php] <?php header("location:http://www.url.com"); ?>[/php]the other page code

[php]<?php 
...
$ip=$_SERVER['REMOTE_ADDR'];
if ($ip = "::1" || $ip = "127.0.0.1") {
?><a href="/path/to/program.html">super secret link</a><?php
}else{
...
?>
[/php]

---

### Post by jvmcintyre on 2010-02-17
Not too sure I understand what you mean. I do not know too much about php. When i go to [www.domain.com]("http://www.domain.com"), it goes to my ispcp login page. I dont want it to go there first. In my apache config under virtual servers, there is an entry for this:

Handles all requests to the address 192.168.1.2 on port 80.
 **Address** 192.168.1.2
**Port** 80 **Server Name** admin.ubuntu.webviewhosting.com
**Document Root** /var/www/ispcp/gui

I would like this to go to a main page that would not be the login page for the ispcp management and maybe have a link on that page where I can redirect to the login page. Maybe I just dont know enough about this, but I guess you have to start somewhere!!



Nevermind.. Silly me! 

I just added some redirects and its working now. I have to put [www.domain.com/webviewhosting](www.domain.com/webviewhosting) but i will figure out how to switch the two around so it functions how I want it to

---

