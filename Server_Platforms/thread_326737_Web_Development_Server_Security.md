---
title: "Web Development Server Security"
date: 2006-12-28
forum: Server Platforms
---

### Post by FyreBrand on 2006-12-28
I've done a standard AMP install using the instructions on the Ubuntu documentation page for [_ApacheMySQLPHP_]("https://help.ubuntu.com/community/ApacheMySQLPHP?").  Everything installs and tests properly on Kubuntu 6.10 (Edgy).  I've also installed phpmyadmin and kmysqladmin.

This is for a course sequence I'm taking that uses PHP and MySQL.  The course is taught on Windows machines using IIS (and I do have an Windows partition with IIS installed), but the instructor doesn't mind me developing on Ubuntu and has no requirement I complete this on Windows.
[U]
So my questions are concerning security and the server[/U]:
**1. ** In the Ubuntu documentation AMP install guide it mentions that I can make /var/www my own for ease of development.  Is there anything inherently unsafe about me owning /var/www as opposed to root if all I'm doing is development?  Even though it sounds safe to me I get an uncomfortable feeling whenever I shift ownership from root to another owner.

**2.**  I've made sure that apache is only listening to localhost:80, but is there anything else such as other ports I need to watch?

I only develop on the local server and test it there.  Once it tests okay, I then transfer my code to the schools apache server so the instructor and view the pages and test them.  So far I'm really happy with developing using Kubuntu and the tools I have here.  Quanta and Kate are so much easier and faster than Dreamweaver and eclipse-php on the Windows partition.  I just want to ensure that I'm being safe and smart about this since I love my Linux partition and don't want to do anything to compromise it.

Any suggestions or cautions would be appreciated.

---

### Post by kidders on 2006-12-28
Hi there,

> **FyreBrand said:**
> Is there anything inherently unsafe about me owning /var/www as opposed to rootNo, not really. The only drawback would be the ease with which you could accidentally erase your entire www root. Feel free to make the change. :-)
**Edit:** Some people create a special "web developers" group and set the ownership of /var/www to root:webdev, rather than root:root. The only advantage in doing that is that more than one person can then play with the files ... which doesn't really apply to your situation, I'd say.
**Second Edit:** I suppose the main reason for choosing "root" as the owner is as an alternative to giving the user apache runs as ownership of the www root, which would not be too clever.

> **FyreBrand said:**
> I get an uncomfortable feeling whenever I shift ownership from root to another owner.Good instinct!


> **FyreBrand said:**
> I've made sure that apache is only listening to localhost:80, but is there anything else such as other ports I need to watch?No, but if you're a little sensitive about these things, iptables is your best bet. You can use it to deny all incoming connections on a per-interface basis, if that would make you feel happier.

---

### Post by FyreBrand on 2006-12-28
Thanks kidders.

---

### Post by at0mic on 2006-12-28
things u could do and watch out for:

chmod 644 -R /var/www/* 

change ur default no password for the sql db:

mysqladmin -u root password your-new-password
mysqladmin -h root@local-machine-name -u root -p password your-new-password
sudo /etc/init.d/mysql restart

secure the server with an app like :

[http://www.bastille-linux.org/](http://www.bastille-linux.org/)

---

### Post by kidders on 2006-12-28
One quick (minor) tweak...

> **at0mic said:**
> chmod 644 -R /var/www/*
It would be worth adding **chmod -R ugo+X /var/www/*** (with a capital 'X'), to ensure you retain the ability to descend into directories, but as at0mic's comment suggests, it's certainly worth curtailing access to your stuff. :-)

---

### Post by FyreBrand on 2006-12-31
Thanks to both of you.  I have ensured that passwords are configured for the server.  I did restrict permissions in the file system.

I'm doing some reading on Bastille.  It's quite an application and I find it impressive.  It looks a bit complicated so I want to make sure I understand at least the basics before I continue with it.  I have the feeling that if I don't configure it properly I could break my system.

---

### Post by kidders on 2007-01-01
Yeah, you'll need to be a little cautious with things like Bastille. For your own personal use, it's considerable overkill ... but you might still enjoy playing around with it. If you're looking for something a little easier on the brain, you might like to try an intrusion detection app.

Also, various Linuxes come in specially hardened versions, for security-critical environments ... but again, for personal use, using one really would be overkill.

---

### Post by at0mic on 2007-01-03
worst that can happen with Bastille is you format and reinstall which takes what, 10 minutes? :)

---

### Post by FyreBrand on 2007-01-03
Well it takes me a little longer than that, but not too much.  I keep a second data partition for documents and such so unless something breaks partitions then I never worry too much.  Thanks again for the suggestions.  Everything is working great.

---

### Post by FyreBrand on 2007-02-24
Here is an update to this idea since I've learned a little more.  This really only applies to development only and not a production server.

Instead of making /var/www your own and then restricting permissions you can make a public_html directory in the root of your home folder.  It must be in the root of your home folder because this is how Apache is configured to see it.  This assumes you've already installed and configured [Apache2, MySQL, and PHP]("https://help.ubuntu.com/community/ApacheMySQLPHP").  Simply create the folder by:
```
mkdir ~/public_html
```

Insert a PHP test file into public_html:
```
from your home directory
nano /public_html/phpinfo.php
<?php phpinfo(); ?>
ctrl-o
ctrl-x
```

From the browser enter the following into the url locator: http://localhost/~<username>/phpinfo.php
Where <username> is the name of your login account.  Now there is much less of a need to open up the default web root.  One thing to note that DOCUMENT_ROOT is still /var/www by default in Ubuntu.  You can change this is your Apache2 configuration if you want to be able to test scripts using the super global DOCUMENT_ROOT.

---

