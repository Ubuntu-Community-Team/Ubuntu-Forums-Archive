---
title: "Apache 2 virtual hosts and mod_rewrite on dev machine"
date: 2008-01-30
forum: Server Platforms
---

### Post by KrisWillis on 2008-01-30
Hi guys,

I'm trying to set up my development machine to host individual web projects as virtual hosts so that I can easily write my URL rewrites without writing one lot for my local version and another lot for when a project goes live onto a production server.

First up, I created a virtual host file (/etc/apache2/sites-enabled/001-dhc) that looks like this:
```
<VirtualHost *>
    ServerName dhc.kris
    ServerAlias dhc.kris
    ServerAdmin kris@localhost
    DocumentRoot /var/www/dhc
</VirtualHost>
```

Modified my hosts file:
```
127.0.0.1	dhc.kris
```

Pointing my browser to dhc.kris shows what it should do, so I can only assume that part of this task was successful.

My problem now, is that I can't actually get mod_rewrite to work. It is enabled in my Apache2 set-up, I have checked with both apache2 -M and it is also listed in the output of phpinfo().

I have created a .htaccess file (/var/www/dhc/.htaccess) containing the following:
```
RewriteEngine On
RewriteRule ^/test/test.html$	/index.php?page=test
```

I have set AllowOverride to all in /etc/apache2/sites-enabled/000-default:
```
DocumentRoot /var/www/
<Directory />
    Options FollowSymLinks
    AllowOverride all
</Directory>
<Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride all
    Order allow,deny
    allow from all
    # This directive allows us to have apache2's default start page
    # in /apache2-default/, but still have / go to the right place
    #RedirectMatch ^/$ /apache2-default/
</Directory>
```

After restarting Apache2 and pointing my browser to dhc.kris/test/test.html I'm getting a 404. Any ideas as to what I have done wrong, or have failed to do?

---

### Post by Yhetti on 2008-01-30
Check /var/log/apache/access.log or error.log and see what file is actually being returned.  I have a feeling the rewrite is referencing /var/www/ and not the subdirectory.

---

### Post by KrisWillis on 2008-01-31
There's nothing related in access.log, but error.log contained the following:
```
[Thu Jan 31 14:42:22 2008] [error] [client 127.0.0.1] File does not exist: /var/www/dhc/test
```

I'm not sure I follow what is happening here, I'm requesting dhc.kris/test/test.html which should be rewritten to dhc.kris/index.php?page=test in accordance with my RewriteRule in my first post.

Ideas welcome :)

---

### Post by MJN on 2008-01-31
A couple of things worth pointing out (and fixing!):
 
1. Your config from 000-default has no relevence to your dhc.kris virtual host since, as it is a seperate host, there is no 'inherited configuration'. Hence, you should expand your dhc.kris virtual host config to contain the necessary directives as per your default host (such as the <Directory> settings for /var/www/dhc etc).
 
2. Since you are putting your RewriteRule's into .htaccess files the base reference for the matching rules is the directory the htaccess file is in. Hence, you should not use any leading slashes (as this implies an anchored root, which you can't have given the above), and so it should be written **RewriteRule ^test/test.html$ index.php?page=test**
 
Give that a shot and see how you go.
 
Mathew

---

### Post by KrisWillis on 2008-01-31
Mathew, many thanks for your direction - You've solved my problem as far as I can tell. 001-dhc now looks like this:
```
<VirtualHost *>
    ServerName dhc.kris
    ServerAlias dhc.kris
    ServerAdmin kris@osx.co.uk
    DocumentRoot /var/www/dhc
    <Directory /var/www/dhc/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```
Thanks again!

---

### Post by KrisWillis on 2008-01-31
Actually, I have a follow-up question. I have just tried accessing this project from another machine on my network by pointing the browser to [http://192.168.1.9/dhc](http://192.168.1.9/dhc) which didn't work, and to be honest, I wasn't expecting it to.

So, I updated the ServerAlias option in my Virtual host to include the internal IP address of the server. Pointing other machines to my IP now displays the project, but to view one of my other virtual hosts from another machine, I have to remove my IP from the ServerAlias of one virtual host and add it to the other. Quite the pain in the ****, as you could imagine.

Short of setting up an internal DNS server, is there anything that I could do to resolve this?

---

### Post by MJN on 2008-01-31
Given you are using name-based virtual hosting then in the absence of a supplied name (i.e. the client's HOST-HEADER is empty) then Apache must have a 'default' site to serve up. So, you can either make one of your sites 'default' (by making it the first virtual host) or, given it sounds like you want to change which site is default on a regular basis, use name-based hosting as intended...

Hence, to do this you really do need to stick to using named URLs so you've got little option but to use DNS or, if you've only got a small number of clients, configure their hosts files to include the name <-> address mapping.

As an alternative, but this really is pushing the ideal a bit too far (and hence likely to cause other problems), you could give all your virtualhosts 'private' names and configure RewriteRules in your default config (which all client requests would initially hit) to rewrite the request based on the Host-Header. I really wouldn't recommend doing this as it is by all definitions a kludge.

Incidentally, in your posted config (which is much better now) you don't need that ServerAlias entry given it is set the same as ServerName.

Mathew

---

### Post by KrisWillis on 2008-02-01
You've been a great help, thanks Mathew!

---

### Post by MJN on 2008-02-01
Not a prolem - you're welcome.
 
Mathew
 
P.S. I work in Corsham so probably not too far from you!

---

### Post by KrisWillis on 2008-02-01
> **MJN said:**
> P.S. I work in Corsham so probably not too far from you!
Quite right, you're less than an hour away. Small world!

---

### Post by nami on 2008-05-06
I am having problems with this too.

I have added the following into the httpd.conf file in /etc/apache2/httpd.conf

<IfModule mod_rewrite.c>
RewriteEngine on
RewriteRule ^/shortcut [http://localhost/test_sub_folder/test_file.html](http://localhost/test_sub_folder/test_file.html)
</IfModule>

I have also changed 'None' to 'all' in default at /etc/apache2/sites-available/default

When I navigate to [http://localhost/test_sub_folder/test_file.html](http://localhost/test_sub_folder/test_file.html)

but

[http://localhost/shortcut](http://localhost/shortcut)

does not work.  the browser shows a message saying

the requested url /shortcut was not found on this server.

any ideas?

---

### Post by KrisWillis on 2008-05-06
Try this:
```
RewriteRule ^shortcut test_sub_folder/test_file.html
```

---

### Post by nami on 2008-05-06
I tried that and it did not work.  Apparently it seems that ubuntu no longer uses the httpd.conf file, instead it uses the apache2.conf file???

[http://www.unix.com/linux/41163-apache-2-httpd-conf-empty.html](http://www.unix.com/linux/41163-apache-2-httpd-conf-empty.html)

---

### Post by KrisWillis on 2008-05-06
> **nami said:**
> I tried that and it did not work.  Apparently it seems that ubuntu no longer uses the httpd.conf file, instead it uses the apache2.conf file???

[http://www.unix.com/linux/41163-apache-2-httpd-conf-empty.html](http://www.unix.com/linux/41163-apache-2-httpd-conf-empty.html)

That is correct, have you tried adding it to apache2.conf? (Don't forget to restart Apache after the change!)

---

