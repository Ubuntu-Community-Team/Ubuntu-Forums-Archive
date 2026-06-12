---
title: "Creating subdomains in apache -&gt; No user error"
date: 2009-01-11
forum: Server Platforms
---

### Post by m1ndpixel on 2009-01-11
Hi Guys,

Im adding:

<VirtualHost 76.10.x.x>
DocumentRoot /var/www/user
ServerName xxxxxxx.xxx
ServerAdmin [email]administrator@xxxxxx.xxx[/email]
ScriptAlias "/cgi-bin/" "/var/www/user/cgi-bin/"
ServerAlias user.xxxxxxx.xxx
</VirtualHost>

to /etc/apache/httpd.conf

However, instead of going to [http://hostname.com/user](http://hostname.com/user) directory, the subdomain is pointed to [http://hostname.com](http://hostname.com)

Any pointers as how I can fix this?
Thanks

---

### Post by volkswagner on 2009-01-11
I think you will be better off using name based virtual hosts, with individual config files.

> For example, sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite  Edit the new file to configure the new site using some of the directives described below.

The above is from [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html").

EDIT:  I may have made some incorrect assumptions...I should have asked some questions first.

I am not sure exactly what the following means.

> However, instead of going to [http://hostname.com/user](http://hostname.com/user) directory, the subdomain is pointed to [http://hostname.com](http://hostname.com)



What would you like to type in the browser address to get to the site in /user?
Do you have a separate site located in /var/www?
If yes how do you access that site?  adifferenthostname.com?
Do you have other hosts listed in /etc/apache2/httpd.conf?

I keep reading the post and it almost reads you want two sites with the same hostname.

---

### Post by osjak on 2009-01-11
> **m1ndpixel said:**
> Hi Guys, 

Im adding: 

<VirtualHost 76.10.x.x>
DocumentRoot /var/www/user
ServerName  xxxxxxx.xxx
ServerAdmin [email]administrator@xxxxxx.xxx[/email]
ScriptAlias "/cgi-bin/" "/var/www/user/cgi-bin/"
ServerAlias user.xxxxxxx.xxx
</VirtualHost>

to /etc/apache/httpd.conf

However, instead of going to [http://hostname.com/user](http://hostname.com/user) directory, the subdomain is pointed to [http://hostname.com](http://hostname.com)

Any pointers as how I can fix this? 
Thanks
Your *user* directory is your website root directory, so Apache doesn't see above it. If you want to use *[http://hostname.com/user](http://hostname.com/user)* format then you need to set your DucumentRoot to */var/www* then Apache will be able to access *user*.

---

