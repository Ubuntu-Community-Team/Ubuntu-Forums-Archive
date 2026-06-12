---
title: "Apache2: Change default Vhost &quot;http://ubuntu.ubuntu-domain/&quot;"
date: 2010-02-07
forum: Server Platforms
---

### Post by robembra on 2010-02-07
Hi & yes im new to Ubuntu,

I have just installed LAMP on my Ubuntu and was wondering could/how you change the default Vhost "http://ubuntu.ubuntu-domain" to you own choice and check if there are any others?

Also I just wanted apache, php, mysql and myphpadmin to be only accessed through 127.0.0.1/localhost could you point me in the right direction?

Thanks in advanced :)

---

### Post by robembra on 2010-02-08
Please anyone...?

---

### Post by yogesh.girikumar on 2010-02-10
Hi,

You can listen to a specific ip by setting that in the Listen directive.

You have to edit the /etc/apache2/ports.conf

Change the line that starts with the 'listen' directive. Mine says:

```
Listen 0.0.0.0:80
```Change it to listen to only the desired IP.

```
Listen 127.0.0.1:80
```For specifying and verifying the virtual hosts served by apache: Look at the file /etc/apache2/sites-enabled/000-default

Looking at how many 

 <virtualhost> 
[..]  
</virtualhost> 

sections there are in the file will give you
 an idea of how many virtual hosts are being served by Apache.

To change the VirtualHost name, you have to edit the directive called 'ServerName' and add it if 'Se
rverName' directive is not present.

Link: [http://httpd.apache.org/docs/2.0/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.0/mod/core.html#virtualhost)
Link: [http://httpd.apache.org/docs/2.0/vhosts/details.html](http://httpd.apache.org/docs/2.0/vhosts/details.html)
Link: [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

---

