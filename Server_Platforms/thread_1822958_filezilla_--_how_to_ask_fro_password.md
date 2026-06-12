---
title: "filezilla -- how to ask fro password"
date: 2011-08-11
forum: Server Platforms
---

### Post by ghelis on 2011-08-11
Hello,i created a domain and used filezilla and everything works fine.
Now,i want in order to have someone access to my domain,to ask him for username and password.

How can i do this?

Thank you!

---

### Post by Wim Sturkenboom on 2011-08-11
Before we're wasting your time by sending you in the wrong direction, are you talking about ftp access or web access?

---

### Post by ghelis on 2011-08-11
Hello,i want ftp access.(but if you can give any direction for web also)
I used vsftpd from [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup")

,is this the only way?

( from my pc i am connecting ok to my domain and i can download the files i uploaded, from other pc in my house,it asks for username and password from my router interface!!! and i tried from my cell phone (not from my router)to connect and it shows me the page "it works")

Thanks!

---

### Post by Wim Sturkenboom on 2011-08-11
Your cellphone probably connects to the webserver;'it works' is the default apache webpage on your server (contents of /var/www/index.html). Username/password stuff can be done using e.g. .htaccess

Easiest way to prompt others for usernae/password for the ftp server is to make them system users (other users on the system). You should jail them to their home directory so they can't snoop around in the file system (e.g. pull the password file). You can also block their normal access (e.g. when physically behind the machine) to the system by giving the a shell like *_/bin/false_*).

Regarding vsftpd.conf, I have used [http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html) as guideline. Written for Fedora but I could easily apply it in my Slackware server and you should be able to apply it to your Ubuntu server.

---

