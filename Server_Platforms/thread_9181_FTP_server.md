---
title: "FTP server"
date: 2004-12-25
forum: Server Platforms
---

### Post by Croccifixio on 2004-12-25
Hello everybody, this is my first post :P, i have been a yoper user, now moved on to ubuntu because of cedega/yoper issues, i love ubuntu, really a great os, now i would like to start an ftp server, i am really new to linux so i would like to ask for some guidelines, what to do, where , how? tips?
Thanks!

~Cross

---

### Post by swerner on 2004-12-25
For your FTP server
```
sudo apt-get install proftpd
``` 
and volia, you have your FTP server. Be sure to configure it, visit [http://www.proftpd.org/](http://www.proftpd.org/) for documentation.

As for tips, read the [From DOS/Windows to Linux HOWTO](http://www.faqs.org/docs/Linux-HOWTO/DOS-Win-to-Linux-HOWTO.html). And make use of linux searching in Google, [http://www.google.co.nz/linux](http://www.google.co.nz/linux).

Enjoy :)

---

### Post by charleyramm on 2004-12-27
I wonder,  is there a gui configuration tool for any ftp server? This would be a nice thing for ubuntu especially.  Something resembling cerberus ftp server, on windows.

---

### Post by charleyramm on 2004-12-27
This looks nice, has anybody tried it?

[GProFTPD](http://mange.dynup.net/linux.html)

---

### Post by p!=f on 2004-12-29
I don't recommend proftpd for a production server. Use pure-ftpd instead.
> 
 Pure-FTPd is a fast, production-quality, standards-conformant FTP
 server based upon Troll-FTPd. Features include chrooted home directories,
 virtual domains, built-in 'ls', anti-warez system, configurable ports for
 passive downloads, FXP protocol, bandwidth throttling, ratios,
 fortune files, Apache-like log files, fast standalone mode, atomic uploads,
 text / HTML / XML real-time status report, virtual users, virtual quotas,
 privilege separation, SSL/TLS and more.


---

### Post by Croccifixio on 2004-12-29
basicly the use of my ftp will be between me and a bunch of freinds, im setting up my old pc as a server , so the use will be between 10-15 people, maybe a bit less but it wont be major, so i dont know, and how does that "anti-warez" system work?, thanks for the replies, im still looking for more suggestions ;)

---

### Post by randy on 2004-12-29
vsftpd--Thats the easiest to setup ftp server daemon that I've ever used.

---

### Post by Hellsteeth on 2004-12-31
Everybody has their favourite. proftpd and vsftpd are the front-runners. Either and all can usually be configured for anti-warez. This has many meanings however usually taken in ftp servers to mean having two separate directories. One “incoming” you can upload into but not download from and one “pub” directory you can download from but not upload into. Depending on your individual situation you can also decide if users can even list the contents of the incoming directory. This is achieved between a combination of ftpd settings and file/directory permissions. Check out the guides on the websites for details.
This prevents others from using your ftp site to distribute unwanted material as only the adminsitartor can move content from incomming to pub.

As for a gui, i'd reccomend none. If this is to be a server on an old pc, you need to preserve as many clock cyles as possible. You do not need X or Gnome. You will also learn quicker by editing the config files directly. If you still need access to a gui then consider webmin.

---

### Post by Croccifixio on 2004-12-31
[QUOTE=Hellsteeth]Everybody has their favourite. proftpd and vsftpd are the front-runners. Either and all can usually be configured for anti-warez. This has many meanings however usually taken in ftp servers to mean having two separate directories. One “incoming” you can upload into but not download from and one “pub” directory you can download from but not upload into. Depending on your individual situation you can also decide if users can even list the contents of the incoming directory. This is achieved between a combination of ftpd settings and file/directory permissions. Check out the guides on the websites for details.
This prevents others from using your ftp site to distribute unwanted material as only the adminsitartor can move content from incomming to pub.

As for a gui, i'd reccomend none. If this is to be a server on an old pc, you need to preserve as many clock cyles as possible. You do not need X or Gnome. You will also learn quicker by editing the config files directly. If you still need access to a gui then consider webmin.[/QUOTE]
I would love to do it without X or Gnome but i dont know how to do that, im really nubish :(

---

### Post by Hellsteeth on 2005-01-01
Everybody was rubbish once until they tried........
Give it a go, you may surprise yourself.

Good luck.

---

### Post by Croccifixio on 2005-01-02
[QUOTE=Hellsteeth]Everybody was rubbish once until they tried........
Give it a go, you may surprise yourself.

Good luck.[/QUOTE]
 i dont even know how to NOT start X and Gnome , without mentioning all the commands i will need :\

---

### Post by britishtrident on 2005-01-02
Pure-Ftp  is the go easy install from tar ball provided you  have the GNU C compiler installed.


Issues with Yoper  ? --- a good system for home desktops never found any show stopper  with it except the relibility of the  yoper.com web site.
Having said it wouldn't be my choice for a server for that a solid  Debian base  is the best hence I my choice of Ubuntu.

---

### Post by maddog39 on 2006-12-22
I'm trying to setup my FTP server to be purely anonymous but all the GUI's wont let you add any user without a password and there isn't an option for anonymous. So how do you set it up to be anonymous in gProFTPD?

---

