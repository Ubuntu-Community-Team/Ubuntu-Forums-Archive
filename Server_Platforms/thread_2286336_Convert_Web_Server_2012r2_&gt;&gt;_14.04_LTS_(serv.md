---
title: "Convert Web Server 2012r2 &gt;&gt; 14.04 LTS (server)"
date: 2015-07-11
forum: Server Platforms
---

### Post by jonjsinger on 2015-07-11
I think I already know what the answer is but since I don't like it I thought I would ask and see if there were any other suggestions. 

I had/have a Server2Go website running on Windows 2012r2 machine and I recently lost my free hosting (long story but I had a small computer running in my neighbor's house as their ISP didn't block port 80/443 and mine does and they just put their house up for sale). As I consider either switching ISP's or using a cheap online hosting provider, I am switching over from Windows to Linux --for a bunch of reasons, starting with *nix is just a better OS and ending with most cheap/budget online solutions only support Linux. Windows is either an added cost or a dedicated machine, which is crazy expensive. 

Someone else built the site for me way back and I don't want to loose the look and feel of my site --but I have no idea what (free) template was used, etc. to start from as a base. 

Is it at all possible to take my Server2Go website and convert it over to use on Linux?

I'd be willing to pay a small amount for a converter, etc. --or on the other hand, I don't mind if it's a somewhat manual process because I'm going to need to maintain the thing going forward. It's just that I don't have the time or skills to start from scratch and I cannot for the life of me find the template. 

Thanks.

---

### Post by dragonfly41 on 2015-07-11
The contents of the site should be OS agnostic. HTML/css/js/images etc.

As far as I can see from reading here ..

[http://www.makeuseof.com/tag/portable-test-web-server-server2go/](http://www.makeuseof.com/tag/portable-test-web-server-server2go/)

you will need these steps ..

**On Windows**

Export your MySQL database used by Server2Go.

Also copy all files from htdocs folder into some USB drive. 

[B]
On Ubuntu[/B]

Install Apache2/MySQL/PHP5 (search on how to do this through commands)

Import your MySQL database (Server2Go) into Ubuntu MySQL

Copy contents of Server2Go /htdocs (and below) into /var/www/html/
but none of the other Server2Go folders/files.

i.e. /html folder (Ubuntu) is same as /htdocs folder (Windows)

...

Then run **sudo service apache2 start**

See if you can view any content through [http://localhost](http://localhost)

Above is 90% of migration workflow.   You might need other tweaks such as setting up a virtual host.

And make sure that contents of /var/www/html/ has www-data ownership (Apache2 expects this).

---

### Post by PaulW2U on 2015-07-11
*Thread moved to **Server Platforms**.*

---

### Post by jonjsinger on 2015-07-12
Thank you dragonfly41. I've never built a site before and have never done anything website related so this is all new. I'm not new to Ubuntu, CentOS & BSD command line so that part is as easy as Googling what I don't know --but it's learning the interactions and structure of a LAMP platform. If it's as easy as just moving the database and php files over I'll give it a shot. Thanks again.

---

### Post by jonjsinger on 2015-07-12
One more somewhat related question --didn't want to start a new thread. I can build a single full LAMP platform and import a single php "coming soon" template. I can also build a non "LAMP" (just Apache on Ubuntu) webserver with multiple websites but I'm struggling with pointing mysql + php to the subdirectories required to host multiple websites on the same ubuntu server. 

Any quick pointers? Thanks.

---

### Post by SeijiSensei on 2015-07-12
MySQL and PHP aren't tied to specific directories.  For the latter, you simply need to code files with a .php extension.  That tells Apache to use its PHP parser to display the file rather than send it directly to the browser.  As for MySQL, that runs globally.  Applications connect to the server using client software like the MySQL functions built into PHP like mysql_connect().

---

### Post by dragonfly41 on 2015-07-13
> but I'm struggling with pointing mysql + php to the subdirectories required to host multiple websites on the same ubuntu server.

I think your next step is to read up some tutorial on how to setup virtual hosts .. one for each of your websites.

e.g. see /etc/apache2/sites-available and sites-enabled

The "pointing to" is DocumentRoot setting in each virtual host in sites-available.

e.g. DocumentRoot /var/www/html/mywebsite1

Remember to add each virtual host into /etc/hosts

Search the subject "apache2 virtual hosts".

---

