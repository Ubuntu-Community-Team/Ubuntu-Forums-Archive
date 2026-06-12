---
title: "Apache 2 and FTP Help"
date: 2007-06-18
forum: Server Platforms
---

### Post by Noah0504 on 2007-06-18
I've just set up a LAMP install on an older computer running Debian Etch.  Everything seems to be running fine, but I would like to know how to change the default directory to just /var/www/ instead of /var/www/apache2-default/.  The last time I messed around with Apache, things were different.  I also have a domain name through GoDaddy.  I was wondering if anyone knew how to set it up with my own server as opposed to a third-party server.

Last but not least, I guess I should set up FTP for easy uploading to my server.  What is the best way to go about this, or is there another suggested way to upload to my server since it's on my network?

---

### Post by asommer on 2007-06-18
To change the default directory edit the file:
[B]
/etc/apache2/sites-available/default[/B]

change the **DocumentRoot** setting to wherever (/var/www/).

About setting your site up on your own server I believe you'll need to point the DNS entry from GoDaddy to your machines IP Address.  Do you have a static public IP?

As far as an FTP server I'd go with something like **vsftp**:

[http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)

Here's a post that looks like it will walk you through the steps:

[http://ubuntuforums.org/archive/index.php/t-91887.html](http://ubuntuforums.org/archive/index.php/t-91887.html)

---

### Post by Noah0504 on 2007-06-18
Well, it actually looks like everything is correct, however, if I place "index.html" in /var/www/ it still wants to go to /var/www/apache2_default/.

There is this line, but it seems like it shouldn't be causing a problem:

```
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
RedirectMatch ^/$ /apache2-deafult/
```

---

### Post by asommer on 2007-06-18
I forgot about that line.  It's definitely redirecting you back to the /apache2-default/ folder.  I just commented the line in my file and everything worked as advertised.

You might try commenting it and seeing if it goes to /var/www:

#RedirectMatch ^/$ /apache2-deafult/

Worth a try anyway.

---

### Post by Noah0504 on 2007-06-18
I commented it out and everything is working fine.  I still don't know why it wasn't working correctly though... Oh well, all is well now.  :)

---

