---
title: "Setting up a web app on production server"
date: 2013-01-07
forum: Server Platforms
---

### Post by wardii on 2013-01-07
I have an Ubuntu server which should serve my web application. So before I start I would like to know the best way to handle the application before deploying it. I heard that there are online tools to archive the files, delete the comments... etc. that we should considered when setting up a production server.

---

### Post by spynappels on 2013-01-07
Perhaps a little more info on what your web-app will do would help get you some answers. Is it a Wordpress/Joomla/Drupal/other CMS type website or a means of storing information for easy retrieval or something else?

---

### Post by wardii on 2013-01-08
> **spynappels said:**
> Perhaps a little more info on what your web-app will do would help get you some answers. Is it a Wordpress/Joomla/Drupal/other CMS type website or a means of storing information for easy retrieval or something else?

it's a JavaScript/php application.
currently I serve my app on apache httpd, so all my files are in www folder. I'm wondering if there is a tool to compress these files?

---

### Post by spynappels on 2013-01-08
Are you trying to remove comments from the PHP scripts to make their bytecount smaller? I'm sorry, I still don't understand what you are trying to achieve. 

The files need to be in a format that Apache and it's PHP engine can read for it to work, you could gzip every file and save some space, but the web-app wouldn't then work. Normally, these files are not very big anyway and don't take up much room, the dynamic content is normally what takes up a lot of room.

---

### Post by Oxii on 2013-01-08
nnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnn

---

### Post by wardii on 2013-01-08
> **spynappels said:**
> Are you trying to remove comments from the PHP scripts to make their bytecount smaller? 


yes! that's what I was asking about. is that necessary in my case? I want to set up a production server so my clients can access my app remotely.

---

### Post by spynappels on 2013-01-09
You don't need to compress the files, you just need to place them in the appropriate folder on the web server and ensure that PHP is enabled in the server config.

---

### Post by Wim Sturkenboom on 2013-01-09
> **wardii said:**
> yes! that's what I was asking about.** is that necessary in my case?** I want to set up a production server so my clients can access my app remotely.
No, that's not necessary. Unless you have 100 lines of comments for each line of php code ;)

---

### Post by wardii on 2013-01-09
Thank you guys!!

---

