---
title: "Password protected server"
date: 2006-05-28
forum: Server Platforms
---

### Post by atomic16 on 2006-05-28
I am running ubuntu 6.06, I would like to have a server that I can upload to from other computers and is password protected. I would use it as a backup server, I am a newbie to linux so a GUI is a must. I really can't do much more than click an install file to install it. Thanks.

---

### Post by adwait on 2006-05-28
How about setting up an FTP server? Run this:
```
sudo apt-get install vsftp
``` 
This will fetch and install the program. Then run
```
sudo rcconf
``` 
Use your space bar to mark the check box next to vsftp so that it is started everytime your computer starts. Save and exit.

You are done! From other computers simple enter your computers IP address and enter your username/password when asked for FTP username/password.

---

### Post by atomic16 on 2006-05-28
is this secure, so that no one can easily get through, I don't need super security but it should be good?

---

### Post by adwait on 2006-05-28
Yes, to login to that FTP server, you will need a username/password on your machine.

---

### Post by mrcowcow on 2006-05-29
You actually have to configure it to allow user logins. And disabling the anonymous account would be a good idea too. [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html) has a list of all the options editable in the conf file. You might want to change some others too.

---

### Post by atomic16 on 2006-06-04
ok so I got my computer  back online, now I tried VSFTPD but I can't get it to work, can anyone recomend a password server with a gui?

---

### Post by juicybananahead on 2006-06-05
How about installing ssh? I know you don't want to use the command line but this is relatively painless.

Open up a terminal (Applications -> Accessories -> Terminal) and type in ```
sudo apt-get install ssh
```. From there, if you want to transfer files to/from your server use [WinSCP]("http://winscp.net/download/winscp381setup.exe") (Windows) or [gFTP]("http://ubuntuguide.org/#gftp") (Linux) as your SFTP GUI. I'd also heartily recommend hardening your ssh configuration if you are going to open it up the internet at large.

Alternatively, if you're just uploading from computers on a home LAN, why not just set up [a Samba share]("http://ubuntuguide.org/#sambaserver") that requires authentication (username/password)?

// juicy

---

