---
title: "Moodle Help"
date: 2006-05-22
forum: Server Platforms
---

### Post by Stu09 on 2006-05-22
I'm trying to setup a moodle server at work.

I can get to the moodle page via /localhost/moodle but when I try to access it from another computer eg [http://moodlebox/moodle](http://moodlebox/moodle) I'm getting a 403 forbidden page :(  I'm guessing it's a permissions problem somewhere...but where :confused: 

Please help
Stuart

PS I'm running Dapper server install (text only) PHP5 Apache2 mysql5  and I installed Moodle from the repositories.

---

### Post by Glut on 2006-05-22
I know nothing about moodle, but 403 errors are usually caused by incorrect permissions. If you need CGI, check that ExecCGI is set in the site setup, also that the CGI files are executable. If not CGI, check that the www-data user can read /var/www/...where-ever the moodle install is. Check your apache error logs: /var/log/apache2/error.log

---

### Post by Stu09 on 2006-05-23
The error message I'm getting in the apache error log is
> [Tue May 23 14:11:58 2006] [error] [client 10.104.1.137] client denied by server configuration: /usr/share/moodle

I guess I need to change the permissions on that directory :confused:

---

### Post by Glut on 2006-05-23
I suspect that your server is setup to only serve /var/www. You may want to post your site config.

---

### Post by Stu09 on 2006-05-23
Forgive my n00b-iness, where exactly do I find that ?

PS I can get to the default apache page from other computers, just not the /moodle page.

Thanks for your help.

---

### Post by Glut on 2006-05-23
/etc/apache2/sites-available/????
This is assuming that you've made a separate site entry. If you haven't there's your problem as it shouldn't be able to read those directories 'out of the box'

---

### Post by Stu09 on 2006-05-23
aha! only 'default' is listed in there. OK, so I need to make another site...

---

### Post by dforge on 2006-06-12
I'm stuck at the same point. How did you get it working???

---

### Post by Stu09 on 2006-06-12
[QUOTE=dforge]I'm stuck at the same point. How did you get it working???[/QUOTE]

Hey man, I ended up removing moodle from the repositories and downloading the newest build.

I extracted it to the /var/www/ directory and it worked :D 

One other thing, if you want it to be available from outside (internet) you will need to edit the config.php so it has a FQDN instead of just a host name.

---

### Post by mdelatorre on 2006-09-13
You need to read /usr/share/doc/moodle/README.Debian

It will tell you to comment a line in /etc/moodle/apache.conf

manuel.

---

