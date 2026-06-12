---
title: "Apache2 Alias with ubuntu server 8.10"
date: 2009-03-19
forum: Server Platforms
---

### Post by abovenewbi on 2009-03-19
hi, I need to allow my server to show the html directories for users. In etc/apache2 I open up apache2.conf and add the following at the end of the file: 

Alias /html /home/admin/tom/html
<Directory /home/admin/tom/html>
Options Indexes Multiviews
AllowOverride None
Order allow,deny
Allow from all
</Directory>

Then I open up my browser and type:
localhost/html
and I can see the files :)

OK...the problem is now that I have two user sections:
Admin and Users ...in the Admin directory I have all the home directories of all admin users and in the Users directory I have all the home directories of the normal users ...I would like that when I open up my browser and type:
localhost/in/tom

I can see all the files in the html directory which is in tom's home direcoty... Anyone have any ideas?

---

### Post by volkswagner on 2009-03-19
You need to set up virtual hosts.  One virtual host will have document root and directory set to /path/to/html and the second vhost with have document root to /path/to/in

All in all it seems a very loose security.  You could set up vhosts for each user with the path to their respective /home folder.  You could also set up an .htaccess and .htpasswd file to require user name and password to view the files.

I think you should be able to use name based virtual hosts.  I have not tried this locally, only using actual domains.

[LIST]
[*]Add the NamedVirtualHost * directive to httpd.conf
[*]Create Vhosts files for each username
[*]access site with [http://localhost.username](http://localhost.username)
[/LIST]

I am guessing this machine is not exposed to the internet.

See more on Vhost's [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html").

---

### Post by heebus on 2009-03-19
You want to use mod_userdir.  Its a simple mod.

[http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)


For instance, I have it set that all users have a ~user/Public. The Public directory is where you can place your html files.

Viewable at: [http://localhost/~user](http://localhost/~user)

---

