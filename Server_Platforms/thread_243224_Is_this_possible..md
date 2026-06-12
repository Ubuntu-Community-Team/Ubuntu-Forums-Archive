---
title: "Is this possible."
date: 2006-08-24
forum: Server Platforms
---

### Post by sdmike on 2006-08-24
Ok is it possible to take the apache2 code from the file called httpd.conf from the WINDOWS version of Apache2 and put that code into the linux version of apache2 and put it into the httpd.conf file??????

Just curious thanks.

---

### Post by chonger on 2006-08-24
Umm... say if the code refers to "C:\Program Files\Apache..." then probably not. Similarly, you will probably have problems if the code refers to a .dll file. 

Note that if you copy the line that says "KeepAlive On", you'll be okay. So it really depends on the part of the configuration you are copying over. 

The syntax for Apache directives are the same between Unix and Windows. But Windows, with its own path syntax and different file naming conventions pretty much means you cannot simply copy and paste any part of the file to Unix apache and expect it work.

---

### Post by harisund on 2006-08-25
Umm... not quite. 

The problem is, on Windows, Fedora, Redhat etc, the entire Apache configuration is in one file titled 'httpd.conf' whereas Apache on Ubuntu has its configuration files split into multiple places. 

The ports which apache2 has to listen to go to /etc/apache2/ports.conf. The main (and perhaps the biggest part of httpd.conf) part is in /etc/apache2/apache2.conf.

The details about the sites hosted, virtual hosts and so on go to /etc/apache2/sites-available/ and then you add a site using 'sudo a2ensite'. This has a symlink created in /etc/apache2/sites-enabled. 

of course, path names differing between '\' and '/' (such as C:\Home and ~/home) are another big difference. 

Do you have a list of changes you made to apache on Windows? perhaps if you list them here, I can try (and others will do a better job as well) to list out the changes you will have to do in Ubuntu to achieve the same functionality.

---

