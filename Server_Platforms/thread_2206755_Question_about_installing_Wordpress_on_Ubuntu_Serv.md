---
title: "Question about installing Wordpress on Ubuntu Server 12.04 LTS"
date: 2014-02-20
forum: Server Platforms
---

### Post by Dbuck9 on 2014-02-20
Our church has purchased a server (I've installed Ubuntu Server 12.04 LTS w/LAMP, Webmin, Usermin, phpMyAdmin, SSH, VSFTP, Sendmail) so that we can host our own websites. 

We are currently hosting 2 websites on our server. 
One of the sites is being administered by an individual who uses Usermin or ftp to upload changes (no problem with this one). 
The second site, which is a WordPress site, is being administered by another individual who has imported the site & connected the database remotely via phpMyAdmin without having WordPress installed on the server. 
We also have a third website which is currently hosted elsewhere that we now want to move onto our server. This website is also a WordPress site.

My questions are: 

1. Is it too late to install WordPress onto this server (all the documentation I've read seem to indicate a fresh LAMP installation is required)? 

2. If it's not too late to install WordPress, will we be able to import the WordPress site that is currently being hosted elsewhere?
 
3. Will we be able to administer changes to the WordPress site that is already on our server using the same WordPress installation?

---

### Post by Habitual on 2014-02-20
1. No.
2. Yes
3. "already installed" negates Q1.

Please clarify.

---

### Post by Dbuck9 on 2014-02-20
The second site, which is a WordPress site, is being administered by another individual who has imported the site & connected the database remotely via phpMyAdmin without having WordPress installed on the server. 

Will we be able to administer changes to that site using the same WordPress installation?

(The 3 sites are sharing one ip address via virtual servers)

---

### Post by Habitual on 2014-02-20
Yes, you will be able to "administer changes" to any WP database hosted on that server.

He is not "using phpMyAdmin" for the actual access, he is using it to allow his IP to connect to the db on that server (via the mysql.user table)

You could in theory have all 3 (and more) sites in a single database (but I don't recommend it), this  can be achieved by using separate table prefixes in a single database.
wpsite1_<dbname_here>
wpsite2_<dbname_here>
wpsite3_<dbname_here>

so, in real life those could be 
wpsite1_testing
wpsite2_development
wpsite3_production

Convention and sanity dictate that each WP have it's own database.

I hope that's helpful.

---

### Post by thnewguy on 2014-02-20
1. A fresh LAMP install is not required. Please take a look at the Wordpress documentation hosted on wordpress.org. They have great tutorials on installing Wordpress on an existing LAMP server and migrating existing Wordpress blogs to another server.

2. Yes, migration is usually pretty easy. Again, the Wordpress documentation has good step-by-step instructions.

3. I'm not sure I understand the third questions, but I think you're wondering about hosting multiple Wordpress blogs on a single server? If so, then the answer is "yes".

---

### Post by CharlesA on 2014-02-20
Speaking from a strictly security standpoint, I hope the server's firewall only allows certain IP address to connect to the database or to pypmyadmin.

as far as the rest goes, I would not recommend using a single database for all the wordpress installations. Create a seperate virtualhost for each one and set it up that way.

Also: Use HTTPS for anything in wp-admin. Self signed ssl certs work fine as long as the admins know to ignore the ZOMG BAD CERT warnings.

---

### Post by kosmokramer314 on 2014-02-21
Moving the new WP site to this server is simple really (I did it and I'm no expert)  You need to create a tar.gz of the existing site after performing a DB dump/backup.  Now take that backup and move it to /var/www/newSiteName on the new server.  untar there.  From there it's just following the standard setup of creating a new website with apache virtual hosts.  OR there are some WP plugins that do all that moving and recreating for you but you still need to do the apache part yourself.  It's nice to use the plugin for some because it's gui based and you can also schedule backups with a gui..if that's what you want.

---

