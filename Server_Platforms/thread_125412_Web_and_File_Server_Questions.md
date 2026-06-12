---
title: "Web and File Server Questions"
date: 2006-02-03
forum: Server Platforms
---

### Post by spyke01 on 2006-02-03
high guys, im developing a line of afordable but powerful servers, and i want to use ubuntu for file, web, print, database, and application servers.

What kind of programs can i use to allow someone to ftp into the www directory of apache and upload or download files? Is there a good tutorial for doing file and printer sharing with windows and linux computers? Also whats a good firewall that can be used, i want to firewall off the mysql databases so that only the server can access them through php files and no one on the net can but through those same php files.

Also, what kind of programs do you suggest i try for these kind of systems, i plan on devoting this weekend to learn the installation and configuration of these programs, starting at 5am

Ill be using xubuntu for the gui and bash for the shell.

---

### Post by LordHunter317 on 2006-02-03
[QUOTE=spyke01]high guys, im developing a line of afordable but powerful servers, and i want to use ubuntu for file, web, print, database, and application servers.[/quote]Not to sound mean, but if you need end-to-end recommendations on what to use to implement this product, you probably lack the skills to bring something saleable to fruition.

> What kind of programs can i use to allow someone to ftp into the www directory of apache and upload or download files?An FTP server.  vsftpd is as good choice as any.  However, FTP is nortiously insecure and buggy, but expected.  IF you plan on offering SMB/CIFS file serving, use that is better.  Or use SFTP with appropriate shell restrictions (rssh)

> Is there a good tutorial for doing file and printer sharing with windows and linux computers?Samba.org is authortative.

>  Also whats a good firewall that can be used, i want to firewall off the mysql databases so that only the server can access them through php files and no one on the net can but through those same php files.You wouldn't and you don't want to deny that behavior.  Most of my databases have to be accessed over the network.  At anyrate, you'd simply configure mysql to not listen on the network.

---

