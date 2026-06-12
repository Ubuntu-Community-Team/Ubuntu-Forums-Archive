---
title: "Web Server Headache!"
date: 2010-03-30
forum: Server Platforms
---

### Post by Datamac on 2010-03-30
Help!  The oddity of permissions with regards to enabling a simple web server is crazy in the GUI of ubuntu.  Now that I have successfully created and save my VirtualHost configuration files in the "sites-available" directory I am getting "permission denied" trying to run "sudo a2ensite www.website1.com"   Help!

---

### Post by Sporkman on 2010-03-31
I believe that sort of thing happens when a command creates a sub-shell in which the root permissions don't propogate - not sure about this, though.

Whenever I run into that kind of problem, I do:

sudo bash
<command you want to run - no "sudo needed>
exit

...i.e. enter a bash shell as root - then you can do whatever you want as root, then exit the root shell.

---

