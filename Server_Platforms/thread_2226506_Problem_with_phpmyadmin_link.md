---
title: "Problem with phpmyadmin link"
date: 2014-05-27
forum: Server Platforms
---

### Post by dusan3 on 2014-05-27
Hi,

I'm getting error message when i'm trying to open url [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and the error is this:
[COLOR=#000000][FONT=Times New Roman]
The requested URL /phpmyadmin/ was not found on this server.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at localhost Port 80

I'm getting the correct default page of Apache when i put [http://localhost/](http://localhost/) but i have problem with phpmyadmin.

Can somebody help me with that.

Thanks.

---

### Post by Doug S on 2014-05-27
We need to know which version of Ubuntu you are using and the location of your phpmyadmin directory. What /var/log/apache2/error.log says about it would help also.
My best wild guess with what information there is right now is that you are using ubuntu 14.04 and have it at /var/www/phpmyadmin whereas it now needs to be at /var/www/html/phpmyadmin.

---

### Post by dusan3 on 2014-05-27
Hi Doug, 
I'm using Ubuntu Server 14.04 and in error.log of appache i have this:
[Tue May 27 22:56:05.361018 2014] [mpm_event:notice] [pid 7500:tid 3073985152] AH00491: caught SIGTERM, shutting down
[Tue May 27 22:56:06.472443 2014] [mpm_event:notice] [pid 11211:tid 3074341504] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Tue May 27 22:56:06.472740 2014] [core:notice] [pid 11211:tid 3074341504] AH00094: Command line: '/usr/sbin/apache2'
[Tue May 27 22:56:48.741946 2014] [mpm_event:notice] [pid 11211:tid 3074341504] AH00491: caught SIGTERM, shutting down
[Tue May 27 22:56:49.852980 2014] [mpm_event:notice] [pid 11314:tid 3074103936] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Tue May 27 22:56:49.853273 2014] [core:notice] [pid 11314:tid 3074103936] AH00094: Command line: '/usr/sbin/apache2'
[Tue May 27 23:06:41.586491 2014] [mpm_event:notice] [pid 11314:tid 3074103936] AH00491: caught SIGTERM, shutting down
[Tue May 27 23:08:28.539285 2014] [mpm_event:notice] [pid 11497:tid 3073997440] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Tue May 27 23:08:28.539376 2014] [core:notice] [pid 11497:tid 3073997440] AH00094: Command line: '/usr/sbin/apache2'

But now i'm getting php code when i run localhost/phpmyadmin  
Its a little strange for me.
Location of phpmyadmin is in /etc/phpmyadmin but i copied in /var/www folder.

Hope you can help me.

Thanks.

---

### Post by dusan3 on 2014-05-28
Can somebody help me with this?I'm getting php code instead phpmyadmin page.
How to fix this?

Thanks.

---

### Post by CharlesA on 2014-05-28
How did you install phpmyadmin?

---

### Post by dusan3 on 2014-05-28
I'm using Ubuntu Server 14.04 and command that i've used is:
 sudo apt-get install phpmyadmin

---

### Post by dusan3 on 2014-05-28
Now its showing the blank page when i put [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
Also when i go on view page source i'm getting blank file.I used permitions with the following command which i found on internet but still no luck with this.
sudo chown -R www-data:www-data /usr/share/phpmyadmin
sudo chown -R www-data:www-data /var/lib/phpmyadmin
sudo chown -R www-data:www-data /etc/phpmyadmin

---

### Post by dusan3 on 2014-05-28
If somebody know solution i would be greatfull.

Thanks in advance.

---

### Post by dusan3 on 2014-05-28
Actually that thing solved my problem ... with editing permission now everythis is working ..
Thanks to all ...

---

