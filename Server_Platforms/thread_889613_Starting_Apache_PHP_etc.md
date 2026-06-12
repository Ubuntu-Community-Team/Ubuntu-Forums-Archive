---
title: "Starting Apache PHP etc"
date: 2008-08-14
forum: Server Platforms
---

### Post by timboellis on 2008-08-14
Is there a way to save on resources of my PC to only start up Apache,MYSQL,PHP when I request it ie. click an icon on the desktop one for start and one for stop

---

### Post by scragar on 2008-08-14
turn off apache and MySQL from the services menu(system>Administration>services)

set up a launcher for this script to launch it in a terminal using sudo, image attached for example

DO NOT USE the chmod option unless you are sure you want to, it will give full perms to everyone to the /var/www folder, this is very unsecure, so unless the box is secure do not run it!


EDIT: image shows apache.pl but the file is .txt it will run fine with either name, but you have to make it executable first(**chmod +x apache.txt** or from the properties box). Don't forget the sudo part, without it the script may hang since it waits for root privileges to do anything other than checking if apache is running.

---

### Post by theyranos on 2008-08-14
You could write a couple of simple shell scripts, like this one to start
```

#!/usr/bin/gksu bash
/etc/init.d/apache2 start
/etc/init.d/mysql start

```

and this one to stop
```

#!/usr/bin/gksu bash
/etc/init.d/mysql start
/etc/init.d/apache2 start

```

Make those scripts executable with **chmod +x**, and you've got easy start- and stop- programs that you can link to from your desktop or your menu.

---

### Post by scragar on 2008-08-14
I prefair mine, it gives a running state(before I wrote this I had way too many instances of stopping apache when it wasn't running, which causes errors BTW), although I understand the want for the little quick launchers, just as long as you remember is apache is running or not.

---

### Post by timboellis on 2008-08-14
> **theyranos said:**
> You could write a couple of simple shell scripts, like this one to start
```

#!/usr/bin/gksu bash
/etc/init.d/apache2 start
/etc/init.d/mysql start

```

and this one to stop
```

#!/usr/bin/gksu bash
/etc/init.d/mysql start
/etc/init.d/apache2 start

```

Make those scripts executable with **chmod +x**, and you've got easy start- and stop- programs that you can link to from your desktop or your menu.

I have tried both and like this idea the best but a quick question how do i manage to get it to run as root so i do not put my password in i changed the sript to sudo /etc/init.d/mysql start am i right?

---

### Post by theyranos on 2008-08-14
The thing that's causing that password popup is the shebang line at the top 
```
#!/usr/bin/gksu bash
```

If you don't want to have to provide a password, you'll have to change that to just
```
#!/bin/bash
```
and then add a **sudo** to the beginning of each line like you said.

Then, you'll need to adjust sudo's settings so it doesn't try to prompt you for a password. (If you're running these scripts from shortcuts and the shortcuts aren't set to show a terminal, having 'sudo' in the script will make it hang while it tries to prompt you for a password with a terminal that isn't there.)

To adjust sudo's settings, you'll need to edit the **/etc/sudoers** file to include a line like this:

```
timboellis ALL = (ALL) ALL, NOPASSWD: /etc/init.d/apache2, /etc/init.d/mysql
``` 

replacing *timboellis* with whatever your username is on your Ubuntu machine.

If the sudoers file already has a line that starts with your name, just add a comma and the NOPASSWD section to the end of that line.

---

