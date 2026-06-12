---
title: "[SOLVED] apache2, can't get rid of certain errors in error.log"
date: 2007-10-25
forum: Server Platforms
---

### Post by inphektion on 2007-10-25
I have apache2 running.  This from a clean install of gutsy.  I then install nagios.  When I remove the default site from apache2 so that just nagios website is running, I get this in the error.log
```
[Thu Oct 25 16:00:13 2007] [error] [client ::1] File does not exist: /htdocs
```

So I put back the default site (but I don't want it there) and figured if I at least don't have it load anything that will be good so I took off indexing.  
With indexing turned off I get this
```
[Thu Oct 25 16:01:56 2007] [error] [client ::1] Directory index forbidden by Options directive: /var/www/
```

This is with just running nagios.  I'm not going to the website when it loads that error.  something from localhost is.  and those errors fly in multiple times a second.  What is causing this and how do I track it down further?
I have a feisty box with apache2 and I disabled the default site and I don't get that htdocs error so maybe nagios is trying something?

Nagios is running great the only message I get from it that I don't understand is at startup I get this
```
Starting nagios:No directory, logging in with HOME=/
 done.
```

Maybe that has something to do with it?

---

### Post by inphektion on 2007-10-25
ah so I think nagios does have something to do with it.  I have this setup in nagios (actually came default with a sample).

define service{
        use                             local-service         ; Name of service template to use
        host_name                       localhost
        service_description             HTTP
        check_command                   check_http
        notifications_enabled           0
        }

So I think this check is what is causing those errors once I kill the default site.  I want it to check that the nagios site is running fine so [http://servername/nagios](http://servername/nagios), not [http://servername](http://servername) which should show nothing.  How do I get nagios to not check /.

---

### Post by inphektion on 2007-10-25
yes it was nagios checking the default site which I wanted to remove.  I wanted nagios check_http to check that the nagios site was running, not the default site.  That was accomplished with the following:
```
define service{
        use                             local-service         ; Name of service template to use
        host_name                       localhost
        service_description             HTTP
        check_command                   check_http!-I localhost -u /nagios -a nagiosadmin:mynagiospass -f follow
        notifications_enabled           0
        }
```

Now I get a 200ok and if the nagios site gets messed up I'll get an email.
perfect.

---

