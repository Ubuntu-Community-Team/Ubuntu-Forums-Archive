---
title: "FTP Server or other means of transfering files"
date: 2005-05-08
forum: Server Platforms
---

### Post by SychoSly on 2005-05-08
I have Ubuntu installed with the "server" installation so I have no GUI. I am running Apache off of it, and I am looking for a way of transfering files to the Ubuntu system from my windows system.

What is a way of transfering files to the ubuntu system? Are there any FTP servers that I can set up without a GUI?

Sorry I am new to this.

---

### Post by kvidell on 2005-05-08
[QUOTE=SychoSly]I have Ubuntu installed with the "server" installation so I have no GUI. I am running Apache off of it, and I am looking for a way of transfering files to the Ubuntu system from my windows system.

What is a way of transfering files to the ubuntu system? Are there any FTP servers that I can set up without a GUI?

Sorry I am new to this.[/QUOTE]
sudo apt-get install ftpd
:) Good server. Does the usual stuff.
- Kev

---

### Post by LordHunter317 on 2005-05-08
No, don't use that FTP server, it's a POS.
Well, that's being polite, actually.

If you **must** use FTP, then use proftpd or vsftpd.  Don't settle for anything else.

But installing SSH and using a SFTP client (like WinSCP3) is a better choice.  You get shell-administration for free, and the connections are encrypted.

---

### Post by SychoSly on 2005-05-08
[QUOTE=kvidell]sudo apt-get install ftpd
:) Good server. Does the usual stuff.
- Kev[/QUOTE]

So I can set it up without a GUI?

Thanks. I will look into it.

---

### Post by kvidell on 2005-05-08
[QUOTE=LordHunter317]No, don't use that FTP server, it's a POS.
Well, that's being polite, actually.

If you **must** use FTP, then use proftpd or vsftpd.  Don't settle for anything else.

But installing SSH and using a SFTP client (like WinSCP3) is a better choice.  You get shell-administration for free, and the connections are encrypted.[/QUOTE]
 apt-get install ftpd does install the proftpd ;)
```
63/clint-t42p:/etc# apt-get install ftpd
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  proftpd proftpd-common
The following NEW packages will be installed:
  ftpd
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 43.1kB of archives.
After unpacking 1278kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com breezy/universe ftpd 0.17-19 [43.1kB]
Fetched 43.1kB in 4s (8975B/s)          

Preconfiguring packages ...
(Reading database ... 97378 files and directories currently installed.)
Removing proftpd ...
ProFTPd is started from inetd/xinetd.
Removing proftpd-common ...
Selecting previously deselected package ftpd.
(Reading database ... 97348 files and directories currently installed.)
Unpacking ftpd (from .../archives/ftpd_0.17-19_i386.deb) ...
Setting up ftpd (0.17-19) ...
Installing new version of config file /etc/ftpusers ...
```

Sorry :)
- Kev

---

### Post by kvidell on 2005-05-08
[QUOTE=LordHunter317]No, don't use that FTP server, it's a POS.
Well, that's being polite, actually.

If you **must** use FTP, then use proftpd or vsftpd.  Don't settle for anything else.

But installing SSH and using a SFTP client (like WinSCP3) is a better choice.  You get shell-administration for free, and the connections are encrypted.[/QUOTE]
 bah. You're right. I meant that one.
I misread apt-cache and thought ftpd was an alias for the proftpd in the repos.

Apologies,
- Kev

---

### Post by az on 2005-05-09
"So I can set it up without a GUI?"

You can do just about everything without a gui.  In fact, you can do more things without a gui than with one.

You can set up nfs instead of ftp.  You can even run samba and have a windows share.

---

### Post by thavid on 2005-05-09
[QUOTE=azz]"So I can set it up without a GUI?"

You can even run samba and have a windows share.[/QUOTE]


I would vote for that in this case... Since he only want's to transfer files between the ubuntu box and the Win box... btw, you'll find a lot of samba configuration files @ [www.samba.org](www.samba.org) to simplify your task... and believe me, it's not that hard to set this up!

---

