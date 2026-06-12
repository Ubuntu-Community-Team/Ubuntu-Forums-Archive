---
title: "Cannot edit files in apache /var/www folder?"
date: 2011-09-04
forum: Server Platforms
---

### Post by g{Lv$qjC8w2 on 2011-09-04
Hello, on my dedicated server i rent, there is ubuntu 10.4 + x2go

I am accessing it via x2go and trying to install web server and game server.
I successfully installed apache and the test file works but i cant delete it or edit it!!

I would like to be able to drag files into it for my web server. How do i go about doing this? also i know this isnt a appache forum but can i get FTP access or do i have to login via x2go everytime i want to add files?

THANK YOU SOO MUCH!!!
George

---

### Post by Wim Sturkenboom on 2011-09-04
You need sudo to write in /var/www. Far easier to tell apached to use files somewhere in the user's home directory. Create a directory dedicated to a website and point apache's document root to it.

You need to install ftp server software (e.g. vsftpd) to be able to ftp to your server.

---

### Post by Lars Noodén on 2011-09-04
Better to use SFTP instead of FTP.  It works out of the box with no extra configuration in the package [openssh-server](http://packages.ubuntu.com/natty/openssh-server).  FTP is not secure.

---

### Post by Lars Noodén on 2011-09-04
You can give group write permission to /var/www and access it that way:  Create a group, add yourself to it, then change the group membership of /var/www and set the group sticky bit.

---

### Post by g{Lv$qjC8w2 on 2011-09-04
> **Wim Sturkenboom said:**
> You need sudo to write in /var/www. Far easier to tell apached to use files somewhere in the user's home directory. Create a directory dedicated to a website and point apache's document root to it.

You need to install ftp server software (e.g. vsftpd) to be able to ftp to your server.

How do i get sudo, i know how in terminal, but it seems to have no effect on gui.
Also im not sure why i cant change my user type? I click it and the button presses but nothing happens :(

George

---

### Post by Wim Sturkenboom on 2011-09-05
Which gui? I don't know what x2go is? Quick research shows that it's a remote desktop solution but that's all that I know about it so no idea how to answer your question.

---

### Post by g{Lv$qjC8w2 on 2011-09-05
I mean, sudo works in terminal, when i refer to gui, i mean physical ubuntu, like i can see the desktop. I cannot edit inside /var/www (the physical folder)

---

### Post by volkswagner on 2011-09-05
While logged in you can get sudo privileges with the file manager or with gedit.

To open the file with root priv's run:
```
gksu gedit
```

You will be prompted for your sudo password and then this will open gedit text editor where you will be able to open config files and edit.  WARNING be very careful, be sure you know what files you are editing.  You should always create a backup file before changing any config files.

You can also open your file manager the same way.  If you have Nautilus installed run:

```
gksu nautilus
```

Same warning applies, be very careful.

You can also just open a terminal from your remote session and run commands that way.  Or even easier yet is to just use an SSH session directly into the server and use the command line and and easy editor such as nano.

---

### Post by g{Lv$qjC8w2 on 2011-09-05
I appreciate your help. So there's no actual way to simply drag and drop a website into the www folder because I don't have permission? Also how can I change the root of the website directory to /home/www

The httpd.conf is blank :/

Many Thanks and good returns

---

### Post by volkswagner on 2011-09-05
You should have a gander at the stickey at the top of this forum.

[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

And for setting up Apache Hosts.

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by g{Lv$qjC8w2 on 2011-09-06
okay so i looked at some links you gave and found inside /sites-available and config where i change the site root, from /var/www to /home/desktop/www

desktop is my user BTW

Anyway when i restarted the apache service, i now get this error :@

(13) Permission Denied: make_sock: could not bind to address 0.0.0.0:80 no listening sockets available, shutting down

Unable to open logs.


Yet if i put the config file back how it was, restart ubuntu and apache starts fine....

:@ Im really having problem after problem

---

