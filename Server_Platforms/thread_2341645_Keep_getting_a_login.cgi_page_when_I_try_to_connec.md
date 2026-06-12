---
title: "Keep getting a login.cgi page when I try to connect to my public IP"
date: 2016-10-30
forum: Server Platforms
---

### Post by jdshelby on 2016-10-30
Hi All, 

I just started trying to set up an Apache2 server for my business in Vietnam. I went through the steps, installed everything, and it all looks like I should as long as I use the 127.0.0.1 IP address. But as soon as I  try and direct my browser to my external, public IP, I get sent to what I think is my router administration page (GPON Home Gateway Login) page. All I get are the router settings.  Why can't I get the Apache server splash page on my public ip address.

I'd love any guidance you all have to offer!  Thanks.

Justin

Oh, and I'm using the latest LTS version of Desktop Ubuntu, 16.04

---

### Post by darkod on 2016-10-30
1. For a webserver that will be public on the internet it is much better to use the Server version, not the Desktop. The Desktop has more unnecessary applications and more security exploits can be found.

2. If you are getting the GPON router login page, that means the router is configured to be accessed from outside on the public IP. That is also a security risk and you should disable that in the router config. After that you should forward port 80 and port 443 to the private IP of your server/desktop behind the router. That is done in the router config too.

Don't forget that sometimes ISPs block port 80 to prevent people running webservers. If they are doing that, you will not be able to access your server on port 80 from the outside. But since you can reach the router login page I don't think this is the case.

---

