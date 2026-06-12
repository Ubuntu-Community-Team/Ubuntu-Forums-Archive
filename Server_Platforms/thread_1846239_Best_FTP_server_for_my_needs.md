---
title: "Best FTP server for my needs?"
date: 2011-09-18
forum: Server Platforms
---

### Post by ThunderKid Zero on 2011-09-18
Hey guys,
I'm trying to find a ftp server best for my needs. I'm pretty new to ubuntu Linux (Mac user - Winslowz hater :D) but I did my homework and found a few FTP servers:
- vsftpd
- proftpd
- pure-ftp

if you have any more that I might like, please write me below...

**My situation:**
I'm pretty familiar with Terminal, so a command line is no problem. I've done some programing for iOS and Mac. (and I also hosted a FTP before - but through crappy Winblowz). Although, I would be delighted if there is a GUI FTP server. I'm not too much concerned about security, I would only host some stuff I want to share with friends etc, nothing too important. A next problem is my PC is quite crappy, I've got a small hard drive, thats why I'd like to share my HUGE external drives... 

The computer which I will use for the server, is just standing around, I won't need to use it for other stuff (work). Its only usage is the server.

**What I'm looking for:**
- something more less easy to use (both Terminal/GUI accepted)
- [IMPORTANT] something with good documentation + tutorials and how-tos on the internet
- how I said, security isn't AS important for me
- the FTP server would be used only for private usage - sharing larger files / photos with friends, family...
- [IMPORTANT] virtual user support!
- I'd like to be able to create user groups, where I can specify which folders which group might access. I'd also like to share my external HDDs.
- I'm not looking for something that would need advanced administration (checking every few days...) It would only stand in my cellar and do it's job... Maybe I'll update, add a user etc... here and there, I'm willing to give up a few hours setting it up, but not that I spend 3 hours every week on it.

If you guys have any advice for me or any more questions, please write below.
If you got a answer, about which FTP server is suited best for me, also tell me why you think so.
If you got any good site telling me how to set it up, also write me :-)

Thanks a lot in advance!!!

---

### Post by ThunderKid Zero on 2011-09-19
bumping my own thread..

---

### Post by zeroseven0183 on 2011-09-19
I'm thinking of cloud computing since you mentioned you want to share files with your friends. Have you tried Ubuntu One or Dropbox? No need for FTP really.

---

### Post by ThunderKid Zero on 2011-09-19
I forgot to mention, I'd like to host around 1 TB of data :).

---

### Post by memilanuk on 2011-09-19
Would sftp work for your needs?

It would be secure, and about as simple as running ssh as a service on your local machine and creating user accounts for your 'friends'.  They should be able to connect to the machine either via CLI or GUI clients (I believe FileZilla supports sftp, for instance).

Virtual users may be a bit of a problem... generally speaking you normally need to have a user account set up on the local machine for the user to be able to log in, but it looks like you can set things up so their login 'shell' is just scp/sftp, not a normal interactive shell like bash.

HTH,

Monte

---

### Post by ThunderKid Zero on 2011-09-19
Good idea... Thanks a lot... This is the last alternative I will try (if necessary). Now I'm trying to host through Gadmin-proftpd :) One thing I don't really get, the command line proftpd is running in the background, while the GUI gadmin administrates it's settings, users and so on?

---

### Post by memilanuk on 2011-09-19
Not familiar with it at all... but thats what I would presume its doing.

Another option may be using Webmin to control things, if this computer is going to be setting in a corner without needing a GUI desktop installed (or even if it is).  Webmin has control modules for pretty much any of the FTP servers you may want to use (and SSH).

---

### Post by ThunderKid Zero on 2011-09-19
tested Gadmin now (and got it working after several error messages.) Just for record, when its saying something about the .conf file, just do
```
sudo rm -r /etc/proftpd/proftpd.conf
```
which will delete the conf file. Open Gadmin and it will tell you that it created a NEW .conf file - VIOLA working again.

[B][COLOR="Red"]So: THE FTP SERVER THAT FITS MY NEEDS IS "GADMIN-PROFTPD" FTP SERVER!
[/COLOR][/B]

How can I mark this thread as [solved]?
Thanks a lot every1!

---

### Post by Lars Noodén on 2011-09-19
Use SFTP instead, it is built into the package OpenSSH server and works out of the box with no additional configuration needed.  Unlike FTP, it is secure.  

You also have a wide range of GUI-based SFTP clients, including FileZilla, Nautilus and Konqueror.  [url=http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/]Stop using FTP, learn how to transfer files securely.
[/url]

---

### Post by memilanuk on 2011-09-19
I think you go back and edit the first post, and change the category.

---

