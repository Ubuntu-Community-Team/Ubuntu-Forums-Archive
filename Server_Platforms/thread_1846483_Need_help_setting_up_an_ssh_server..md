---
title: "Need help setting up an ssh server."
date: 2011-09-19
forum: Server Platforms
---

### Post by DJKEMMET on 2011-09-19
If anyone knows of good tutorials or step by steps could you please send them my way. I'd like to test my proficiency with this. Thanks!


Dj

---

### Post by HugoSerrano on 2011-09-19
Hello!

depends on what you want, but to setup an ssh server you only need to do:

$sudo apt-get install openssh-server

and you're done!

You can login from another machine by: ssh user@server

Regards!

---

### Post by DJKEMMET on 2011-09-19
> **HugoSerrano said:**
> Hello!

depends on what you want, but to setup an ssh server you only need to do:

$sudo apt-get install openssh-server

and you're done!

You can login from another machine by: ssh user@server

Regards!



Thanks so much!! In was wanting to make an FTP server I could get to from anywhere and also a mine craft server for me :PP any thoughts?

---

### Post by elico on 2011-09-19
it depends on the need for the ftp..
i really recommend to you to try to install webmin to manage the server with a nice web-gui
and then try to mange the ftp server from there..

---

### Post by YesWeCan on 2011-09-19
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by cipherboy_loc on 2011-09-19
If you have SSH set up, you don't need FTP. The openssh-server supports the SFTP protocol, which is encrypted and more secure than the standard FTP.  It requires no extra configuration. `man sftp` for more info.


Cipherboy

---

### Post by DJKEMMET on 2011-09-25
> **YesWeCan said:**
> [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

> **cipherboy_loc said:**
> If you have SSH set up, you don't need FTP. The openssh-server supports the SFTP protocol, which is encrypted and more secure than the standard FTP.  It requires no extra configuration. `man sftp` for more info.


Cipherboy

> **elico said:**
> it depends on the need for the ftp..
i really recommend to you to try to install webmin to manage the server with a nice web-gui
and then try to mange the ftp server from there..


Elico- What's the package name?

Cipherboy- Thank you for the tip I'm reading through the mannual right now. 

YesWeCan- thanks for the article, I looked at it and it's on my list now!

---

### Post by patryk77 on 2011-09-25
For webmin:
sudo apt-get install webmin

Also, I usually use Filezilla to connect to SFTP servers from a GUI. If you use the shell then the sftp command is what you need (and of course, it is always good to know your way around the shell)

---

### Post by Elfy on 2011-09-25
Thread closed. Please do not post duplicates, it dilutes community effort.
[http://ubuntuforums.org/showthread.php?t=1849894](http://ubuntuforums.org/showthread.php?t=1849894)

---

