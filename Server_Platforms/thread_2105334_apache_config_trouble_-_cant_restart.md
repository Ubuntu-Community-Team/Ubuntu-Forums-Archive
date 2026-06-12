---
title: "apache config trouble - cant restart"
date: 2013-01-15
forum: Server Platforms
---

### Post by ZenMasta on 2013-01-15
I just setup a new server and installed apache. 

I am hosting dev site for a magento cart. The home page was loading fine but I realized I had forgotten to bring over my .htaccess file when I got a 404 on my admin url.

After doing so, I wasn't sure if rewrite was enabled or not by default so I tried to do so but when I tried to restart apache it failed. see output below

Now when I try to load the site I just get an internal error.
I've uploaded both of my log files. 

Thanks in advance :)

dev ~/html: sudo a2enmod rewrite
service apache2 restart

which gave me this message
>  * Restarting web server apache2                                                /usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]


---

### Post by SeijiSensei on 2013-01-15
You need a sudo before "server apache2 restart".

---

### Post by ZenMasta on 2013-01-16
Thanks yeah I ended up figuring that out, but I'm still stuck with a critical error. any ideas how to clear that up?

If I remove the .htaccess I no longer get the error

---

### Post by SeijiSensei on 2013-01-16
> **ZenMasta said:**
> Thanks yeah I ended up figuring that out, but I'm still stuck with a critical error. any ideas how to clear that up?

If I remove the .htaccess I no longer get the error

Check your site configuration files.  .htaccess is disabled by default in /etc/apache2/sites-available/default.  You can either change the "[AllowOverride]("http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride")" directive or, better, move any directives you would put in an .htaccess file into the <Directory> stanza for your DocumentRoot.

Your first step in troubleshooting should always be /var/log/apache2/error.log.

.htaccess files are a kludge so that a web hosting provider can enable individual customers to specify Apache directives.  If you are in control of the entire server, putting the directives into the site configuation files makes the most sense.

---

### Post by ZenMasta on 2013-01-17
I trashed my logs and gave it some time before I tried viewing any of the pages. Discovered that I needed to enable headers mod.

.htaccess: Invalid command 'Header', perhaps misspelled or defined by a module not included in the server configuration
I was getting this error. I think everything is okay now.

---

