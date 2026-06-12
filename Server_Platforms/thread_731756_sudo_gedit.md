---
title: "sudo gedit"
date: 2008-03-22
forum: Server Platforms
---

### Post by ixxalnxxi on 2008-03-22
i am new to linux (first OS i'm actually trying to learn outside of windows) and i was wondering if it was necessary to open files to edit using 'sudo gedit /www/var/file.php'

is it not possible to set myself the permission to just double click and open the file?

also, i am attempting to set up phpmyadmin so that i can control my database that way... where would i go to find out the socket/port and all that other info that it asks for?

---

### Post by unutbu on 2008-03-22
I don't know if it is safe to change the permissions on /www/var/file.php. If you are running a server that is accessible by untrusted computers and do not fully understand the security implications of changing the permissions, I would recommend that you do not do it. Using gksudo is far less of a pain than recovering from a hacked computer.

And by the way, when running any graphical application like gedit as root, the correct command to use is gksudo, not sudo.
"Nine out of ten times it won't make a difference, but the tenth time will really screw you up." 

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by kevdog on 2008-03-22
Minor point

Is really gksu not gksudo as gksudo is simply a symbolic link to gksu  -- Just some info to pass along.

---

### Post by FakeOutdoorsman on 2008-03-22
You can change the /var/www to your user if it is a development machine behind a firewall and unavailable to anyone outside your LAN as described on the [Apache section]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-8edf3f71165ac1563f27de66b69496fd5909b8f2") of the Ubuntu Wiki.

---

