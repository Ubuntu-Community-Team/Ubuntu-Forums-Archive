---
title: "FTP Server"
date: 2006-10-01
forum: Server Platforms
---

### Post by lugos on 2006-10-01
Hello,

I have set up an Ubuntu Web Server, and I would also like to set up FTP.  I use my laptop to develop html/php, and I would like to FTP the files over to my web server using either SmartFTP and/or the FTP tool/client that comes with Dreamweaver.  Is there a tutorial in the Wiki or somewhere else maybe that I can look at to set it up?  I've also read that there are a few options available.  I would prefer to use FTP with user accounts.  Also, I will possibly be hosting two or more sites on my web server.  Any help would be greatly appreciated.

Thanks in advance

---

### Post by Mr Frosti on 2006-10-01
I would recommend using SFTP over FTP. The reasons for this are security. FTP allows for a connection over an unencrypted channel, so anyone can sniff your username and password and compromise your machine.

To run SFTP, you can install the "openssh-server" package. This will provide you SSH, SFTP, and SCP utilities, and there is no additional configuration to do.

---

### Post by lugos on 2006-10-01
So I can just do that, open up SmartFTP, type in my url, and start transferring files?

---

### Post by K.Mandla on 2006-10-01
I've used vsftpd as a server client on a machine at home, then used SmartFTP from my office to access it. vsftpd is fairly easy to set up ... kind of ... sometimes. ... :rolleyes:

---

### Post by lugos on 2006-10-07
OK, I've installed the openssh-server using Synaptic Package Manager.  I would like to use SFTP, as was stated above, for security reasons.  How can I start uploading files to my web server?  Can I use an FTP client like SmartFTP or Dreamweaver?

Thanks in advance for the help.

---

### Post by lugos on 2006-10-08
I was able to type the 'ssh www.mydomain.com' in the command line on my Ubuntu Desktop and I was able to get access to my Ubuntu Server.  However, when I used SmartFTP to try and access my Ubuntu Server from my Windows XP desktop, I could not do it.  Is there something I haven't done or am not doing right?

Thanks in advance for the help.

---

### Post by lugos on 2006-10-08
OK, I found out that SmartFTP does not support ssh.  However, Dreamweaver does.  So I configured the Dreamweaver FTP tool and I'm able to connect fine, however, it appears that permissions are set correctly.  Let's say my user name is jdub.  How can I get jdub the permissions to copy files/directories to my web directory?

Any help would be greatly appreciated.  Thanks in advance for the assistance.

---

### Post by lugos on 2006-10-09
A quick search on this great community support forum gave me the answer I was looking for.  I was able to get Dreamweaver to successfully transfer files and directories to my web server.  

Thank you Ubuntu Forums for your second to none support!!

---

