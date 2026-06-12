---
title: "Gedit/Nautilus and SSH file saving"
date: 2010-07-13
forum: Server Platforms
---

### Post by gecka on 2010-07-13
Lox,

I connect with ssh to an Ubuntu server to edit some files in /var/www witch I have set the setgid bit:

# sudo chgrp -R www-data /var/www
# sudo chmod -R 770 /var/www
# sudo chmod -R g+s /var/www

I have added the user "user" to www-data group. Now I connect using ssh as user "user" to my server with nautilus. When I copy files using nautilus file get the group permission 'www-data' as they should. 

But if I edit a file using Gedit and save it, the file's group get changed to "user" group ?!?

How is this possible? Shouldn't setgid bit avoid this?

Regards.

---

### Post by jmlapeyre on 2010-10-10
I have exactly a similar problem here: different behavior in a shell (in which the command line file/directory creation shows the right behavior) and through Nautilus (the group is not properly inherited by the new files)...

> **gecka said:**
> Lox,

I connect with ssh to an Ubuntu server to edit some files in /var/www witch I have set the setgid bit:

# sudo chgrp -R www-data /var/www
# sudo chmod -R 770 /var/www
# sudo chmod -R g+s /var/www

I have added the user "user" to www-data group. Now I connect using ssh as user "user" to my server with nautilus. When I copy files using nautilus file get the group permission 'www-data' as they should. 

But if I edit a file using Gedit and save it, the file's group get changed to "user" group ?!?

How is this possible? Shouldn't setgid bit avoid this?

Regards.

---

### Post by leifharmsen on 2011-02-06
Same problem and it is 2011, using Ubuntu 10.04 lts both at home and on the server.  I ssh with Nautilus, use gedit to edit a php file, and when I save gedit for some mysterious reason changes the file's group from www-data to my username which, well, sucks!  I've been googling all day and can't find a work around or solution.  I'm sure this was not a problem when my server was 8:04 lts.  

Before editing and saving with gedit:
myusername   www-data   drwxr-----

After edtiting and saving with gedit:
myusername   myusername  drwxr----- 

So I have to maunally chgrp the files I edit or apache can't see them anymore - it's driving me nuts. :mad:

Anyone know a fix for this constant annoyance?   Maybe a setting I can change on my server?  Maybe another nice php parsing gui editor works better with nautilus over ssh?

---

### Post by Green Bean on 2012-12-11
I find same bug in 12.04 .  

FYI, same problem existed with jEdit, but only when its "Two-stage save" option was set.  It would upload file to a temporary name, and once complete, then replace remote server's file with temporary upload.  Perhaps the temp file had both owner and group set to ssh login.  When instead two-stage save feature disabled, original file's group is preserved.  Owner may change to ssh login.  So change file's group to www-data to preserve Apache2 functionality.

So if you are looking for an alternate editor, try jEdit with "Two-stage save" option cleared.(Utilities / Global Options / jEdit / Saving & Backup)

---

