---
title: "Apache2 Redirect"
date: 2018-02-28
forum: Server Platforms
---

### Post by MTBowhunter on 2018-02-28
Hi!

I have my Apache2 server setup and it will serve web pages successfully internally.  When you try to browse to the external IP, it directs me to the correct internal IP but then the web page times out....  

My web directory is:

/var/www/html/moodle/

I have set the sites-available 000-default.conf file as follows:

ServerName 172.16.X.XX
DocumentRoot /var/www/html/
RedirectMatch ^/$ [http://172.16.X.XX/moodle/index.php](http://172.16.X.XX/moodle/index.php)

I added the following to apache2.conf....

Listen 80

NameVirtualHost 172.16.X.XX:80
NameVirtualHost 206.127.XXX.XX:80

<VirtualHost 172.16.X.XX 206.127.XXX.XX>
DocumentRoot /var/www/html/
ServerAlias  XXXXXXXX
</VirtualHost>

My firewall will successfully point them to our web server...  It will display the root directory of the html directory...  When you try and follow any links from that page it resolves them to our internal IP address and times out....  

Any ideas would be greatly appreciated...  I've tried my Google Foo and have failed.  

I owe someone a beer or three! 

Cheers,


Joe

---

### Post by volkswagner on 2018-02-28
I'm curious where you found documentation to setup your
config files as you have.

There's a lot of information on the Internet, unfortunately it's not all good.
I've setup several Apache servers on Ubuntu. I can't remember the last time I've
had to edit /etc/apache2/apache2.conf.

I can't even say if it's wrong, but it's not typical in my opinion.

The sticky at the top of this forum is helpful
Take a look at the [web server documentation]("https://help.ubuntu.com/14.04/serverguide/httpd.html").

I don't have any experience with Moodle. Some web applications expect the
url or address to be the same as when you set it up. This is why it's useful to use domain names
over ip addresses. You can do a lot with DNS settings and /etc/hosts to direct queries
to the server's you'd like. When you hard code an ip address as part of the domain
name or as part of a web applications config, you may get undesired results.

You may want to look and see if Moodle has anything like an alias directive.

You should also consider a rewrite vs redirect if the above is true and your
Moodle server is expecting a specific url.

---

### Post by MTBowhunter on 2018-03-01
Volkswagner,

Thanks for the reply.  I will have to check with Moodle and see.  This is a test server for our Moodle site, currently administration does not want to put the money out to register a domain name for our Moodle site.  Ideally, I agree, I would do exactly like you say and point it to the domain name and avoid any IP issues.  As for where I found the documentation telling me to make changes to Apache2.conf..  I believe it was from [https://httpd.apache.org/docs/trunk/vhosts/examples.html](https://httpd.apache.org/docs/trunk/vhosts/examples.html).  It does not say to modify the Apache2.conf file here but this is the same info.  I believe I found the info on editing the Apache2.conf file on DigitalOcean.  

Thanks for the link to the Ubuntu Apache config.  I will check that out too.  

Cheers!

Joe

---

### Post by SeijiSensei on 2018-03-01
If you set the virtual host's ServerName to its IP address, it won't match incoming requests forwarded through the router using its external address.  

You can register a domain name for ten bucks or so these days.  Surely the "administration" can afford that.

---

### Post by MTBowhunter on 2018-03-01
After I reviewed the information that Volkswagner provided, I saw that the ServerName would cause conflicts in the way I had it set up. I believe that my error lies someplace within Moodle.  I may have to register my changes with our current Domain registry. 

I guess what it boils down to is not so much affording the domain.  They own that.  It's purchasing an SSL certificate and making the appropriate contacts. I work for a school district.  We have our school website registered several places as we are part of a state system.

---

### Post by SeijiSensei on 2018-03-01
Will this site serve members of the general public, or an identifiable group?  If the latter, you could opt for a self-signed certificate and tell your users they should expect the browser to complain until they accept the cert.

---

### Post by MTBowhunter on 2018-03-01
I ended up fixing all of my errors on the Apache end of things.  That worked perfectly.  Moodle was not liking the fact I didn't use a FQDN... SO I registered with No-IP.com and got one for testing.  That worked perfectly.  So for others running into similar issues, check that out.

---

