---
title: "how to setup reverse proxyapache2 drupal problem clean urls"
date: 2010-04-16
forum: Server Platforms
---

### Post by tapas_mishra on 2010-04-16
Hi
 I have a scenario.A domain [www.mydomain.com](www.mydomain.com)
then there are 4 private computers on which applications are hosted at port 80.
So when some one from outside access the site it look 
as [www.mydomain.com/site1](www.mydomain.com/site1)
Now  in apache2.conf where [www.mydomain.com](www.mydomain.com) is hosted 
I added 
```

ProxyPass /site1 http://192.168.0.2
ProxyReversePass /site1 http://192.168.0.2

```
is it correct ?
I am able to see [www.mydomain.com/site1](www.mydomain.com/site1)
but when some one logs in from internet to [www.mydomain.com/site1](www.mydomain.com/site1)
 it is redirecting to [www.mydomain.com](www.mydomain.com) and not taking to page where a successful login will go 
in [www.mydomain.com/site1](www.mydomain.com/site1) 
what should I check or do ?

---

### Post by tapas_mishra on 2010-04-17
I am posting a solution since by now I have solved the problem.
[http://swik.net/MySQL/Planet+MySQL/Operating+a+Drupal+Site+behind+a+Reverse+Proxy+Server+(Apache)/dcslr](http://swik.net/MySQL/Planet+MySQL/Operating+a+Drupal+Site+behind+a+Reverse+Proxy+Server+(Apache)/dcslr)

I am posting so that if some one else faces the same problem they may get a solution.Which is mentioned on the above link you can go there directly and read it.
```

When you install drupal on a server which is behind apache reverse proxy you need to tell that drupal installation about the presence of reverse proxy in your nework.
That is the core of the problem.
To achieve this you need to do do following
in your drupal installation folder go to sites/default/settings.php
and change the following

$base_url="http://www.mydomain.com/;
then 
$cookie_domain = 'proxyserver.yourdomain.com';

if above both are same then place them same values
then
uncomment 

$conf = array(

then
uncomment 
'reverse_proxy' => TRUE,

then 
'reverse_proxy_addresses' => array('192.168.0.1',),
replace it by IP of your apache reverse proxy 

and uncomment below it
);

```
Hopefully it should work.
Keywords to search for this are if you are using drupal
"drupal behind apache reverse proxy"

You can get same problem if you do not use drupal the thing is any web server running behind a proxy needs to know how to handle requests which are forwarded by proxy.
Some one if comes across same situation do reply here make a blog etc it will help others.

---

