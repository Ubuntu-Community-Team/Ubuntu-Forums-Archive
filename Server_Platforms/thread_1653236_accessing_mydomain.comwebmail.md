---
title: "accessing mydomain.com/webmail"
date: 2010-12-26
forum: Server Platforms
---

### Post by entertheraptor on 2010-12-26
I have set up a home based server following "The Perfect Server Ubuntu 10.10 [ISPConfig 3]" guide on HowtoForge.com. Since then I installed Roundcube Webmail in /var/www/mail and after some initial instillation problems everything works fine. I can access my Roundcube Webmail locally through 192.168.x.x/mail and like I said all works fine.

What I want to do is access my Roundcube Webmail through the internet at "mydomain.com/mailbox" mydomain.com was set up with ISPConfig 3 so it's physical location on the server is /var/www/clients/client1/web1/web or /var/www/mydomain.com/web.

The first method that was suggested to me was to create a file /etc/apache2/conf.d/roundcube.conf with the following content,

Alias /mailbox /var/www/mail
<Directory /var/www/mail>
php_admin_value open_basedir /var/www/mail
AllowOverride All
Order allow,deny
Allow from all
</Directory>

Theory being that Roundcube could then be accessed from any domain on the server by appending /mailbox to the domain name. Using this method when I go to mydomain.com/mailbox I get "Internal Server Error 500".

I repaced this method with a symlink created in the mydomain.com/web directory using the command "ln -s /var/www/mail mydomain.com/web/mailbox" which appears to have created the symlink just fine and when I use the command "ls -l" in that directory the symlink appears to point to /var/www/mail but when I go to mydomain.com/mailbox I am again greeted with the "Error 500".

Help please.

---

### Post by Vegan on 2010-12-26
what port is your web mail running on?

---

### Post by entertheraptor on 2010-12-26
I'm afraid I don't understand the question. Seeing as it's accessed with a browser then I would assume port 80 (or whichever port the server listens on) unless there is actually a setting in Roundcube to configure it to be accessed on a different port. Is there?

---

### Post by entertheraptor on 2010-12-27
OK, now things are really screwed up!

I went back to using the file /etc/apache2/conf.d/roundcube.conf as described above and was still getting the error 500. Whether it was a good idea or not I decided to change this file to point to the squirrelmail instillation instead to see if that worked figuring it may give me some indication as to whether the problem was with roundcube (or something associated) itself or with the roundcube.conf file. 

When I changed the roundcube.conf file to point to the squirrelmail instillation what happened was when I went to "mydomain.com/mailbox" the browser (Chrome) downloaded the index.php file in the squirrelmail directory instead of opening it.

So I changed the roundcube.conf file back to it's original settings (pointing to /var/www/mail) expecting it to go back to throwing a 500 error and it still downloads the squirrelmail index.php.

This behavior has continued after refreshing the browser, restarting apache and even rebooting the server.

I'm now at a complete loss.

---

