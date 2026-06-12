---
title: "Apache Help"
date: 2011-11-13
forum: Server Platforms
---

### Post by sridharpandu on 2011-11-13
Not sure if this is the right place to post this, but since Apache doesn't have an official forum I thought someone here could help me out. My apologies in advance if the question is not appropriate for this forum

I have Ubuntu 10.10 installed on a Rackspace virtualised (Xen) server. I have configured several virtual hosts as given below. 

I had my first slashdot effect a few days back when domain2.in was in Denial of service mode to regular users of the site. On inspect I found that the other_vhosts_access_log file was very large 12 MB and there were several archived other_vhosts_access_log files. On inspect I found that the search engines were aggressively caching my site (though I am yet to submit the site maps to them!) So I changed the order of directives from Allow,Deny to Deny,Allow and did a Deny all followed by Allow some ip's (see the 4th vhost for domain2.in below). However I still see ip's that don't match the list being allowed access to the domain. Not sure what could be wrong. Any help would be appreciated. Thanks in advance.

   <VirtualHost *:80>
      ServerName demo.domain1.net
      DocumentRoot /home/domain1
      <Directory /home/domain1/>
         AllowOverride all
         Options -MultiViews
      </Directory>
   </VirtualHost>

  <VirtualHost *:80>
      ServerName [www.domain1.net](www.domain1.net)
      DocumentRoot /var/www
      <Directory /var/www/>
         AllowOverride all
         Options FollowSymLinks Multiviews
         Order allow,deny
         Allow from all
      </Directory>
  </VirtualHost>

 <VirtualHost *:80>
      ServerName [www.domain2.in](www.domain2.in)
      ServerAlias domain2.in *.domain2.in
      DocumentRoot /home/domain2
      <Directory /home/domain2/>
         AllowOverride all
         Options FollowSymLinks Multiviews
         Order deny,allow
         Deny from all
         Allow from 14 59 117 118 119 121 122.1
      </Directory>
 </VirtualHost>

 <VirtualHost *:80>
     ServerName crm.domain3.in
     DocumentRoot /home/domain3
     <Directory /home/domain3/>
         AllowOverride all
         Options FollowSymLinks Multiviews
         Order allow,deny
         Allow from all
     </Directory>
 </VirtualHost>

 <VirtualHost *:80>
     ServerName demo.domain4.co.in
     DocumentRoot /home/domain4
     <Directory /home/domain4/>
         AllowOverride all
         Options FollowSymLinks Multiviews
         Order allow,deny
         Allow from all
     </Directory>
 </VirtualHost>

---

### Post by dapperdanny77 on 2011-11-13
apache is writing a log entry for every request even if it's blocked.
the response to blocked ip's should be http 403 (forbidden) - you should find matching entries in the error log as well (something like "client denied by server config ")

---

### Post by sridharpandu on 2011-11-13
Thank you. There are entries in the error.log. (A sigh of relief). Is there a way to tell these search engines to stop indexing the site.

---

### Post by SeijiSensei on 2011-11-14
Create a robots.txt file in the server's DirectoryRoot like this:

```

User-agent: *
Disallow: /

```

This only protects you against legitimate search engines that respect the robots.txt protocol, of course.

---

### Post by dapperdanny77 on 2011-11-14
usually search engines are looking for robots.txt files and honor the settings there. you can exclude parts from being crawled. you can find a lot about this on google

the crawlers like google also react on getting a 403 forbidden - as far as i know these sites where excluded from future crawlings some time

---

### Post by sridharpandu on 2011-11-21
Thank you. Included a robots.txt file.

---

