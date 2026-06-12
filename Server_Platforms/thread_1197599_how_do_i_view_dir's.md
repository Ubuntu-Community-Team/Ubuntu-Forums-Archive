---
title: "how do i view dir's"
date: 2009-06-26
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-06-26
I'm just making a test site right now. on an Apache2 "localhost"

i want it so if i open a dir that doesn't have an index file, i can see and open folders and files located there.

but right now if i open it i get a "403 Forbidden"

how do i make it not forbidden

---

### Post by Luke has no name on 2009-06-26
In your httpd.conf file, Find a line that has "Options" on it and add "Indexes".

After reading your question, I immediately googled "directory browsing apache" and found solutions in the first screen worth of links. 

This is not a joke or a meme, it is fact: Google is your friend.

PS: Do that google search, as my explanation is a little flimsy.

---

### Post by Wim Sturkenboom on 2009-06-26
Below the excerpt of my virtual host configuration on a Slackware server. Check the bold part.
```

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

# catch-all
<VirtualHost *:80>
    ServerAdmin me@btd-techweb02
    DocumentRoot /srv/httpd/htdocs
    ServerName btd-techweb02
</VirtualHost>

# site 1
<VirtualHost *:80>
    ServerAdmin me@btd-techweb02
    DocumentRoot /home/wim/www/site1/web
    ServerName site1.btd-techweb02
    ErrorLog /var/log/httpd/error_log
    CustomLog /var/log/httpd/access_log common

[B]#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site1/web">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>
[/B]
# site2
<VirtualHost *:80>
    ServerAdmin me@btd-techweb02
    DocumentRoot /home/wim/www/site2/web
    ServerName site2.btd-techweb02
    ErrorLog /var/log/httpd/error_log
    CustomLog /var/log/httpd/access_log common

#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site2/web">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

```

---

