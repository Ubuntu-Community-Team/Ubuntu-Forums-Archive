---
title: "Ubunto Server Apache And host Proxy or Mod proxy reserver"
date: 2015-05-18
forum: Server Platforms
---

### Post by Andy_Asselin on 2015-05-18
Hello Not sure if this best fourm to ask but is possible to use mod proxy or mod proxy reserver to provide acess to local subnet via public face website  ? 

I seen some exsample for single ip not whole subnet or they any way to embed the local webserver in public server

---

### Post by SeijiSensei on 2015-05-18
What exactly do you mean by "provide access to local subnet?"  Do you want to serve pages from servers behind the firewall, or do you actually want to let people connect to network resources from a web page?  I'll say right now that I think the latter is a bad idea from a security perspective.

If you just want to have a public site that serves pages from a server behind it, then mod_proxy will do that, or you can just forward your router's port 80 back to the servers behind the firewall.

---

### Post by Andy_Asselin on 2015-05-18
Okay I try to explain better I have client that are open vpn into the server they all run a webserver for admin  on local ip such as 10.0.0.1  or  2 or 3 etc

on  the same box I have public face http server apache am look for away to embed the webpage from vpn clients into the public face webserver

---

### Post by SeijiSensei on 2015-05-18
The only way you could "embed" the webpage would be to have a public page that uses iframes.  The frame would need to reference the page on the VPN server.  I don't think you'd need to run mod_proxy in the case since the publicly-visible page should be able to see the VPN servers.  But the only way to know if this will work is through experimentation.

---

### Post by Andy_Asselin on 2015-05-19
that client that are  view  won't be on same network so embed page as iframe don't work the public server will be on on same network

---

### Post by SeijiSensei on 2015-05-19
If the machine can see the servers behind it, I think it would be possible to make a frame that loads from them.

Otherwise you could use something like PHP to accomplish the task.  You could write a public PHP script like this:
```

<?php
include("http://10.10.10.10/page1");
include("http://10.10.10.10/page2");
?>

```
with obviously a lot more content around those includes.

---

### Post by Andy_Asselin on 2015-05-20
Hello Nope  Nice idea on php no go 

I just to make clear layout of network is vpn into private subnet that server 

in 10.8.0.4 / 24

on same server is public acessable via public ip 

clients are not on same vpn  will only be able to acess via public face ip

---

### Post by SeijiSensei on 2015-05-20
I don't know why the PHP method doesn't work.  If you're on the server, can you open a URL on a VPN-connected machine behind it with a browser?  If so, then the same approach should work with PHP.  Maybe try using the [cURL functions]("http://php.net/manual/en/book.curl.php") in PHP?

---

### Post by Andy_Asselin on 2015-05-21
From the server on ssh I can acess the page across the vpn on the router

---

### Post by Andy_Asselin on 2015-05-21
apache logs say this in the error 


[Thu May 21 06:20:10.124909 2015] [:error] [pid 1425] [client 96.54.100.103:9624] PHP Warning:  include(): Failed opening 'https://10.8.0.4' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/html/test/test.php on line 2, referer:

---

### Post by Andy_Asselin on 2015-05-21
I add that I can do it webmin http tunnel  not that works for applications but it suggested the webserver can see content on both ip

---

### Post by SeijiSensei on 2015-05-21
Are you sure 10.8.0.4 supports SSL?  Is there a reason why you can't use plain-old HTTP over port 80?  I'm not sure how well something like include() works with SSL servers.

---

### Post by Andy_Asselin on 2015-05-21
it run on ssl or non ssl and  the script doesn't work

---

