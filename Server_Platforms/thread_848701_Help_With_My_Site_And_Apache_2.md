---
title: "Help With My Site And Apache 2"
date: 2008-07-03
forum: Server Platforms
---

### Post by UbuntuNerd on 2008-07-03
hey guys can someone please help get mi site working im new to ubuntu so im just trying as i go i have apache 2 ready to go and i can see the default site. i moved my site files to the folder call (www) using nautilus as root. i disable the default site and restarted apache but when i try to acces my site by typing the ip i get this error

Not Found

The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) Server at 192.168.1.102 Port 80

also i notice that the file extension in my site's index is htm and not html like the default site can someone help please

---

### Post by mbeach on 2008-07-04
how did you disable the default site?

I think you want to re-enable it, then edit the 
/etc/apache2/sites-available/default 
file, and just make sure that the Redirect to apache2-default is commented out.
> 
# Uncomment this directive is you want to see apache2's
# default start page (in /apache2-default) when you go to /
# RedirectMatch ^/$ /apache2-default/


then, issue the 
sudo /etc/init.d/apache2 reload

to reload the configuration.

Change your DirectoryIndex directive in /etc/apache2/apache2.conf to include a index.htm if you want it to load instead of index.html.
see:
[http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex)

---

