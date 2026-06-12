---
title: "xampp virtual hosts problem"
date: 2008-09-29
forum: Server Platforms
---

### Post by rwalkerarn on 2008-09-29
Hi everyone!

I am running xampp on the latest version of ubuntu.  I have successfully setup a couple of joomla websites to test on localhost and over the local network.

Once I was happy that one of them was ready I decided to shut down my windows server (also running xampp) and switch to my ubuntu box.

I turned on the line in the httpd.conf that links to the virtual hosts file ( Include etc/extra/httpd-vhosts.conf ) and then added the following into the httpd-vhosts.conf file : ...

```

<VirtualHost *:80>
ServerName www.colchestersamaritans.org
DocumentRoot /opt/lampp/htdocs/samaritans
</VirtualHost>

<VirtualHost *:80>
ServerName www.test.johnrayjuniors.com
DocumentRoot /opt/lampp/htdocs/johnrayjuniors
</VirtualHost>

```

This is exactly what I had done successfully using the windows install of xamp, however now when you go to the address you get redirected to the xampp folder that asks you for your lampp password. ie if you go to [www.colchestersamaritans.org](www.colchestersamaritans.org) you get [www.colchestersamaritans.org/xamp/](www.colchestersamaritans.org/xamp/)

Anyone got any ideas what could be causing this?

---

