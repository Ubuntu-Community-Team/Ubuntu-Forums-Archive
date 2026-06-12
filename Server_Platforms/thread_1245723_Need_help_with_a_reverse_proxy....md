---
title: "Need help with a reverse proxy..."
date: 2009-08-20
forum: Server Platforms
---

### Post by devin0 on 2009-08-20
I have two webservers on my ip address, one is my ubuntu box one a windows box. Currently to get to my windows box I have to type in my ip address and then a port number (8080). I belive I can get it setup with a reverse proxy so I only have to type -

[http://myip/server1](http://myip/server1) to get to my ubuntu box
[http://myip/server2](http://myip/server2) to get to my windows box

What would be the best way to do this?

---

### Post by paul.maddox on 2009-08-21
You can do this easily with Apache2 on your Ubuntu box.

The one problem with your idea is that this does make your windows site dependant on your Ubuntu box - but I guess you realise this already.

```


# Make sure apache2 is installed
$ sudo apt-get install apache2

# Enable mod_proxy
$ sudo a2enmod proxy

# Now create the following file:
$ sudo vi /etc/apache2/conf.d/proxy_rules.conf

# And add the following lines to setup /windows to point to your box (replace 10.0.0.1 with your windows box IP):

ProxyPass /windows http://10.0.0.1
ProxyPassReverse /windows http://10.0.0.1

# Then reload apache2 to apply config
$ sudo /etc/init.d/apache2 reload


```

:)

---

### Post by devin0 on 2009-08-21
I did everything you said to do but when i try to go to 
[http://myip/windows](http://myip/windows) 

I get an error saying:
forbidden, you do not have permission to view /windows on this server.

---

