---
title: "Setting up FTP to send data into the server"
date: 2008-07-07
forum: Server Platforms
---

### Post by cooldude_832 on 2008-07-07
I'm running Ubuntu 8.0.4 inside of my xp system so I can run LAMP in the background and use the xp system to run all the web stuff through firefox (phpmyadmin etc.)

I haev apache setup, mysql, phpmyadmin all are good but now I want to be able to use my ftp client in my text editor (notepad++) to send files to the LAMP server I have set up.  

I can't figure out how to set up any ftp out there (the documentation are mostly geared toward fedora or red hat)

The networking is all fine I just can't figure out how to define FTP users + their base directory etc.

---

### Post by simonapnic on 2008-07-07
I suggest you use vsftpd (The Very Secure FTP Daemon).
You can install it easily with apt-get vsftpd (as root) on your server machine.
Configuring it is easy, you can take a look here:
[http://www.brennan.id.au/14-FTP_Server.html]("http://www.brennan.id.au/14-FTP_Server.html")

---

### Post by cooldude_832 on 2008-07-07
I ran sudo apt-get install vsftpd

and its up to date
but the first line of the tutorial points to a location not there

any idea???

---

### Post by cooldude_832 on 2008-07-07
I'm also having permission issues on it too.

---

