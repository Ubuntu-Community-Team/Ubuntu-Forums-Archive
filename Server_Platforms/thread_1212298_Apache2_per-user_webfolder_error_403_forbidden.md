---
title: "Apache2 per-user webfolder error 403 forbidden"
date: 2009-07-13
forum: Server Platforms
---

### Post by AFarris01 on 2009-07-13
Hey all!

I'm trying to set up a folder in my home directory that I can use to test out .php webpages before I upload then to the net, but i can never access the folder.  no matter what i've done, when i try to access the folder with localhost/~username/ it just returns 403 forbidden.

I've added myself to the www-data group, ive tried chown, chgrp on the public_html folder in my home directory to www-data, ive tried modifying the permissions to 777 and 0777, none of which have done anything different.  

What am I doing wrong?

---

### Post by Thirtysixway on 2009-07-14
Try changing the group owner of your home directory to www-data.

---

### Post by JohnnySage50307 on 2009-07-14
I've never actually coded a PHP page, but I know for my CGI pages, I had to mess with the config file and add that option to it.  You might want to search for that and check Apache's pages for it.

---

### Post by AFarris01 on 2009-08-21
Thanks for the replies! 

the chown on my home directory was what did it. I figured adding myself to the www-data group would've been enough...guess not.  Thanks though!

---

