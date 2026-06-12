---
title: "How to set default web page in Apache2?"
date: 2007-08-10
forum: Server Platforms
---

### Post by Horinius on 2007-08-10
I'm using VirtualAppliances.net's LAMP virtual machine which is based on Ubuntu.  In their forum, users are advised to post question in Ubuntu forum, that's why I'm here.  Anyway, I can't find answer there.

I'd like how to set default web page in Apache2.

Right now, the default home page is index.php. But I need it to be default.html. When there's no index.php, the web server lists out the content of wwwroot!! :shock:

I've tried to create a .htaccess file which contains "DirectoryIndex default.html". This doesn't work!

Then I've tried to edit /etc/apache2/httpd.conf file. It is empty! :|:shock:

I had taken a look at apache2.conf file but it doesn't contain anything related to index.php!  :evil:

I'm lost!  Hey, isn't there some convention/standard for configuration? What a mess, Linux world!  Every software creates its own standard.  Every distro creates its own standard!  Just like Microsoft but worse.  At least with Microsoft, we could search in its web site.

---

### Post by heimo on 2007-08-10
> **Horinius said:**
> I'm lost!  Hey, isn't there some convention/standard for configuration? What a mess, Linux world!  Every software creates its own standard.  Every distro creates its own standard!  Just like Microsoft but worse.  At least with Microsoft, we could search in its web site.

You were doing nice job asking for help until this. Check Apache documentation.
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

Remember to restart or at least reload Apache after changes to apache2.conf. Check your spelling, html or htm?

And if you will, there's always IIS which I think has default.htm as a default page. No one here's going to force you to use Apache or Ubuntu.

---

### Post by ukripper on 2007-08-10
> **Horinius said:**
> I'm using VirtualAppliances.net's LAMP virtual machine which is based on Ubuntu.  In their forum, users are advised to post question in Ubuntu forum, that's why I'm here.  Anyway, I can't find answer there.

I'd like how to set default web page in Apache2.

Right now, the default home page is index.php. But I need it to be default.html. When there's no index.php, the web server lists out the content of wwwroot!! :shock:

I've tried to create a .htaccess file which contains "DirectoryIndex default.html". This doesn't work!

Then I've tried to edit /etc/apache2/httpd.conf file. It is empty! :|:shock:

I had taken a look at apache2.conf file but it doesn't contain anything related to index.php!  :evil:

I'm lost!  Hey, isn't there some convention/standard for configuration? What a mess, Linux world!  Every software creates its own standard.  Every distro creates its own standard!  Just like Microsoft but worse.  At least with Microsoft, we could search in its web site.

Try XAMPP it will be easier for you to configure. LAMP can be  bit daunting  to configure for web developers/ users who are used to  IIS. That is where XAMPP kicks in for users like you - here is the link [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

