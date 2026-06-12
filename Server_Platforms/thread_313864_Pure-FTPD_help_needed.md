---
title: "Pure-FTPD help needed"
date: 2006-12-06
forum: Server Platforms
---

### Post by NumberOne on 2006-12-06
Hello, I am new to linux, but not to computers and servers.  I am a windows consultant and have about 25 years of computer experience, but 0% experience with linux.  

I am trying to get excited about ubuntu, but I am getting very frustrated.  

I have installed ubuntu 6.10 server and the 6.10 gnome desktop.

I have got Apache2 server up and running.

I have MySQL server up and running.

I have been trying to set up an FTP server.

I first tried to install Proftpd.  Using Synaptic pkg mgr I received and error on install  and it would not install GProftpd because of the error generated from Proftpd.

So, I unstalled it.  

I then installed Pure-Ftpd and pure admin and all installed fine.
I have a few problems that I don't know how to fix.
PureFtpd server works if I access it with a system login account.  I cannot get it to work with virtual accounts.  I have used the 2 How to's in the forums.  Step by step, everything works during setup.  When I try to login I get a login dialog from my ftp client as follows.  User login name fine,  then it sends password, and I get authentication failed.  I've tried uninstalling and reinstalling and going through the setup several times with the same results.

Second problem, when I start ubuntu, the PureFtpd server does not start automatically.

Does anyone have any advice to help solve my problems.

Thanks,
Tony

---

### Post by elst on 2006-12-06
It sounds basic, but check the log files for errors first: Linux log messages are typically much more useful than the Windows event logs! You can often get the answer to a problem by pasting the error message into Google: [www.google.com/linux](www.google.com/linux).

Based on what you've said, my hunch would be that the problem lies with MySQL, so I'd also recommend checking that end. The documentation on the Pure-FTPd Web site implies that you have to be careful when setting up MySQL authentication.

[http://www.pureftpd.org/project/pure-ftpd/doc](http://www.pureftpd.org/project/pure-ftpd/doc)

---

### Post by NumberOne on 2006-12-06
I solved my problem:  Being a windows user, I like the GUI.  I was trying to use PureAdmin to create users and assign directories.

Well, PureAdmin just dosen't work when adding or modifing users.

When I created users from the cmd line, and generated new file everything worked.

I visited the PureAdmin web site and they mentioned that ubuntu users were haveing problems.  The said it was related to wrong file locations.

Thanks --

---

