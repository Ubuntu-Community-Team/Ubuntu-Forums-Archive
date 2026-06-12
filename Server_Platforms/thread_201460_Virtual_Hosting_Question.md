---
title: "Virtual Hosting Question"
date: 2006-06-21
forum: Server Platforms
---

### Post by jordans on 2006-06-21
Ok, Will someone please help me. I am rather new to Ubuntu server but am rather stable. The server does work fine with APACHE2 and i can get it to run but this is my problem:
I have two websites that I want to host on the same server. How would I go about exactly setting up for both websites. The files are located in /var/www/DJC and /var/www/NPP. Both have index files and are ready but I am lost when looking at other posts and short tutorials about this. Maybe someone can help guide me through this. (to view as it stands now go to [www.doddjohnson.com](www.doddjohnson.com)) or 67.170.99.31

---

### Post by makenaa on 2006-06-21
I am having the exact same problem! I did find one thread here that is sorta helpful([http://ubuntuforums.org/showthread.php?t=194807)](http://ubuntuforums.org/showthread.php?t=194807)). Maybe we can work together on this one, and find you whats what. Still though, help would be great.:confused:

---

### Post by foxylad on 2006-06-21
If you have domain names for your sites, you need to set up virtual hosts. When you make a request with a browser, apache checks the required host against it's list of virtual hosts, and then takes pages from the given document root.

Check the apache documentation at [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/). Basically you need to add files to /etc/apache2/sites_available (or something like that - sorry, don't have access to my server right now) containing a virtual host "container". For a domain called [www.example.com](www.example.com) that had files stored in /var/www/example you need something like this:

<VirtualHost *>
    ServerName [www.example.com](www.example.com)
    DocumentRoot /var/www/example
    ServerAdmin [email]webmaster@example.com[/email]
    ErrorLog /var/log/apache2/www.example.com-error_log
    CustomLog /var/log/apache2/www.example.com-access_log common
</VirtualHost>

If you don't have domain names set up, this won't work. You will have to access it using the directory like this:

[http://your.server.name/example](http://your.server.name/example)

Hope that helps.

---

### Post by martinoc on 2006-06-21
[QUOTE=jordans]Ok, Will someone please help me. I am rather new to Ubuntu server but am rather stable. The server does work fine with APACHE2 and i can get it to run but this is my problem:
I have two websites that I want to host on the same server. How would I go about exactly setting up for both websites. The files are located in /var/www/DJC and /var/www/NPP. Both have index files and are ready but I am lost when looking at other posts and short tutorials about this. Maybe someone can help guide me through this. (to view as it stands now go to [www.doddjohnson.com](www.doddjohnson.com)) or 67.170.99.31[/QUOTE]

Go to /etc/apache2/sites-available/
create a file named after each domain.
```

#
# sitename.com 
#
<VirtualHost *:80>
  ServerName sitename.com
  ServerAlias www.sitename.com
  DocumentRoot /var/www/DJC/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
```


then run 
```
a2ensite sitename.com
```
This will enable your site by creating a symlink in the /etc/apache2/sites-enabled/ directory.

You will need to make sure your DNS is set up correctly. There should be ideally an A record pointing from the domain and [www.domain](www.domain) to your IP.

---

### Post by jordans on 2006-06-21
What do you mean by "If you don't have domain names set up"?

---

### Post by jordans on 2006-06-21
also when I ran that last bit of code it told me site does not excist. Please help!

---

### Post by jordans on 2006-06-21
ok, here is the update. I got it to work so that it does it but one more thing. I tested the thing with two domains- [www.vashontechsupport.com](www.vashontechsupport.com) and [www.doddjohnson.com](www.doddjohnson.com), I forwarded [www.vashontechsupport.com](www.vashontechsupport.com) to the IP and it should send you to the NPP part. It does if you type vashontechsupport.com but if you type [www.vashontechsupport.com](www.vashontechsupport.com) it takes you to the DJC site. How do i make it so that i can type [www.vashontechsupport.com?](www.vashontechsupport.com?)
Thanks
Jordan

---

### Post by foxylad on 2006-06-21
Just add a server alias line to the virtual host container:

ServerAlias [www.vashontechsupport.com](www.vashontechsupport.com)

Don't forget to restart apache after making the change.

---

### Post by jordans on 2006-06-21
ok, Becuase I am new to Linux and am only 14 will ya tell me exactly how to restart apache. I have been restarting the entire server with no better knoledge of how to do it.

---

### Post by foxylad on 2006-06-21
Not bad for 14... :)

sudo /etc/init.d/apache2 restart

---

### Post by jordans on 2006-06-21
ok, I tried adding that as an alias (which it already was) and still does the same thing. Any suggestions. [www.vashontechsupport.com](www.vashontechsupport.com) doesn't work, vashontechsupport.com works.

---

### Post by jordans on 2006-06-21
This is how it reads now:
NameVirtualHost *
<VirtualHost *:80>
  ServerName doddjohnson.com
  ServerAlias [www.doddjohnson.com](www.doddjohnson.com)
  DocumentRoot /var/www/DJC/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
  ServerName vashontechsupport.com
  ServerAlias [www.vashontechsupport.com](www.vashontechsupport.com)
  DocumentRoot /var/www/NPP/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>

---

### Post by samuelkarush on 2006-07-04
I have been setting up virtual hosting on apache ubuntu 5.10
 I am getting a 404 error. Examining the error log shows that  apache is trying to direct to /htdocs, which doesn't exist.
 I don't quite understand why. My document root is set to var/www/whatever.com   I know apache is reading this, because if i select a nonexistent directory for document root, I am warned of this during restart.
 Does anyone know why apache would be looking for /htdocs? 
thanks,
sam

p.s. the default file in sites-available works fine, with /var/www/ as document root.

---

### Post by Disstress on 2006-07-04
HTDOCS is where the user document is hosted before you set up an actual website and use the /var/www/... folders. 
Seeing as it is pointing there, you more than likely don't have a setting correctly set up.

If I can get some time today, I'll install apache and try to recreate so I can walk you through a correct config file.

---

### Post by samuelkarush on 2006-07-04
[QUOTE=Disstress]HTDOCS is where the user document is hosted before you set up an actual website and use the /var/www/... folders. 
Seeing as it is pointing there, you more than likely don't have a setting correctly set up.

If I can get some time today, I'll install apache and try to recreate so I can walk you through a correct config file.[/QUOTE]


Thanks, much appreciated.
I've tried a bunch of stuff.  I noticed if I put a DocumentRoot directive in http.conf, then all my domains will point there, regardless of what the DocumentRoot is in sites-available.

Its strange, because my default file in sites-available points to the document root no problem.

sam

---

### Post by jordans on 2006-07-04
Sam,
The default file for virtual hosting should point to a directory not a specific website. This is how it should look:
/var/www/firstwebsite
/var/www/secondwebsite

Then each directory will contain a index.html file.

the defualt file should look like this when you are done
NameVirtualHost *
<VirtualHost *:80>
  ServerName secondwebsite.com
  ServerAlias _[www.secondwebsite.com](www.secondwebsite.com)_
  DocumentRoot /var/www/secondwebsite
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
  ServerName firstwebsite.com
  ServerAlias [www.firstwebsite.com]("http://www.vashontechsupport.com/")
  DocumentRoot /var/www/firstwebsite/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>

---

### Post by samuelkarush on 2006-07-04
Thanks, that worked great!
 That looked much different than the file I had in there:-s 

 My documentroot was actually pointing to a directory, I just named the directory whatever.com.

I did get this error in terminal, but it didn't affect anything AFAIK:

[Tue Jul 04 19:22:18 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

So, thanks again, a little progress makes my day.
 happy 4th
sam

---

### Post by jordans on 2006-07-05
Glad I could help!

---

### Post by hdpc on 2006-07-25
Hi Jordan,

Did you managed to get your second domain to work with [www.seconddomain.com?](www.seconddomain.com?)

I can get my first domain to work with [www.firstdomain.com](www.firstdomain.com) but for my second domain, it works if seconddomain.com but does not work if [www.seconddomain.com](www.seconddomain.com).  I also have ServerAlias set too.  Can you think what I am missing or doing wrong?  Thanks.

-haiN

---

### Post by jordans on 2006-07-26
Sorry I couldn't get back earlier. I was away. What I would do is copy the script I put below exactly but change it just for your website. All I had to do to get mine to work was mess with it enough until it looked like that. Good luck!

---

### Post by hdpc on 2006-07-26
> **jordans said:**
> Sorry I couldn't get back earlier. I was away. What I would do is copy the script I put below exactly but change it just for your website. All I had to do to get mine to work was mess with it enough until it looked like that. Good luck!

Thanks Jordan for replying.  You mentioned "copy the script I put below", but I don't see any.  Thanks.

-haiN

---

### Post by jordans on 2006-07-26
```
NameVirtualHost *
<VirtualHost *:80>
  ServerName secondwebsite.com
  ServerAlias [www.secondwebsite.com]("http://www.secondwebsite.com/")
  DocumentRoot /var/www/secondwebsite
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
  ServerName firstwebsite.com
  ServerAlias [www.firstwebsite.com]("http://www.vashontechsupport.com/")
  DocumentRoot /var/www/firstwebsite/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
```

---

### Post by hdpc on 2006-07-26
> **jordans said:**
> ```
NameVirtualHost *
<VirtualHost *:80>
  ServerName secondwebsite.com
  ServerAlias [www.secondwebsite.com]("http://www.secondwebsite.com/")
  DocumentRoot /var/www/secondwebsite
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
  ServerName firstwebsite.com
  ServerAlias [www.firstwebsite.com]("http://www.vashontechsupport.com/")
  DocumentRoot /var/www/firstwebsite/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
```

Thanks Jordan,

I got it working now.  Thanks again for your help.

-haiN

---

### Post by jordans on 2006-07-26
No Problem

---

### Post by ragdemai on 2006-08-01
I'm new to apache web server, I like to host my apache in local network, but I have totally no idea to set it up.

---

### Post by adamkane on 2006-08-01
Talk to your web host. They will have simpler solutions that involve routing traffic to the appropriate directory via a particular port.

---

### Post by kustomjs on 2008-03-25
I get this error: [Tue Mar 25 19:22:18 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

and also when I try that code it doesnt redirect to the site

---

### Post by Mr. C. on 2008-03-25
> **kustomjs said:**
> I get this error: [Tue Mar 25 19:22:18 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

and also when I try that code it doesnt redirect to the site

Show your VirtualHosts configs.

---

### Post by kustomjs on 2008-05-20
where do you want me to get that conf from?

---

### Post by kustomjs on 2008-07-09
Ok I have redone my server and now I am using 2 different domains and I want to use virtual hosting how do I get this working? what piece of code I need to get this working because I copied that code that Jordon posted up and it didnt work. here is the 2 domains I am working on jbodyconnection.com and cbcperformance.net and server name is server1.

---

