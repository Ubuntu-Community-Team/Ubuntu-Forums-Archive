---
title: "FTP Troubles"
date: 2012-06-10
forum: Server Platforms
---

### Post by leschandrew on 2012-06-10
Okay so I am using Ubuntu Server 12.04 LTS and am trying to upload files via an FTP client to the server. I have samba and vsftpd installed on the server. When I go to upload files, it will only allow me to upload to one directory (my home/usr/ directory). When I try to upload a file to, for example, /home/andrew/music/, my ftp client (filezilla) outputs "permission denied".  Does anyone know what's going on here? I want to be able to upload files onto my server wherever the heck I please. I looked over the configuration file for vsftpd, but couldn't find anything that helped. When I used fedora in the past, I ftp'd right in and could do whatever I wanted to. Not so with ubuntu I guess. Any advice?

---

### Post by nsnidanko on 2012-06-14
> **leschandrew said:**
> Okay so I am using Ubuntu Server 12.04 LTS and am trying to upload files via an FTP client to the server. I have samba and vsftpd installed on the server. When I go to upload files, it will only allow me to upload to one directory (my home/usr/ directory). When I try to upload a file to, for example, /home/andrew/music/, my ftp client (filezilla) outputs "permission denied".  Does anyone know what's going on here? I want to be able to upload files onto my server wherever the heck I please. I looked over the configuration file for vsftpd, but couldn't find anything that helped. When I used fedora in the past, I ftp'd right in and could do whatever I wanted to. Not so with ubuntu I guess. Any advice?


As the error states you do not have permission to write to that directory. Try connecting via ftp using credentials of the user, which has permissions to write to the desired directory. Alternatively you can add write permissions for your ftp user to that directory.

---

