---
title: "LAMP+Wordpress: FTP data required?!"
date: 2010-11-03
forum: Server Platforms
---

### Post by The Bright Side on 2010-11-03
Hey guys,

I set up Wordpress on my machine in a LAMP environment (as in, on my localhost). I used two really helpful tutorials to get it all running:

[http://www.techtickle.com/how-to-setup-lamp-on-ubuntu.html](http://www.techtickle.com/how-to-setup-lamp-on-ubuntu.html)
[http://www.techtickle.com/install-wordpress-locally-on-ubuntu-linux-with-lamp.html](http://www.techtickle.com/install-wordpress-locally-on-ubuntu-linux-with-lamp.html)

But now, I cannot install themes or plugins, or delete their files, because Wordpress asks me for my FTP data, and I'm stumped.

When I download e.g. the Arras theme as zip, unpack it and move the folder into /var/www/kme/wp-content/themes (running Nautilus as root to do it), it simply won't show up in my "Appearance" section of the wp admin panel.

If I try to download and install it from the Wordpress control panel, I get the screen that asks me for FTP info (Host name, username, password), and no matter what I enter, I get

> Failed to connect to FTP Server localhost:21

or variations thereof, depending on what I put in as FTP server (e.g. "localhost/kme").

How can I get past that? I did install vsftpd, but even with that, Wordpress still won't function properly. What am I doing wrong? Any ideas?

I hope you can help me out. I can't wait to build my web page.

Thanks!
M.

---

### Post by The Bright Side on 2010-11-03
I tried sudo chown -R thebrightside www

Now the entire /var/www folder and all its sub-folders are owned by thebrightside, aka me. 

Same result.

---

### Post by DrReaper on 2011-01-20
I am having the same issue. Did you ever find the answer? I am sure it's a rights issue but I am not sure how to solve it.

---

### Post by mdlueck on 2011-01-21
I got into sort of a tangle with WP on Ubuntu. Our standard is to have umask = 002 (aka group writable files / dirs) on all of /srv/www, which is where all of our Apache sites are stored.

We have a sticky bit forcing group ownership of files/dirs to www-data, and those allowed to write files within /srv/www are members of the www-data group.

Works well, expect for WordPress!

WordPress INSISTS that www-data:www-data be owner:group of all of the WP files, else the plug-in auto-update puts up a fuss. So I must have the WP portion of the site running with custom ownership, and everything else is standardized.

---

