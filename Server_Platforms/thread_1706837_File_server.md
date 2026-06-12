---
title: "File server"
date: 2011-03-14
forum: Server Platforms
---

### Post by enoch99 on 2011-03-14
Hello all,
I wanted to configure a server where users can access files(would be better if it can be done from browsers)both download and upload using their usernames and passwords. There are different departments and sub departments, users in a sub department are allowed to access their personal files and their respective sub department's files. The head department is supposed to access all the sub departments' files. The clients are windows. What are the servers that I need to use for this purpose? Samba with kerberos? Vsftpd? Please be kind to drop some helping information.....
Thanks
UBUNTU ROX!

---

### Post by headvampyre@hotmail.co.uk on 2011-03-14
Firstly are you running a Windows style domain? - Can be hosted from Samba/Samba4 or windows server.

Upload would have to be done through FTP, or for less open ports - PHP connecting to a local app through some sort of data stream. The app could be wrote in any language of choice, E.G. C/C++, Python, etc. - This is only if your doing the file access via a web browser. For Windows explorer(local file browser), all youll need is some variant of Samba.

---

### Post by rubylaser on 2011-03-14
I assume when you say upload / download, you actually mean file sharing, because making users use a web form on the LAN is not the most effective way to share files.  If you already have Active Directory (AD) setup, using SAMBA on your Ubuntu server is probably the easiest way to go.  Just bind it to the domain, and you can use AD to manage the permissions on the file shares.

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

---

### Post by kevinthecomputerguy on 2011-03-15
[http://woodel.com](http://woodel.com)

---

### Post by HermanAB on 2011-03-15
Here is a preconfigured VM that does what you want:
[http://bitnami.org/stack/knowledgetree](http://bitnami.org/stack/knowledgetree)

Can hardly be any easier.

---

