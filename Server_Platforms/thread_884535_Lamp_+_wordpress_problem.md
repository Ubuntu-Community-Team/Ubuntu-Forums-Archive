---
title: "Lamp + wordpress problem"
date: 2008-08-09
forum: Server Platforms
---

### Post by visio159 on 2008-08-09
K guys I installed LAMP and updated my system.
test.php ran well.

Also installed wordpress 2.6 by extracting it to /srv/http/wordpress. I have given the read write permission to the whole srv and its sub folders to my user account.

Wordpress database was also created and wp-config,php was filled manually.

It all worked well ! yeah I was able to change the theme of blog in wordpress and evrything.

[http://i269.photobucket.com/albums/jj44/visio159/Screenshot-6.png](http://i269.photobucket.com/albums/jj44/visio159/Screenshot-6.png)

But then now it shows a blank page when I click on wordpress folder ([http://localhost/wordpress/](http://localhost/wordpress/))




This is my hosts file content:

> 
#
# /etc/hosts: static lookup table for host names
#

#<ip-address>    <hostname.domain.org>    <hostname>
127.0.0.1        localhost.localdomain    localhost scar
#192.168.1.2             scar.mydomain.com       scar  
#192.168.1.1             router.mydomain.com     r
#0.0.0.0               [www.google.co.in](www.google.co.in)        g  
#0.0.0.0               [www.google.com](www.google.com)          g
#127.0.0.1                [www.mvps.org](www.mvps.org)             
# End of file

I remember I edited the hosts file, so is there something wrong here ?

please help me !

---

### Post by visio159 on 2008-08-10
tehehe PROBLEM SOLVED !!!

There was some conflicting code in the "header.php" oops !

---

