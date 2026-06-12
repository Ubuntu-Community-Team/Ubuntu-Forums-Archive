---
title: "Apache Document Path"
date: 2007-06-28
forum: Server Platforms
---

### Post by lintoon on 2007-06-28
Hi everyone.  I'm a new member of these forums and have what is probably a stupid question.

I've been using Ubuntu for ages now and love it.  I'm not a power user or anything more of a fiddler to get things running.  I have never used Apache, MySQL etc.

My friend is starting to build websites and is learning mysql/php.  I have installed Apache, Mysql, Php from synaptic package manager and thats all I have done.  He has asked me to install OSCommerce so he can look into it.  

OSCommerce tells us to put the "Catalog" folder in the Documents Path and gives examples of:
/home/hpdl/public_html/
/srv/www/htdocs/
/usr/local/htdocs/

My problem is these folders do not exist on his system.  Can shed some light on this please.

Thank you.

More info:
Ubuntu 6.10
Apache Version 2.0.55
Mysql Server Version 5.0.24a-9
PHP version 4:4.4.2-1.1

---

### Post by joewilliams on 2007-06-28
try /var/www

---

### Post by Peter_ Jensen on 2007-06-28
I have the same problem in ubuntu 7.04 I can't find out where to put my files , its seems that the path used in previous version dosent apply more.

but for your friends system he should make the public_html folder in his home folder and can then load his site with this url [http://localhost/~username/](http://localhost/~username/)

if any one can shed some lights on how it works in 7.04 I will really appriciate it as the above dosnt work there ;)

---

### Post by lintoon on 2007-06-28
Thank you both for your replies.  Much appreciated.  

Cheers Peter I will pass that info on.

Joe, unfortunately it does not exist at /var/www.

This is driving me crazy.  I have googled for the location for days now but found nothing.  I am now starting to think it was the installaton procedure which was wrong.  Or maybe there is a config file which points to the document path.  I can't find it though.  

More digging I think.

Regards.

---

### Post by s_raghu20 on 2007-06-28
Hi Guys,

Well, I have this feeling that the ubuntu apache package that we receive from the repositories is built a bit differently than the standard build for apache.

I had exaclty the same problems, only a bit more. I was looking into all sorts of apache configuration files after I installed the ubuntu apache package. (apache2 actually). I wanted to change the document root, and enable/disable some modules...couldnt really succeed.

So, for me, the solution eventually was to download the source from httpd.apache.org, its a newer version there, and compile it myself.  That was pretty easy. And it worked after that.  Then I found all the regular file locations, config files etc. that I have always known about apache.  

But, there the catch is, the default installation does not seem to provide/setup automatic startup scripts for init.d kind of locations.

I am still after that task. If anyone has a diff version of his apache story, please share

regards
raghav..

---

### Post by joewilliams on 2007-06-29
the standard install for ubuntu lamp server does have the /var/www set for http documents. Have you considered installing a new instance of ubuntu lamp server? Everything is standardized in the 'Ubuntu Way" with this install. (for example: Use Ubuntu 6.06.L Server and choose LAMP on the first setup screen) It's ready to go in short order this way.

---

### Post by lintoon on 2007-06-29
Thanks for the advice Joe.  I will try to copy the catalog folder to /var/www and see if that works.   I'll post my results.  I think a full reinstall is out of the question. Unless it is the only option of course.  Cheers.

---

### Post by lintoon on 2007-07-01
Update:

I copied the catalog folder to /var/www 
(after changing owner and permissons on /var/www to allow me to do so).

And got a different error:
"Server Requirement Error: register_globals is disabled in your PHP configuration. This can be enabled in your php.ini configuration file or in the .htaccess file in your catalog directory"

Note: This error occurs when connecting to the apache server from a networked windows pc.  Entering 127.0.0.1/catalog on the ubuntu webserver prompts to locate an application to open a .PHTML file.  So I went with the windows error because it was telling me what the problem was.

Tried enabling register_globals in /etc/php4/apache2/php.ini, restarted apache - Made no difference.

Enabled register_globals in /var/www/catalog/.htaccess and also uncommented AllowOverride Options
It now works.  We get the OSCommerce screen to install a new store.  Fantastic.  

Just thought I would let you all know.

Thank you for the input everyone.  Big thanks to Joe for the location.

---

