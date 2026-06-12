---
title: "From Filezilla FTP Server to vsftpd - how to configure"
date: 2011-02-21
forum: Server Platforms
---

### Post by Katakana_2 on 2011-02-21
Hy all,
First let me appologize if the question is in the wrong forum, but I feel this is the place to put my questions.
I have used for a long time Filezilla FTP Server on a windows server, for multiple users in my company around the country.
Lately the windows box died and I said let's try ubuntu server 9.10. I configured to my best as a Samba file server and from a speed point of view it works even faster than the Winbox.
Now getting to FTP setup, I had the following problem when setting vsftpd.
How can I enable more directories for the user, each with its own rights. By example, in Filezilla I had two folders for each user: one was a specific folder in which he could also write, and the other was read-only. They were setup with aliases, so that when user login, he sees one continous list of folders.
I tried with symlink, but couldn't do it. Also I searched through the man page but also did not find something specific for this task:)
I would appreciate any help you guys could give me in order to solve this issue, using the best practice for vsftpd. Also note that I am open to other FTP servers as well.

---

### Post by Lars Noodén on 2011-02-22
I would recommed skipping FTP, it's hard to set up and insecure.  Instead use SFTP.  If you can connect using SSH, then you already have SFTP up and runnning.  

FileZilla supports SFTP, so you have a [GUI SFTP client](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications) on hand already.

---

