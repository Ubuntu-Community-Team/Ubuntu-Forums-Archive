---
title: "Apache/CGI-Perl/Kubuntu"
date: 2008-06-02
forum: Server Platforms
---

### Post by ksparkman on 2008-06-02
I dont know if i choose the right categorie to post this, So please excuse.


I am running Kubuntu with Apache2. 

I have a cgi script in the /cgi-bin/ folder.

apache has the /cgi-bin/ script alias setup in the httpd.conf

however, when you go to the cgi script ex.. 

[http://192.168.1.240/cgi-bin/email.cgi](http://192.168.1.240/cgi-bin/email.cgi) it says 404 not found.

now if you go to

[http://192.168.1.240/cgi-bin/](http://192.168.1.240/cgi-bin/) you get a forbidden, 

and [YES] the email.cgi is in the cgi-bin folder.

---

### Post by ksparkman on 2008-06-03
Ok so i opened up the /var/log/apache2/error.log

and this is what it stated: 
[Tue Jun 03 12:59:42 2008] [error] [client 74.212.210.131] (2)No such file or directory: exec of '/usr/lib/cgi-bin/email.cgi' failed, referer: [http://www.commercial-lighting.net/autho/](http://www.commercial-lighting.net/autho/)
[Tue Jun 03 12:59:42 2008] [error] [client 74.212.210.131] Premature end of script headers: email.cgi, referer: [http://www.commercial-lighting.net/autho/](http://www.commercial-lighting.net/autho/)


so I put the email.cgi in the /usr/lib/cgi-bin/ in the directory.. 

and I still get the same thing.

---

### Post by Sef on 2008-06-03
Moved to server platforms.

---

