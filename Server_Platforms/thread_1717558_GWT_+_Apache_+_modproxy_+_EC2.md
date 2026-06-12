---
title: "GWT + Apache + modproxy + EC2"
date: 2011-03-30
forum: Server Platforms
---

### Post by thinrhino on 2011-03-30
Hello,

We have an application, whose frontend is in GWT and backend runs on an EC2 instance. The dev team uses windoze for development and I use ubuntu. I was trying to setup this environment on my machine, but I am running into errors.

The front-end in order to login and display data, interacts with the back-end server running on the ec2. To enable this, I was asked to insert the following code into apache2 configuration. 

```

<VirtualHost *:80>
    DocumentRoot "/var/www"
    ServerName ec2-xx-xxx-xxx-xxx.compute-1.amazonaws.com

    ProxyPass /abc http://ec2-xx-xxx-xxx-xxx.compute-1.amazonaws.com:8888/abc
    ProxyPassReverse /abc http://ec2-xx-xxx-xxx-xxx.compute-1.amazonaws.com:8888/abc
</VirtualHost>

```

After using google, I found out about the site-available / site-enabled configuration and hence put the above code into a file into site-available and did a2ensite and restarted apache. 

Now when I try to log into the front-end code on my machine, I keep getting a 404 error.

Any suggestion or idea what I am doing wrong? Pointers will be appreciated.

Regards
ThinRhino

---

