---
title: "Apache Configuration"
date: 2007-10-20
forum: Server Platforms
---

### Post by caseyg on 2007-10-20
Hello all. As a 2 year linux user you can figure my abilities are limited. I've decided to install Apache on my Ubuntu Studio distro and try to get it working for simple file share access that would be helpful for my job.  I'm looking for some docs or direction as how to create a simple file share or viewable file directory. It can be very simple, no scripts needed, at least I think. I currently have apache installed and can access the test page when browsing my domain. Any help would be so apreciated. Is it as easy as this directive and is the 'var' location the correct place to put my files.

<Directory '/var/www/web1/web/docs'>
   Options Indexes
</Directory>

Thanks in advance

caseyg

---

### Post by u_kraze on 2007-10-27
hi 

im new to this but ive been trying with my own server for a few days. From my understand the server is supposed to list index as default.if you have webmin running you can just go into the SERVERS menu and then APACHE SERVER and then there is a button named EDIT CONFIG FILES. and then you select the **/etc/apache2/sites-available/default** and then look for this part if its not there then addd it.

```
<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
```

If you do not have webmin then you have to go to the directory /etc/apache2/sites-available/default
and you have to edit the default file as root.
Then you add the part above .

Im pretty  sure when you install it lists the files as directories.  

i hope i helped in some way but im new to this too just trying to help you out though.

---

