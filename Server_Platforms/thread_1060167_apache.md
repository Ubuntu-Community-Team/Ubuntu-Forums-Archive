---
title: "apache"
date: 2009-02-04
forum: Server Platforms
---

### Post by Pakia on 2009-02-04
I have installed an apache2 server and administer with webmin.
If I type localhost it says "it works"
If I type servername it says "it works"
If I type my local IP of the server it says "it works"
I created 3 virtualhosts
If I type [http://virtualhostname.com](http://virtualhostname.com) it starts to search opendns (my dns service) and I do not get the local file as I used to.
Under the virtual host in webmin I have tried standard httpd.conf as well as new file under virtual server directory /etc/apache2/site-available
Both have the same effect
virtual servers are listed under my network configuration dns client options search domains

If I start apache it says "could not realiably determine the servers fully qualified domain name, using 127.0.1.1 for server name. 

Any advice appreciated

---

### Post by spiderbatdad on 2009-02-04
Just add your fqdn to httpd.conf
```
ServerName your.domain.com
```

---

### Post by Pakia on 2009-02-04
Thanks for that but the issue of when I type a virtualhostname.com in the browser it still does not show my local file?

Any help appreciated

---

### Post by spiderbatdad on 2009-02-04
WAN IP incorrectly registered? What message from your browser when the expected page fails to load?

---

