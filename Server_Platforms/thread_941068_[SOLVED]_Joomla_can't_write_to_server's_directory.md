---
title: "[SOLVED] Joomla can't write to server's directory"
date: 2008-10-07
forum: Server Platforms
---

### Post by adri_ht_ on 2008-10-07
I'm relatively new to Ubuntu, but not to linux. Anyways the other day I started to set up Ubuntu Server Edition 8.01 in a Virtual Machine under my Windows box. So far I have everything working except that I can't make Joomla write to the server's directory. Ubuntu security seems to be very tight indeed. 

I had the same issue with FTP but I got around it by making a local user and pointing his home directory to the web server directory. I don't think I can take the same approach now and I'm totally clueless. Thank you.

---

### Post by alastair on 2008-10-07
Very little (to no) information there. What are you trying to do, and what exact error do you get? Web server error logs may also be of interest.

---

### Post by adri_ht_ on 2008-10-07
> **alastair said:**
> Very little (to no) information there. What are you trying to do, and what exact error do you get? Web server error logs may also be of interest.

Sorry that I wasn't able to explain my problem better. There are no errors simple that Joomla can't write to /var/www/htdocs/ where I have the whole Joomla system with its website. For instance, at first it couldn't create the "configuration.php" text file, I had to do it manually via ftp. If I want to edit a template, I can't because it says that the file is unwritable. The whole server directory is unwritable by any outside source other than an authenticated user. 

I know there is a way, and I hope you guys can help me. Thanks again.

---

### Post by christianvaldes on 2008-10-07
Joomla

Have you tried Drupal.
I found it to be the best CMS.....

sounds like you have a permissions problem....

you can try 

chmod 777 -R on the directory that is giving you the problem

thou I would read the documenation to find out what chmod command should be run on the directory...

just run it on the joomla directory

---

### Post by adri_ht_ on 2008-10-07
> **christianvaldes said:**
> Joomla

Have you tried Drupal.
I found it to be the best CMS.....

sounds like you have a permissions problem....

you can try 

chmod 777 -R on the directory that is giving you the problem

thou I would read the documenation to find out what chmod command should be run on the directory...

just run it on the joomla directory

Never heard of it, but I guess I will give it a try. Modifying the permissions to 777 solved my problem, but I guess is not the most secure way of doing it. I will have to dig more into chmod and try to just allow the right user for security purposes. I found this user in /etc/passwd "www-data" /var/www, that might be the one. Thanks again.

---

### Post by MystaMax on 2008-10-08
Have a look at the link below. It'll give you an overview of permissions w/ Joomla.

[http://forum.joomla.org/viewtopic.php?t=121470](http://forum.joomla.org/viewtopic.php?t=121470) (very thorough)

Joomla has the following recommended permissions for files and folders

Files = 644  
Directories = 755

If you have SSH access, you can run the following command to adjust your file and directory permissions to their recommended settings, respectively:

```


find -type f -exec chmod 644 {} \;
find -type d -exec chmod 755 {} \;


```The code above should be ran from your Joomla install directory.


Let me say that choosing a CMS is a matter of personal preference. Make sure you're choosing the right tool for the job. Joomla & Drupal are two of the best CMS' out there, both with their own set of strengths. You can play around w/ both of them @ [opensourcecms.com]("http://opensourcecms.com").

---

### Post by adri_ht_ on 2008-10-12
> **MystaMax said:**
> Have a look at the link below. It'll give you an overview of permissions w/ Joomla.

[http://forum.joomla.org/viewtopic.php?t=121470](http://forum.joomla.org/viewtopic.php?t=121470) (very thorough)

Joomla has the following recommended permissions for files and folders

Files = 644  
Directories = 755



Thanks a lot.

---

