---
title: "Remote filesharing like samba"
date: 2015-08-21
forum: Server Platforms
---

### Post by Anton_de_Goede on 2015-08-21
I would like to get your help on the following. We are using Ubuntu server 14.04 for some time now and it works perfect (before we used OSX server). The only thing I need to get working is the remote filesharing. Al the files are on the server at work. At the office we work with only one Sambu user which is used for about 12 employees. This works great. We have some people working from home time-to-time. I would like them to work on the server like they where in the office. We worked with FTP before but this gives issues with permissions, groups, users, etc. I hoped there was a way to just be Samba user from home. I use SSH from home myself but people here are not familiar with terminal/SSH and also the Mac's our people work with do not have a working SSH/Finder option.

Can anyone help me with a solution where people can access the fileserver like they where in the office?

---

### Post by SeijiSensei on 2015-08-21
The CIFS protocol really isn't secure enough to share files over the public Internet.  If you are supporting Windows users, I recommend WinSCP, which encrypts all the transactions using SSH.  As long as the server has the openssh-server package installed, you can use WinSCP.

I don't know anything about Macs, but I would guess there is a similar option that uses SCP or SFTP.

Another option that requires nothing more than a browser is [WebDAV]("https://www.digitalocean.com/community/tutorials/how-to-configure-webdav-access-with-apache-on-ubuntu-12-04") over an SSL connection.

---

### Post by Lars Noodén on 2015-08-21
For OS X, there is Cyberduck as an SFTP client.

---

### Post by tripp98 on 2015-08-21
Setup a vpn then they can access it like they are in the office.

---

### Post by TheFu on 2015-08-21
+1 for using sftp.  Filezilla is a client for any platform.  WinSCP is a nice client for Windows.  For Linux, any of the file managers (nautilus, pcmanfm, thunar, etc ...) support sftp:// URLs.

You get the idea.  sftp is secure from anywhere in the world, provided they don't use passwords and only use ssh-keys.

---

