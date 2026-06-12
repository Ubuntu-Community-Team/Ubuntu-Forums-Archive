---
title: "[SOLVED] SFTP in natulaus?"
date: 2008-09-23
forum: Security
---

### Post by Kain000 on 2008-09-23
Hello everyone, 
Does anyone know whether or not natulas supports SFTP transfers?  I know it supports plain text FTP transfers as you can browse a remote server and download it with natulas.     I am worried about all my transfers in plain text however and would like to use SFTP if possible with natulas because it's so integrated and handy.    

Also My server is running ProFTP as the ftp client, but I dont know wether or not it can support SFTP transfers, and if so how to change it.  If not any one know a good SFTP client?

any help or advice would be much appreciated.
-Sean

---

### Post by Dave_Connor on 2008-09-23
nautilus, and yes nautilus supports it. Places > Connect to Server > Name of computer or ip, port, folder, etc and then your password for the system and now you can transfer files to your second system when you need to.

---

### Post by cariboo on 2008-09-23
Just type what you need in the location bar eg:

```
sftp://user@server
```

Jim

---

### Post by Kain000 on 2008-09-23
cool thanks guys, question does anyone know a reliable client for my server side machine to host the SFTP tra?\nsfers.  Is the abaility to transfer in SFTP limited by the host program like PROFTP? or should any host program be able to do this?

---

### Post by cariboo on 2008-09-23
You don't need a client, when you use sftp it opens up the directory tree on the remote computer in nautilus. you can do all your file transfer directly from nautilus.. See attached screen shot, not on the first tab that is my home directory on the local computer, and the second tab is the file system on the remote system. I don't remember if nautilus in hardy has tabs, but this is on Intrepid alpha6.

Jim

---

