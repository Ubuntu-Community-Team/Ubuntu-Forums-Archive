---
title: "apache2 access.log has stopped loggin..!"
date: 2006-09-22
forum: Server Platforms
---

### Post by CzarAlex on 2006-09-22
access.log no longer logs. It did. And I noticed today that its been a couple weeks now since it last logged. error.log logs just fine.

The only thing I've changed about apache2 in the last few weeks was the introduction of virtualhosts in apache2.conf

Here is an example:

```
<VirtualHost *:80>
ServerName www.czaralex.com
ServerAlias czaralex.com 
DocumentRoot /var/www
</VirtualHost>
```

Do I need to specify a location for access.log files for each virtualhost? (ive got like 4 setup). If so, how come error.log works? or is that independant of the access.log problem? Someone suggested i chown all log files in /var/log/apache2 to www-data and that had no change. ](*,) 

Thanks!

---

### Post by spp on 2006-09-22
You should not have to specify on a per-host basis. No log in the VirtualHost == server level log.

Things to check...

...permissions on the access.log - Can the www user write to it?
...restart Apache - Can it write now?



SP

---

### Post by CzarAlex on 2006-09-22
i did a sudo chown -R www-data /var/log/apache2 earlier today and restarted the apache2 server. no change :(

Just to clarify, anytime someone accesses my site, it should log that access in access.log?

---

### Post by spp on 2006-09-22
If configured with the log, yes.

On those ownership permissions, the write bit is set, yes? Restarting apache - any affect?

SP

---

### Post by CzarAlex on 2006-09-22
all files (including error.log) are set to 640. restart, no change.

---

### Post by spp on 2006-09-22
What is the CustomLog variable set to in Apache?

(/etc/apache2/sites-enabled/000-default should have that)

SP

---

### Post by CzarAlex on 2006-09-22
CustomLog /var/log/apache2/access.log combined

---

### Post by CzarAlex on 2006-09-22
Hmm. im not sure if this`ll help, since i dont much understand it :) 

[http://www.ubuntuforums.org/showthread.php?t=99871&highlight=access.log](http://www.ubuntuforums.org/showthread.php?t=99871&highlight=access.log)

> Ok, I've figured out that it's not the system logger....the vsftpd log writes in real time. Just need to fix Apache.

Would that be a clue? (note, that is a quote from that other gentelmen's post, not mine.

---

### Post by spp on 2006-09-22
System logger really doesn't do anything with the apache logs. I am now at a loss of what is wrong. 

Other things I would try...
Add CustomLog statements to the virual host entry.
Validating that the www-data user can get to the log file (enable login for www-data user and cd to the directory)

SP

---

### Post by CzarAlex on 2006-09-22
doesn't www-data write to error.log? If so, and since error.log is getting data, it must be something else.

What is the format for adding a custom log file to the virtual host area in apache2.conf?

---

### Post by spp on 2006-09-22
Ahh, good point. 

Same as the main log. Except it is in the virtual host directive. Anything popping up in the error log regards to the access log?

SP

---

### Post by CzarAlex on 2006-09-22
Nothing out of the ordinary. Just some file not found's and stuff. How do I add custom log file specifications to the virtualhosts in my apache2.conf?

```
<VirtualHost *:80>
ServerName www.czaralex.com
ServerAlias czaralex.com 
DocumentRoot /var/www
**CustomLog /var/log/apache2/czar-access.log common**
</VirtualHost>
```

and of course make sure I create that file?

---

### Post by spp on 2006-09-22
That will do it. 

You may not even have to create the file as Apache *should* do it for you.

SP

---

### Post by CzarAlex on 2006-09-22
Heh it *should* log to access.log too :) I`ll give it a whirl.

---

### Post by CzarAlex on 2006-09-22
And it did...that worked. so now stuff from that one virtual host is being logged at czar-access.log

hmm..still wondering why the others aren't going to access.log but i thank you for your assistance!

---

### Post by rocktorrentz on 2007-03-18
I have the exact same problem but i'd quite like all my virtualhosts to log to access.log. My access.log.1 is a month old but i'm pretty sure I had virtualhosts back then. I'll set up the log per virtualhost for the timebeing though.

edit: Don't worry, simply adding "CustomLog /var/log/apache2/access.log combined" to the end of my 000-default file worked.

---

