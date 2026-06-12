---
title: "FTP and or a HTTP mirror of SAMBA shares"
date: 2011-12-06
forum: Server Platforms
---

### Post by catsrules on 2011-12-06
I am looking in to remote access for a file server.
Right now the server is setup for SAMBA and sharing files locally.
SAMBA is great for local stuff, but I would like to look at FTP and or HTTP for remote access. And I would like this to be all secure, so it guess SFTP or FTPS and HTTPS.

I have started looking at FTP and found vsftpd and proftpd. But from what I can tell, it based the folder share from the users home directory. I want it to pull multiple locations like SAMBA does. 

My ultimate goal would be to mirror what my SAMBA shares are set to. So I could log in with the same user and it would look the same to what I see on SAMBA.

Any suggestions?
Thanks

---

### Post by Lars Noodén on 2011-12-06
SFTP is the best option there for remote access.  You then have your choice of clients like Nautilus, Dolphin and FileZilla.  There is also [SSHFS](http://www.linuxjournal.com/article/8904) which is a very clever and useful solution.

---

### Post by catsrules on 2011-12-06
Thanks for your reply.

I think I got an idea of how to get FTP working, by using symbolic links in the home directories.  It isn't exactly what I was looking for but, it should work for what I am doing. 

My next problem is getting HTTPs working.

---

### Post by catsrules on 2011-12-13
*Update*

I found a program called owncloud. That is an amazing little web program, lets you upload and download from your personal "cloud".
I just added some symbolic links to that data folders and I can access my files I am sharing over samba

---

