---
title: "FTP privileges question"
date: 2009-01-29
forum: Server Platforms
---

### Post by mkriegs90 on 2009-01-29
I have a personal Ubuntu server that I setup myself, right now it's only setup to serve files off http and sftp and all I have on it at the moment are just files, no HTML. Also, I'm not too clear on the difference between sftp and ftp, all I know is that I'm using sftp and I've been told it's better, actually I'm pretty new to this in general.

So, my question is say I want to give someone ftp access but I only want to give them the ability to read/download files. IE: I don't want to give them the ability to upload/delete files or SSH access. How would I do that?

---

### Post by surj08 on 2009-01-29
you want to do a chmod on the folder that houses the ftp files so you'd probably want to do "sudo chmod 775" If its FTP. Either way that will give you full controll as a user (if you logon to the ftp) and if you dont logon it will only let you read (download) the files

---

