---
title: "VirtualHosts - Only One Works"
date: 2009-02-10
forum: Server Platforms
---

### Post by etali on 2009-02-10
Hi All,

I'm having a problem setting up some virtual hosts with apache.  I've searched, and tried a lot of the suggestions, but so far, no joy.

I have two domains, and one works fine, but when I access the other one it's pointing to the same folder as the first domain.

My sites files are:

domain1.com.conf:

NameVirtualHost *:80
<VirtualHost *:80>
ServerName domain1.com
ServerAlias [www.domain1.com](www.domain1.com) domain1.com
DocumentRoot /home/domain1/public_html
</VirtualHost>

domain2.com.conf:

NameVirtualHost *:80
<VirtualHost *:80>
ServerName domain2.com
ServerAlias [www.domain2.com](www.domain2.com) domain2.com
DocumentRoot /home/domain2/public_html
</VirtualHost>


Domain1.com works, but domain2.com is pointing to domain1.com's folder.

I've been hammering at this for a few days now, I have a feeling I've missed something obvious?  

Thanks in advance for any advice.

---

### Post by volkswagner on 2009-02-10
You should comment out or remove the following from each vhost file "NameVirtualHost *:80".  You should add that directive to /etc/apache2/apache2.conf

You also should not need the second mention of the server name in the alias directive.

Are both sites listed in /etc/apache2/sites-enabled ?


ServerAlias [www.domain2.com](www.domain2.com) [COLOR="Red"]domain2.com[/COLOR]

---

### Post by etali on 2009-02-10
Thanks for your response.

I've made the changes that you suggested, and apache now starts without any warnings, but the two domains are still both pointing to the same place.

Both sites are in sites-enabled.  I even ran a2dissite, restarted, then ran a2ensite on them and restarted again just to sanity check...

Thanks again.

---

### Post by volkswagner on 2009-02-10
Verify your permissions are correct for index.html for site two.

```
ls -alt /home/domain2/public_html/
```

vs

```
ls -alt /home/domain1/public_html/
```

---

### Post by volkswagner on 2009-02-10
You may also try adding the following to each respective file.  Insert it just above.

```
</VirtualHost>
```





```
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /home/domain1/public_html/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>
```

```
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /home/domain2/public_html/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>
```

---

### Post by etali on 2009-02-10
Thanks for your response.

I hadn't made an index.html yet (just touched a text file in each folder so there was something to identify it).

The permissions look OK.  


drwxr-xr-x 3 slayers  slayers  4096 Feb  9 20:47 ..
-rw-r--r-- 1 root     root        0 Feb  7 16:44 vampires.txt

drwxr-xr-x 2 gigas gigas 4096 Feb  7 17:39 .
-rw-r--r-- 1 root  root    19 Feb  7 17:39 testing.php
-rw-r--r-- 1 root  root     1 Feb  7 17:29 gigas
drwxr-xr-x 5 gigas gigas 4096 Feb  7 15:54 ..
-rw-r--r-- 1 gigas gigas    0 Feb  1 21:10 gigas.txt


What's wierd is at first it was gigas that was working (testing.php contains phpInfo() so that I could make sure PHP was ok - I was able to view that file fine).  

When I noticed slayers wasn't working, I followed some suggestions found in other threads on this forum.  Now Slayers is the domain that is 'taking over', and I see the slayers directory listing when I visit the gigas domain.

Thanks again.

---

### Post by etali on 2009-02-10
Sorry for the double post.  I added the extra Directory stuff, still no change.  Slayers points to the right place, Gigas is showing the same files as Slayers.

Thanks again.

---

### Post by etali on 2009-02-10
Problem solved :)

I did some more searching, and checked my /etc/hosts file - I had an entry for each domain on my external IP.  I added them on 127.0.0.1 as well, and that seems to have solved the problem.  Do I need the entries on the external IP?

Thanks for all the help!  It's good to know the proper way to set things up - I've got two more domains to point at this server now.

Thanks again.

---

### Post by volkswagner on 2009-02-10
Those file permissions are not ideal.  Group should be set to www-data.

---

### Post by etali on 2009-02-10
Thanks.  I've been a bit lazy and been doing almost everything as root.  I'll sort out some proper group permissions and disable root from being able to log in before doing anything else!

---

