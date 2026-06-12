---
title: "Migrating Drupal Site"
date: 2008-12-08
forum: Server Platforms
---

### Post by gtmurff on 2008-12-08
I'm migrating my web server to newer hardware and at the same time switching from an Arch Linux server to Ubuntu 8.10 server.  It's a drupal based site and uses mysql.  I was able to copy the content and the database info.  However, I had to add the following lines to the <Directory> section in my /etc/apache2/sites-available/<my domain> file in order to make drupal work.

#########################
   <IfModule mod_rewrite.c>
          RewriteEngine on
          RewriteCond %{HTTP_HOST} ^(.+\..+)$ [NC]
          RewriteCond %{HTTP_HOST} !^.+\..+\..+$ [NC]
          RewriteRule ^(.*)$ http://www.%1/$1 [L,R=301]
          RewriteCond %{HTTP_HOST} ^(.*)$ [NC]
          RewriteRule ^files/(.*)$ sites/%1/files/$1 [L]
          RewriteRule ^files/(.*)$ sites/%1/files/$1 [L]
          RewriteCond %{REQUEST_FILENAME} !-f
          RewriteCond %{REQUEST_FILENAME} !-d
          RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]
   </IfModule>
########################

I found this info at [http://drupal.org/node/134439]("http://drupal.org/node/134439") and I was wondering if anyone could explain why I had to add this?  As well as what this does, or point me to where I could read about what this does.  I generally like to know exactly what is going on with my web server.

Without the above code, the index page works, but none of the other pages in the site work. 

Thanks,

GT

---

