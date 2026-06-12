---
title: "Server LAMP"
date: 2009-08-03
forum: Server Platforms
---

### Post by chapa on 2009-08-03
Hi all, I have read around on the forums but nothing really answered my question. 
 
Here it goes, I am fairly new to Linux but I am pretty comfortable navigating around. I wanted to created just a little website that only my family will have access to. Simply using "IP address/index.html" really it will only be a online photoalbum. Figured it would be a really cool project and a good way to learn linux. 
 
I have installed Ubuntu LAMP 9.04, did all the updates and everything else. I did not have any problems what so ever except.... Now the problem, Now what? From all the online stuff I had read and skimmed over there is really only directions on how to make a LAMP server. When it comes to actually adding a website in the /var/www/html directory there is very little to no real direction on how to accomplish this feat. I am creating the site on a older version of dreamweaver on my windows machine, If I can't directly "link" with dreamweaver, I can burn the site to a CD, but again how do I add the site on the Linux box? Help?:confused:

---

### Post by wojox on 2009-08-03
I ported all my scripts over from windows to linux with this:

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

You just install it on windows. Open it find you file connect to your linux box and tell it what directory you want it in (/var/www)

---

### Post by chapa on 2009-08-03
I did forget to mention that.... I had been using winscp. I get the following error:

Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 14

Is there a way I can I can switch to su through winscp?

---

### Post by wojox on 2009-08-03
I believe you need ssh installed.

---

### Post by chapa on 2009-08-03
Umm... I do. I have all this installed and log into the server with putty or with winscp without problems. HOWEVER when I try to add files etc. I get the error I posted.

Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 14

Is there a way I can sudo su in winscp?

---

### Post by jonabyte on 2009-08-04
Change the group ownership of the webfolder, include your user as a member of the new group and then you can use winscp to upload your files.
Otherwise, setup ftp.

---

### Post by DGortze380 on 2009-08-04
> **jonabyte said:**
> Change the group ownership of the webfolder ...

That's a bad idea...

just add yourself to whatever group owns /var/www ... probably www

---

### Post by cdunbar on 2009-08-04
Hello,

Once you get the Group membership and/or permission straightened out and confirm that winscp is working, you should also be able to use Dreamweaver. It supports sftp which relies on SSH. That should be a nice way for you to manage the site.

Regards,
Chris

---

