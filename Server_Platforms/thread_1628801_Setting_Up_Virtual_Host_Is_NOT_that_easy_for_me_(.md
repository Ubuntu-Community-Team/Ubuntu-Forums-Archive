---
title: "Setting Up Virtual Host Is NOT that easy for me :("
date: 2010-11-23
forum: Server Platforms
---

### Post by pijamaz on 2010-11-23
hi.
I'm trying to set up a virtual host on my ubuntu 9.04. I've tried many ways but all of them fail when I want to access my virtual host in my browser. where I can easily access "localhost" but cannot access virtual hosts (that I've created) such as : mydomain.com 
(I followed this article : [http://www.debian-administration.org/articles/357#website](http://www.debian-administration.org/articles/357#website) )
here is contet of my "/etc/apache2/sites-available/mydomain.com" file :

```
<VirtualHost * >
        #Basic setup
        ServerAdmin webmaster@mydomain.com
        ServerName www.mydomain.com
        DocumentRoot /var/www/realtime/docs

        <Directory /var/www/realtime/docs>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>
</VirtualHost>
```
 
and I don't know why  every virtual host that I create Does not work either. I use a2ensite command too. every thing seems ok but I don't know why I can't access my virtual hosts through my browser?! :(

---

### Post by Ryan Dwyer on 2010-11-23
Did you add a hosts entry for [www.mydomain.com](www.mydomain.com) so it resolves to your server?

---

### Post by wongo888 on 2010-11-23
If your web server machine is on your local area network at, say, 192.168.0.5 then you add this entry to your /etc/hosts file on the machine that you are browsing from (assuming you are browsing from a UNIX machine):

```

192.168.0.5 www.mydomain.com

```

If you are browsing from a Windows machine, then you need to add it to the Windows hosts file which on Vista is at C:\Windows\System32\drivers\etc\hosts

Your browser will then resolve your domain to your server IP and send the domain name as the Host header portion of the HTTP/1.1 GET request. That "Host" header is used by Apache to figure out which virtual host to use. The details of this transaction can be seen if you use LiveHTTPHeaders on Firefox.

[http://en.wikipedia.org/wiki/Virtual_hosting](http://en.wikipedia.org/wiki/Virtual_hosting)

I'm assuming that you have more than one machine.

---

### Post by Silverfox on 2010-11-23
I also found these two articles helpful...

[http://beginlinux.com/index.php/server_training/web-server/117-web-server/994-ubuntu-804-named-based-hosting]("http://beginlinux.com/index.php/server_training/web-server/117-web-server/994-ubuntu-804-named-based-hosting")

and the Apache docs were helpful as well (assuming of course that you're using Apache as your web server....)

[http://httpd.apache.org/docs/2.2/vhosts/]("http://httpd.apache.org/docs/2.2/vhosts/")

---

### Post by pijamaz on 2010-11-24
yep you are right the problem was /etc/hosts file. thanks all.

---

### Post by tad1073 on 2010-11-24
Example of /etc/apache2/sites-available/nameofsite

```
<VirtualHost *:80>
ServerName yurservername
ServerAlias namebasedvirtualhost.com
DocumentRoot /where/the/files/are
ServerAdmin name@email
DocumentRoot /where/the/files/are
</VirtualHost>
```Example of /etc/apache2/httpd.conf

```

NameVirtualHost address:port
<VirtualHost address:port>
ServerName yurservername
ServerAlias  namebasedvirtualhost.com
  DocumentRoot /where/the/files/arel
</VirtualHost>

<VirtualHost address:port>
  ServerName yurservername
  ServerAlias  namebasedvirtualhost1.com
  DocumentRoot /where/the/files/are
</VirtualHost>


<VirtualHost address:port>
  ServerName yurservername
  ServerAlias  namebasedvirtualhost2.com
  DocumentRoot /where/the/files/are
</VirtualHost>

<VirtualHost address:port>
ServerName yurservername
ServerAlias  namebasedvirtualhost3.com
DocumentRoot /where/the/files/are
</VirtualHost>
```

---

### Post by bistro on 2010-11-24
Hi

I am fumbling around trying to do this for the first time, I have the following code in these two files:

_/etc/apache2/sites-available/ioai-loca_l
NameVirtualHost *:80
<VirtualHost *:80>
ServerAdmin [email]webmaster@ioai-local.org[/email]
ServerName ioai-local
ServerAlias [www.ioai-local.org](www.ioai-local.org)
DocumentRoot /home/dave/public_html/ioai-local
</VirtualHost>


_/etc/hosts_
192.168.1.2	dave-VGN-AW31M-H	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	dave-VGN-AW31M-H	localhost6.localdomain6	localhost6
127.0.1.1	dave-VGN-AW31M-H
127.0.0.1     [www.ioai-local.org](www.ioai-local.org)

I've entered the a2ensite command and reloaded the server, but when I enter [www.ioai-local.org](www.ioai-local.org)  I am taken to the localhost index page in home/dave/public_html

Any advice much appreciated!

Regards

Dave

---

### Post by Ryan Dwyer on 2010-11-24
Your browser might have cached the previous content. Try clearing your browser cache or using a different browser.

Also, you shouldn't need to use the NameVirtualHost directive in your virtual host file because it's already in ports.conf.

---

### Post by bistro on 2010-11-26
Hi

thank you very much - that solved it!

Best wishes

Dave

---

