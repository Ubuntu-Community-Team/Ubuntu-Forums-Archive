---
title: "Permissions on a web server problem."
date: 2008-09-19
forum: Server Platforms
---

### Post by Jeabo on 2008-09-19
I am trying to use a php script in the //var/www directory. 

I used chmod to give the file rights. Using ls, the file is shown as green.

Pulling up the site from another computer gives me an error. It shows a permission problem.

Do I need to change the owner and group of //var/www to www-data?

Thanks!

---

### Post by TurboRush on 2008-09-19
Whats the owner/group and permissions currently at?

What error are you getting specifically?

---

### Post by baudday on 2008-09-19
The file and the folder it's in should be chmodded to 755

---

### Post by Jeabo on 2008-09-19
"Not Found

The requested URL /file.php was not found on this server."

BTW, the php app is called "...::::PHP File Manager" from sourceforge.

I have managed to get the fist page to run. It shows an enter button. When pressing it, I get the above apache error.

Basically, I used chgrp, chown, and chmod 777 on //var/www and chmod 777 on index.php

Sorry if this makes it more difficult for you. I have just migrated from the GUI  terminal commands.

---

### Post by Iowan on 2008-09-19
The word "script" triggered a thought - should PHP scripts be in /var/www or /cgi-bin or /usr/lib/cgi-bin?

---

### Post by baudday on 2008-09-20
no you should be able to see php files in webroot. Are you sure that file does in fact exist?

---

### Post by cariboo on 2008-09-20
Your php file should be owned by root and it should have a permission of 755, giving use a colour really doesn't help.

Jim

---

