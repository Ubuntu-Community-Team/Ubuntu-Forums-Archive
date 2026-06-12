---
title: "Auto start a file on startup"
date: 2009-06-26
forum: Server Platforms
---

### Post by tutunmayan on 2009-06-26
Hi I made a php socket chat server. I can manualy start it and it works fine.

I need to know how can I make this file run automaticly on server startup?

[LIST]
[*]File located at **/var/www/chat/socketServer.php**
[*]First line of file is **#!/usr/bin/php -q**
[/LIST]

---

### Post by Luke has no name on 2009-06-26
I believe you can add a symlink to that file in /etc/init.d/

---

### Post by tutunmayan on 2009-06-26
I am not familiar with linux yet :(

Does this meatn create a file named start-server.sh with a content **/var/www/chat/socketServer.php ** and put it into etc/init.d

> **Luke has no name said:**
> I believe you can add a symlink to that file in /etc/init.d/

---

### Post by zharmad on 2009-06-26
You should be able to make the symlink using 
ln -s /var/www/chat/socketServer.php /etc/init.d/socketServer.php 
and it should then run that script at startup.

---

### Post by tutunmayan on 2009-06-27
I executed symlink command.
when I **ls -l** etc/init.d directory the link is there :
**lrwxrwxrwx 1 root root    29 2009-06-27 10:51 [COLOR="MediumTurquoise"]socketShell.php[/COLOR] ->  [COLOR="SeaGreen"]/var/www/chat/socketShell.php[/COLOR] **

but when I reboot server script does not start and it is not listed in processes (I checked by typing ps -A)


Any ideas?

> **zharmad said:**
> You should be able to make the symlink using 
ln -s /var/www/chat/socketServer.php /etc/init.d/socketServer.php 
and it should then run that script at startup.

---

### Post by kerry_s on 2009-06-27
put the command you would use to start it in /etc/rc.local with a "&" on the end.
example:
your-program &

remember it already runs as root so you don't need sudo.

---

### Post by tutunmayan on 2009-06-27
Thanks, it worked !

> **kerry_s said:**
> put the command you would use to start it in /etc/rc.local with a "&" on the end.
example:
your-program &

remember it already runs as root so you don't need sudo.

---

### Post by Yuki_Nagato on 2009-06-27
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Let the Caps_Lock key do some useful work
xmodmap -e 'remove lock = Caps_Lock'
xmodmap -e 'add control = Caps_Lock'

exit 0

```

Is this a sane rc.local file?  It is located in the "/etc/" directory, not the "/etc/init.d" version.

These commands fix my keyboard when run in a terminal emulator, but have no effect when I log in.

I am running xmonad instead of GNOME, if that matters.

---

### Post by kerry_s on 2009-06-27
> **Yuki_Nagato said:**
> ```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Let the Caps_Lock key do some useful work
xmodmap -e 'remove lock = Caps_Lock'
xmodmap -e 'add control = Caps_Lock'

exit 0

```

Is this a sane rc.local file?  It is located in the "/etc/" directory, not the "/etc/init.d" version.

These commands fix my keyboard when run in a terminal emulator, but have no effect when I log in.

I am running xmonad instead of GNOME, if that matters.

no, for xmodmap you need to create a ~/.Xmodmap file with your settings.

**your-editor ~/.Xmodmap**
put your settings:
```
remove lock = Caps_Lock
add control = Caps_Lock
```

to make sure it loads:
**your-editor ~/.profile**
add this line:
```
xmodmap $HOME/.Xmodmap
```

---

### Post by Yuki_Nagato on 2009-06-27
> **kerry_s said:**
> no, for xmodmap you need to create a ~/.Xmodmap file with your settings.

**your-editor ~/.Xmodmap**
put your settings:
```
remove lock = Caps_Lock
add control = Caps_Lock
```

to make sure it loads:
**your-editor ~/.profile**
add this line:
```
xmodmap $HOME/.Xmodmap
```

It works correctly now.

Thank you.

---

### Post by kerry_s on 2009-06-27
> **Yuki_Nagato said:**
> It works correctly now.

Thank you.

your welcome.

---

