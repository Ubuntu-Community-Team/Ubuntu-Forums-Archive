---
title: "How to document a web application server ?"
date: 2013-01-10
forum: The Cafe
---

### Post by Oxii on 2013-01-10
I have a web app server and I would like to document its configuration but I'm a little bit lost and don't know where to start. I want to include:
-Environment
-OS
-Servers (apache httpd - tomcat)
-app structure
..
.. etc

Does anyone have a template or something similar to help me ?

---

### Post by oldfred on 2013-01-10
I am a desktop user, but that is a start.

I like rsync and add a few commands to provide extra documentation.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I used this as a starting point and added my own commands.
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

This is now getting very old - 2006 but servers have not changed all that much.
       Document system backup or multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)
[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

Does not include a lot of other server folders you probably want to include.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

   Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

