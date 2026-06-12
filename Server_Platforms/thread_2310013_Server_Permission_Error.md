---
title: "Server Permission Error"
date: 2016-01-15
forum: Server Platforms
---

### Post by wefixit on 2016-01-15
Hello there,

I'm not very experienced with Ubuntu, but hopefully someone here can help. The permissions on our public html folder (its called httpdocs on our server) was set to 777 and as a result our website went offline. The error message our site is displaying is below:

Forbidden

You don't have permission to access / on this server.
Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.


our server info is:
Apache/2.2.22 
hosted on: Ubuntu 12.04.5 LTS

How can I resolve this? I tried setting permissions back to what they were 755 but it still has this same message.

Thank you

---

### Post by darkod on 2016-01-15
Have you double checked that the document root parameter is pointing to the correct folder?

Also, someone might have modified some files. That's why you don't do 777 on web server.

---

### Post by wefixit on 2016-01-15
How do I check that please? All our hosting and accounts etc were recently handed over to us.

---

### Post by darkod on 2016-01-15
In apache each site should have his own config file in /etc/apache2/sites-available. In this file the DocumentRoot parameter points to the folder where the site files are.

Double check that this config is as you expect it to be.

Also, when you were changing permissions back, did you use the -R option to do it recursively (all subfolders)?

I'm not apache expert myself, you need to start looking in details into the apache config, its logs in /var/log/apache2 and the permissions of the files structure.

---

