---
title: "-bash seem to block the vsftpd.conf command"
date: 2011-03-16
forum: Server Platforms
---

### Post by krazikoffee on 2011-03-16
hello im new on ubuntu and i really dont have any background on making a server. to be frank is im still a student learning ubuntu server, how to make and configure them.

my problem is that whenever i type the command:
/etc/vsftpd.conf
an error message says that:
-bash /etc/vsftpd.conf: Permission Denied

can someone help me on this problem im still discovering what are the commands on the vsftpd server.

by the way im using the server on VMware.

thanks for the help in advance

---

### Post by soulresin on 2011-03-16
> **krazikoffee said:**
> hello im new on ubuntu and i really dont have any background on making a server. to be frank is im still a student learning ubuntu server, how to make and configure them.

my problem is that whenever i type the command:
/etc/vsftpd.conf
an error message says that:
-bash /etc/vsftpd.conf: Permission Denied

can someone help me on this problem im still discovering what are the commands on the vsftpd server.

by the way im using the server on VMware.

thanks for the help in advance

/etc/vsftpd.conf is the configuration file for vsftpd.  It is not a command to be executed.  If you are wanting to start vsftpd you can use a command such as:

sudo /etc/init.d/vsftpd start

If you are wanting to edit the configuration file, you will want to use a text editor such as pico, nano, or vim:

sudo vim /etc/vsftpd.conf

---

### Post by cipherboy_loc on 2011-03-16
Also, if you install a graphical environment (X server), you could install Gedit, or some similar software and tunnel it over SSH.

Cipherboy

---

### Post by Lars Noodén on 2011-03-17
> **krazikoffee said:**
> hello im new on ubuntu and i really dont have any background on making a server. to be frank is im still a student learning ubuntu server, how to make and configure them....

If you can connect to the machine with SSH then you already have SFTP installed and configured for use as part of the deal.  You probably have at least one [SFTP client](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) already available, too.  

FTP is insecure and FTPS is hard to add to your system.  You probably already have SFTP, so it would make sense to use it.

---

