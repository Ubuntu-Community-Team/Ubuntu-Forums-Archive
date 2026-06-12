---
title: "Battling with an error on my server, cant seem to find the cause"
date: 2012-09-06
forum: Server Platforms
---

### Post by Nixforce on 2012-09-06
Im getting a 500 Internal Server Error on my server. All it says is 

> Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

Im trying to find the cause. Any advice on the best way to start would be great. I have tried looking in the log files, but cant seem to figure it out.

Could someone give me an idea where to start, ive looked in the log files, but not sur if its the correct one i looking in.

---

### Post by Bachstelze on 2012-09-06
Post your Apache log (specifically, the log of the virtualhost where the error occurs).

---

### Post by Nixforce on 2012-09-06
Thanks, where would i find the log file. The problem is with all my sites on the server.

---

### Post by Bachstelze on 2012-09-06
What do you have in /var/log/apache2?

---

### Post by Nixforce on 2012-09-06
I have these files:

[LIST]
[*]access.log
[*]access.log.1
[*]error.log
[*]error.log.1
[*]error.log.2.gz
[*]error.log.3.gz
[*]other_vhosts_access.log
[*]other_vhosts_access.log.1
[*]other_vhosts_access.log.2.gz
[*]other_vhosts_access.log.3.gz
[*]suexec.log
[*]suexec.log.1
[*]suexec.log.2.gz
[*]suexec.log.3.gz
[/LIST]

---

### Post by Bachstelze on 2012-09-06
Look in error.log.

---

### Post by Nixforce on 2012-09-06
Its back up, not sure why.. Im downloading some software called apache log viewer to see what caused it and can see if i can stop it for future

---

### Post by SeijiSensei on 2012-09-07
Do you have any .htaccess files in the DocumentRoot directories.  By default Ubuntu disables commands in .htaccess files.  Look at the AllowOverride option for Apache; you'll see it activated in /etc/apache2/sites-available/default.

A 500 error means there's a misconfiguration somewhere in Apache.

You have some weeks' worth of rotated log files, so your server must have been working before this error occurred, no?  Did you add a new site or make some change to Apache or the virtual host configurations?

---

### Post by Nixforce on 2012-09-17
Hi All,

Sorry for the delay in replying. I had it all working great, thanks.

I have done something again, and am currently looking at the logs.

Thanks again.

---

