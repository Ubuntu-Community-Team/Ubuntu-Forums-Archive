---
title: "Access Restrictions and Remote Desktop"
date: 2009-11-09
forum: Server Platforms
---

### Post by madprofessor on 2009-11-09
This is a two parter. First question is this: When I had Windows XP a while back, I successfully installed Filezilla Server. It allowed me to specifically set a folder as an individuals home folder. How do I do this in Ubuntu Server?

Second question is: I set my server up in GUI mode to be accessed remotely. When I set it up I had a monitor, keyboard, mouse and ethernet hooked up and tried to access it from a different computer and it worked. But when I moved it to a different spot in the shop, same IP address, I get this message

> Connection to 192.168.1.28 was closed

Any help or ideas would be appreciated. Thanks in advanced.

---

### Post by BQAggie2006 on 2009-11-09
> **madprofessor said:**
> This is a two parter. First question is this: When I had Windows XP a while back, I successfully installed Filezilla Server. It allowed me to specifically set a folder as an individuals home folder. How do I do this in Ubuntu Server?


Are you trying to restrict the users to only access their home folder or are you trying to just specify the user's home folder?

---

### Post by madprofessor on 2009-11-09
i'm trying to set the folder that they begin at when they log in.

---

### Post by BQAggie2006 on 2009-11-09
With VSFTPD, the FTP server documented in the Ubuntu Server Guide, a user will start their session in the folder that is designated as their system home folder (e.x. /home/alice, /home/bob). If you would like the user account to have a different home folder, you can specify it during the user creation process or by modifying the /etc/passwd file.

VSFTPD can then be configured to allow local users to login, upload, and download files.

Or, if you'd like, you can confine the user to their home directory by configuring VSFTPD to chroot local users.

Here is the Ubuntu Server Guide section over VSFTPD: [https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html)

---

### Post by cariboo on 2009-11-10
You need to be logged into the server in order to use remote desktop.

If you can access the server via ssh, you can use X forwarding to run gui apps from the server. If you have ssh installed, you don't need an ftp server, just use sftp to manipulate files.

---

### Post by madprofessor on 2009-11-10
Thanks for all the advice. I really appreciate it. This will get me pointed in the right direction.

---

### Post by madprofessor on 2009-11-11
Just an update, I was able to edit the passwd file and it worked flawlessly. Thanks once again for the help.

---

