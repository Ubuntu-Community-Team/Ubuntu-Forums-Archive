---
title: "ubuntu server, cant add files"
date: 2010-08-09
forum: Server Platforms
---

### Post by da3533 on 2010-08-09
hi

i wanted my own server so installed ubuntu and installed apache2, vsftp etc
apache2 works, typed in localhost and it showed the 'it works' page...

now, after setting up vsftp, i am now able to access the server via ftp on another pc.  i used my username password which was created at the beginning of the Ubuntu installation.
it connects fine, but everytime i am trying to upload a file to the var/www/ directory, it says permission denied..

what do i have to do in order to transfer files into that directory?

---

### Post by Ryan Dwyer on 2010-08-09
Change your DocumentRoot for the default virtual host to something like /home/yourname/www. /var/www is owned by root and cannot be written to by regular users unless you change the permissions.

---

### Post by da3533 on 2010-08-09
thanks.  how do i change it?  i cannot save  anything i change in apache2.conf,   it keeps saying operation failed.,

---

### Post by Bachstelze on 2010-08-09
You really need to familiarise yourself with UNIX permissions. Your favourite search engine will give you a lot of pages covering that.

Sorry, but if you want to run a server, you have some homework to do.

---

