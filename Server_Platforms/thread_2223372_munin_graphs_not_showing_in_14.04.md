---
title: "munin graphs not showing in 14.04"
date: 2014-05-10
forum: Server Platforms
---

### Post by dschuur on 2014-05-10
I have setup munin for monitoring on an Ubuntu 14.04 server, and I am running into issues viewing the munin graphs.

I believe the Apache2 configuration is correct: I have setup the munin.conf file in /etc/apache2/conf-available/ and then enabled it (I discovered the default munin.conf file is not configured for Apache 2.4 -- one needs to change the "Order allow,deny" and "allow from" lines to the new Apache 2.4 syntax). I can see the html portions of my munin webpage at [http://myserver/munin/](http://myserver/munin/) but the graphs do not appear.

Looking inside /var/cache/munin/www it appears the html files are world readable, but not the graph image (*.png) files. The graph image files are set with file permissions of 660. I tried "forcing" the image files to be world readable by chmod'ing the file permission to 664, but gradually they all changed back to 660 (presumably as they were being updated by the munin cron job).

Are others having this issue too? Is this a bug, or perhaps I am overlooking something in the setup? Is it necessary to add the apache user to the munin group in order to read the graph image files? Is /usr/share/munin/munin-graph somehow setting the wrong permissions, or are the umask settings wrong for the munin user?

Any suggestions or advice?

thanks!

---

### Post by dschuur on 2014-05-27
Here's a quick update in case someone stumbles on this thread: I tracked the issue down to a modified **umask** setting in /etc/login.defs. The umask settings were changed from 022 to 027 to prevent users from being able to read files in other peoples home folders. Unfortunately this had the undesired side-effect that the image file permissions inside /var/cache/munin/www were no longer world-readable either...

FYI - I have had other unexpected side-effects from changing the default umask settings in some other programs as well. Thankfully, they are all resolved now. :)


Derek

---

