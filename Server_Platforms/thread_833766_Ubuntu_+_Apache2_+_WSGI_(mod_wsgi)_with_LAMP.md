---
title: "Ubuntu + Apache2 + WSGI (mod_wsgi) with LAMP"
date: 2008-06-18
forum: Server Platforms
---

### Post by alecwh on 2008-06-18
I'm making this small tutorial so others can be spared from researching how to get mod_wsgi working with Apache. It took me quite awhile to find out because there was no documentation indexed on Google (it seemed like).

Assuming you have Apache2, PHP, mySQL, and phpmyadmin installed, you'll need to install the wsgi module:

```
sudo apt-get install libapache2-mod-wsgi
```

This should install the module. Now to activate it:

```
sudo a2enmod mod-wsgi
```

Now to restart Apache2:

```
sudo /etc/init.d/apache2 restart
```

Okay, we have the module installed and ready to go, but now we need to associate the module with the ".wsgi" extension on your server. This will make files with a .wsgi extension use the wsgi module for processing. Open up /etc/apache2/sites-available/default:

```
sudo gedit /etc/apache2/sites-available/default
```

Around line 10, you should have something like this:

```

<Directory /var/www/>
	Options Indexes FollowSymLinks MultiViews ExecCGI
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

```

Replace it with this:

```

<Directory /var/www/>
	Options Indexes FollowSymLinks MultiViews ExecCGI

	AddHandler cgi-script .cgi
	AddHandler wsgi-script .wsgi
	
	AllowOverride None
	Order allow,deny
	allow from all
</Directory>

```

If you don't want to replace the whole thing, all you need to do is add "ExecCGI" to the Options list, and add the handlers cgi-script and wsgi-script (shown above).

That's it. Restart Apache:

```
sudo /etc/init.d/apache2 restart
```

An example program:
```
def application(environ, start_response):
    status = '200 OK' 
    output = 'Hello World!'

    response_headers = [('Content-type', 'text/plain'),
                        ('Content-Length', str(len(output)))]
    start_response(status, response_headers)

    return [output]
```

**You're done!**

If you want to make "index.wsgi" act as an index for your directory (much like index.htm, index.html, index.php), open up /etc/apache2/mods-enabled/dir.conf:

```
sudo gedit /etc/apache2/mods-enabled/dir.conf
```

And change line 3 (the line that has the DirectoryIndex) to:

```
          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm index.wsgi
```

Okay, that's it. Please reply to the thread if you see any problems or possible improvements. I didn't spend a whole lot of time on this... so I hope everything works. PHP and wsgi files should run next to each other perfectly.

---

### Post by alecwh on 2008-06-26
Okay, I've been using this for a number of days, and it works perfectly. The only issue that I've had is having both mod_wsgi AND mod_python. Does anybody know how to do this?

---

### Post by cmnorton on 2011-01-26
> **alecwh said:**
> I'm making this small tutorial so others can be spared from researching how to get mod_wsgi working with Apache. It took me quite awhile to find out because there was no documentation indexed on Google (it seemed like).

Assuming you have Apache2, PHP, mySQL, and phpmyadmin installed, you'll need to install the wsgi module:

```
sudo apt-get install libapache2-mod-wsgi
```This should install the module. Now to activate it:

```
sudo a2enmod mod-wsgi
```Now to restart Apache2:

```
sudo /etc/init.d/apache2 restart
```Okay, we have the module installed and ready to go, but now we need to associate the module with the ".wsgi" extension on your server. This will make files with a .wsgi extension use the wsgi module for processing. Open up /etc/apache2/sites-available/default:

```
sudo gedit /etc/apache2/sites-available/default
```Around line 10, you should have something like this:

```

<Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews ExecCGI
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

```Replace it with this:

```

<Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews ExecCGI

    AddHandler cgi-script .cgi
    AddHandler wsgi-script .wsgi
    
    AllowOverride None
    Order allow,deny
    allow from all
</Directory>

```If you don't want to replace the whole thing, all you need to do is add "ExecCGI" to the Options list, and add the handlers cgi-script and wsgi-script (shown above).

That's it. Restart Apache:

```
sudo /etc/init.d/apache2 restart
```An example program:
```
def application(environ, start_response):
    status = '200 OK' 
    output = 'Hello World!'

    response_headers = [('Content-type', 'text/plain'),
                        ('Content-Length', str(len(output)))]
    start_response(status, response_headers)

    return [output]
```**You're done!**

If you want to make "index.wsgi" act as an index for your directory (much like index.htm, index.html, index.php), open up /etc/apache2/mods-enabled/dir.conf:

```
sudo gedit /etc/apache2/mods-enabled/dir.conf
```And change line 3 (the line that has the DirectoryIndex) to:

```
          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm index.wsgi
```Okay, that's it. Please reply to the thread if you see any problems or possible improvements. I didn't spend a whole lot of time on this... so I hope everything works. PHP and wsgi files should run next to each other perfectly.

I tried the first two commands. 
In between the two I restarted the apache server, but get this error after issuing second command
dbadmin@steamboy:~$ sudo a2enmod mod-wsgi
ERROR: Module mod-wsgi does not exist!

Any ideas?

---

### Post by simoes94 on 2011-03-03
CMNorton:

I had this exact same issue on Debian Linux... after much searching and an hours worth of unproductive hacking I cam across this article: [http://blog.stannard.net.au/2010/12/11/installing-django-with-apache-and-mod_wsgi-on-ubuntu-10-04/](http://blog.stannard.net.au/2010/12/11/installing-django-with-apache-and-mod_wsgi-on-ubuntu-10-04/)

It prescribes the following commands:

```
sudo apt-get purge libapache2-mod-wsgi
sudo apt-get install libapache2-mod-wsgi
```
Instead of simply using apt-get remove. Hope this helps!

---

### Post by cmnorton on 2011-03-04
> **simoes94 said:**
> CMNorton:

I had this exact same issue on Debian Linux... after much searching and an hours worth of unproductive hacking I cam across this article: [http://blog.stannard.net.au/2010/12/11/installing-django-with-apache-and-mod_wsgi-on-ubuntu-10-04/](http://blog.stannard.net.au/2010/12/11/installing-django-with-apache-and-mod_wsgi-on-ubuntu-10-04/)

It prescribes the following commands:

```
sudo apt-get purge libapache2-mod-wsgi
sudo apt-get install libapache2-mod-wsgi
```Instead of simply using apt-get remove. Hope this helps!

Thanks for responding. In my case, this was a 64-bit Linux problem. I needed to build wsgi with a configuration switch that allowed hard-coding the location of a .so shared library into wsgi, so Apache could find it. There was another switch to build the shared library.

I got the information from here. 

[http://code.google.com/p/modwsgi/wiki/ConfigurationIssues](http://code.google.com/p/modwsgi/wiki/ConfigurationIssues)

Incidentally, the Google Group for wsgi is first rate and very helpful.

---

### Post by guygriffiths on 2012-01-19
> Thanks for responding. In my case, this was a 64-bit Linux problem. I  needed to build wsgi with a configuration switch that allowed  hard-coding the location of a .so shared library into wsgi, so Apache  could find it. There was another switch to build the shared library.Any chance you can post how you fixed it, assuming you can still remember?  The link you posted doesn't seem to still have the relevant information.

---

### Post by krasulya on 2012-06-04
> **guygriffiths said:**
> Any chance you can post how you fixed it, assuming you can still remember?  The link you posted doesn't seem to still have the relevant information.

Try 
```
sudo a2enmod wsgi
```

---

