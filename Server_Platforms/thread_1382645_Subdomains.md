---
title: "Subdomains"
date: 2010-01-16
forum: Server Platforms
---

### Post by barnesey on 2010-01-16
HI,
I have been learning ubuntu server to play around with and am getting used to it. I would like to now make a local test webserver with sub domains, eg site1.localhost or fourms.localhost etc or if possible site1.testserver. I have done some googleing but have not gotten very confused on how to do it.
 
I am planning on using Ubuntu Server 8.0.4LTS with LAMP, but do i need DNS or any other application installed. I have setup up a simple web server with LAMP and SSH. The machine has a resverd IP address 
 
Once i have the server up and running how to i create/setup the subdomains. 
 
Barnesey

---

### Post by a9k3d on 2010-01-21
There are two part to setting up "play" subdomains: adjusting the testing machines /etc/hosts file and configuring apache.

First is a trick to "playing" with subdomains when you don't have them setup or even have a domain of your own is to use the /etc/hosts file on your testing machine to create the association between the name and local ip.

SO you can make one word names like I do for internal virtual servers:
```
192.168.1.10  test1
192.168.1.10  mythweb
192.168.1.10 ampache
192.168.1.10 zina
```
The above assumes your server is at 192.168.1.10

Now, you need to adjust your apache config on the server machine. 
[B]cd /etc/apache2
sudo nano ports.conf[/B] 
edit ports config file to just contain:
```
NameVirtualHost *
Listen 80

```
Save the file.

Next, you will be working in **/etc/apache2/sites-available**. cd there.
First edit the file named **default** change the top line to say **<VirtualHost _default_>** and make sure bottom line is **</VirtualHost>**

Then create a new file for your first "virtual" site called **test1**
```
<VirtualHost 192.168.1.10:*>
  ServerName test1
  DocumentRoot "/var/www/test1"
</VirtualHost>

```

Run **sudo a2ensite test1** to enable the site.

Next, create a directory for the test1 site under /var/www called test1. **mkdir /var/www/test1**
Make sure the owner is you and the group www-data. **sudo chgrp www-data /var/www/test1**
Create an index.html file inside the /var/www/test1 folder. Make sure the group is www-data. B]sudo chgrp www-data /var/www/test1/index.html[/B]
Edit the /var/www/test1/index.html file to have a minimal web page - for example:
[HTML]<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>test1</title>
</head>
<body>
<h1>Test1</h1>
<p>It lives!</p>
</body>
</html>[/HTML]
Finally reload apache - I use **sudo apache2ctl graceful** usually.

Now back to the testing machine (which can be the server is you have installed a desktop). Launch Firefox, go to  [http://test1](http://test1)
You should see your new virtual site.
Good luck!

---

### Post by barnesey on 2010-04-11
Thanks for the reply, sorry i have not replied as have had problems with the server i was using but now have come back around to my testing.
 
Anyway, thank you a9k3d that was very easy to understand and complete and worked first time,

---

