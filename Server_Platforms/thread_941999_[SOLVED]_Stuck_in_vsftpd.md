---
title: "[SOLVED] Stuck in vsftpd"
date: 2008-10-08
forum: Server Platforms
---

### Post by icantfindausername on 2008-10-08
Ok, I have searched and tried about everything I have found so far.  Been stuck on this for about a week.  

Anyway, I'm running ubuntu server with vsftpd as my ftp service.  I am still in the stages of experimenting.  My problem is uploading files with dreamweaver or any ftp program for that matter.  Directory listing and reading files works fine.   

I've set up permission to read write in my ftp directory, and I log in to it in dreamweaver with my main username password. It shows the index.html that is in the /var/www directory.


here is a copy of my vsftpd.conf

[COLOR="Yellow"]listen=YES
local_enable=YES
write_enable=YES
chown_uploads=YES
chown_username=andy
local_root=/var/www/[/COLOR]



and here is the output when I use [COLOR="Yellow"]ftp localhost[/COLOR]
login:[COLOR="Yellow"] andy[/COLOR]
password:
230 login successful
ftp>[COLOR="Yellow"]dir[/COLOR]
150 Here comes the directory listing
-rwxr-xr-x    1 0     0   48 Oct 3 04:22 index.html
226 Directory send OK.


Like I said I'm just experimenting and it doesn't need to be completely secure or anything right now.  I'm actually using vmware workstation to learn about servers, before I actually dedicate actual hardware for one.

---

### Post by lykwydchykyn on 2008-10-08
/var/www is by default owned by, and writeable by root and root alone.  You need to do one of the following to write files to it:

 - change the permissions of /var/www so that your user can write to it.
 - delete /var/www and symlink it to a directory you can write to.
 - edit /etc/apache2/sites-available/default and set the webroot to a directory you can write to.
 - log in as root via ftp (just kidding, that's a bad idea).

---

### Post by icantfindausername on 2008-10-08
I tried  sudo chmod 777 /var/www/

Doesn't that add all permission to that folder?  I'm still learning, so maybe I'll get it to work. 

Thanks for your response,   I need to study on permissions more.

---

### Post by lykwydchykyn on 2008-10-08
You are correct.  However, it doesn't change permissions on the contents of the folder, so you won't be able to edit the index.html file.  To do that, you need to specify the -R flag for recursion:
```

sudo chmod -R 777 /var/www

```

That will make everything inside /var/www world-writeable.

---

### Post by icantfindausername on 2008-10-08
That worked, dreamweaver uploaded without any problems.

Thanks so much,  I seen the -R before but I thought that applied only to subfolders.


Once again thanks.  I need to study about permissions again.

---

