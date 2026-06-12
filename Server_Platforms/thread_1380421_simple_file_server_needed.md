---
title: "simple file server needed"
date: 2010-01-13
forum: Server Platforms
---

### Post by RobTi on 2010-01-13
Hi
I am new to this and would like some advice, i have an old pc that i would like to use as a file server in the home.
I would like to have it store my media files (music,video,photos )and to have a printer connected,all to be accessed by any users in the home.
Can you recommend what software to use and any walkthroughs
Thanks
Robert

---

### Post by lisati on 2010-01-13
One of your options is samba. Don't worry if the "howtos" mention Windows, it can be used for file & printer sharing between Ubuntu boxes.

See here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by nexes128 on 2010-01-13
I'd actually recommend FreeNAS its lightweight and loaded with file sharing options.

---

### Post by falconindy on 2010-01-13
I'd recommend purely using CUPS over Samba for printer sharing. Samba merely interfaces with CUPS to create the connection on the server side -- cut out the middle man. Windows computers can connect to CUPS as if it were an internet printer by connecting to:
```
http://<ip_address_of_server>:631/printers/<printername>
```

---

### Post by confusedstingray on 2010-01-14
here is a good tutorial you can use a newer release of ubuntu like 8.04lts instead of version 7.04

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by frenchn00b on 2010-01-17
> **RobTi said:**
> Hi
I am new to this and would like some advice, i have an old pc that i would like to use as a file server in the home.
I would like to have it store my media files (music,video,photos )and to have a printer connected,all to be accessed by any users in the home.
Can you recommend what software to use and any walkthroughs
Thanks
Robert

This is made for you !!  

Enjoy and please ontribute to the project if you would like the program (mailing me your lines or versiosn) :
[http://easyldap.exofire.net/files/installer/easyldap-installer.sh](http://easyldap.exofire.net/files/installer/easyldap-installer.sh)
 
[screenshot]("http://easyldap.exofire.net/files/installer/shot01.jpg")

---

### Post by HermanAB on 2010-01-17
Howdy,

Well, there is nothing simpler than FTP.  Install vsftp and it works out of the box.  You can access it from Linux machines using the Nautilus file browser and from Windows using FileZilla.

---

