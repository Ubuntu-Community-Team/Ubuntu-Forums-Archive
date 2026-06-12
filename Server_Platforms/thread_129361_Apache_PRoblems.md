---
title: "Apache PRoblems"
date: 2006-02-13
forum: Server Platforms
---

### Post by TomH on 2006-02-13
Hi All, 

Im running apache2 and it all works fine, [http://localhost](http://localhost) loads up the file in /var/www/ however i want to create a new folder so i would have htp://localhost/vnc and the files would be stored in /var/www/vnc but i cant get my head around how i would do this ?

If i just create the directory and put the files in it i get a 

Forbidden 

You dont have permission to access /vnc/vnc.html on this server/

  [Mon Feb 13 20:46:14 2006] [crit] [client 86.129.40.171] (13)Permission denied: /var/www/vnc/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

Thats in my log file. 

Any help greatly apreciated 

Im a bit of a newbie :rolleyes:

---

### Post by nagilum on 2006-02-13
When you copy the new files to /var/www you have to make sure they are readable by the user under which Apache runs, usually www-data. So after copying just execute the appropriate chown command, like 'chown -R www-data:www-data /var/www/*'.

---

### Post by TomH on 2006-02-13
what permissions should the files have? 

sorry if its a really simple file im just unsure. 

Thanks Tom

---

### Post by TomH on 2006-02-13
Ok i have set it as www-data as the owner and owner permissions as read and execute and it seems to work :cool: 

That ok ?

Thanks

Also how do i prevent directory listings?

---

