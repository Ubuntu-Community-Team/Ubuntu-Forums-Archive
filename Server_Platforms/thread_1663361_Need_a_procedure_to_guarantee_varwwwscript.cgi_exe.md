---
title: "Need a procedure to guarantee /var/www/script.cgi execution"
date: 2011-01-09
forum: Server Platforms
---

### Post by bobtestact on 2011-01-09
Can somebody post (or link to) a procedure that will *guarantee* that the shell script "/var/www/script.cgi" will be executed when requesting the URL "http://hostname/script.cgi"?  It should also execute any newly-added shell script ending with ".cgi" at or below /var/www without requiring any changes to the Apache config.  This procedure would be applied after a fresh install of Server 10.10 with the "LAMP server" configuration selected.

I imagine that the procedure would include things like this:


sudo chmod 755 /var /var/www /var/www/script.cgi
# Append the following onto /etc/apache2/httpd.conf:
...
(... some combination of AddHandler, Options, etc. ...)
...
# Make sure that script.cgi begins with the line "#!/bin/sh"
sudo service apache2 restart
etc.
etc.


I have been trying to develop such a procedure using various tips and hints from about a dozen different sources.  No matter what I do, the script is either downloaded, or else I get "You don't have permission to access /script.cgi".  I am probably forgetting some little thing, so I think it's very important to have a totally comprehensive checklist of procedures.

(I'm aware of the recommendation to use /usr/lib/cgi-bin for script execution.  However, this particular application uses extensive scripts mixed with html files, and it's too much work to reorganize it to separate the scripts from the html.)

---

