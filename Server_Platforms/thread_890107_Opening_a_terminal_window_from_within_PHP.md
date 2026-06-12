---
title: "Opening a terminal window from within PHP"
date: 2008-08-14
forum: Server Platforms
---

### Post by frank754 on 2008-08-14
I've searched far & wide on this, and am wondering if it's possible. I run a lamp server under linux, and it's usually on a laptop not connected to the internet. The user navigates via apache to various pages where he inputs data into forms, and the data is saved to mysql databases.
What I want to do, is have an option to open an external terminal window on top of the viewer's PHP web page, using a command from inside PHP.
He would click on a radio button, then SUBMIT, and then the terminal window would open of the same desktop.
I know the php user is "www-data" and I have been successful so far to let the user mount & unmount an external flash drive, by editing the sudoers file and adding a line like:
www-data  ALL=  NOPASSWD: /bin/mount, /bin/umount, /bin/sh, /usr/bin/gnome-terminal

Given that shell.sh contains the following:
#! /bin/sh
/usr/bin/gnome-terminal --window

I can never get any of these commands to work under php:   

$execCmd = ("/var/www/shell.sh");
exec($execCmd);

$execCmd = ("sudo sh /var/www/shell.sh");
exec($execCmd);

(even if the owner of this file is www-data and it's executable)

Also, this and many variations won't work either:

$execCmd = ("sudo /usr/bin/gnome-terminal");
exec($execCmd);

nor if trying to open a gedit window:

$execCmd = ("sudo /usr/bin/gedit ///dir/file");
exec($execCmd);  (if sudoers is set for that)

I don't actually need a terminal, just need to run a command for dosemu to do something in an interactive window, and then open gedit with the result.
Any thoughts on this?

---

### Post by skunkbad on 2008-08-15
I think you are opening up a big can of worms. You, or whoever you are trying to authorize access to the terminal, are way better off using an SSH client like Putty or if you are on Mac/Linux just use its terminal and connect via SSH. Portability shouldn't be a concern, since Putty comes in a portable version that you can put on a USB stick. Putty is only for windows, which is the only OS you really need it for.

---

### Post by Duckyspetrie on 2008-08-15
Hey, look Eric, a virgin!

Nerds!

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

---

### Post by brocky102 on 2008-08-15
i had the same problem with the sudoers file a while ago.
this is how mine ended up so i could restart dansguardian

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias      DANSGUARDIAN = /etc/init.d/dansguardian, /usr/sbin/dansguardian

# User privilege specification
root    ALL=(ALL) ALL
www-data ALL=NOPASSWD: DANSGUARDIAN
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%www-data ALL=NOPASSWD: DANSGUARDIAN
```

don't know if this will help but might put you on the right track. notice that i have **/etc/init.d/dansguardian** and **/usr/sbin/dansguardian** as **/etc/init.d/dansguardian** because it basically called **/usr/sbin/dansguardian** as well

---

### Post by frank754 on 2008-08-15
Thanks, so far, I will play around with it a bit more, if anyone does know what will work please post back. 
It's not critical to do this, as the user can minimize the window and run what is needed from desktop icons, but it would be nice to be able to invoke all of this from within php.

---

