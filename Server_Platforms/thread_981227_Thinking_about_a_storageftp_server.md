---
title: "Thinking about a storage/ftp server"
date: 2008-11-13
forum: Server Platforms
---

### Post by College_Trained on 2008-11-13
Hey all,
I've been thinking about setting up a private ftp/storage server so the family has a place to store all important files, and so that I can store all my backed up DVD's to it as well.
This is all in the planning stage so far. The things I will need to do are read/write files to the server, stream my movies from the server, and possibly more later on. I was hoping you could give me advice on what kind of hardware I need and how to set it up once the machine is built.
I am going to have the server based out of my dorm room and I'm not sure if the college's network will allow a connection. (I will have to ask tomorrow.)
Both family machines are running XP and I am running Ubuntu 8.10 on my laptop. My thought was to run Ubuntu Server Edition 8.04 or 8.10.
Any general help/ideas/etc. would be of great help.
Also is there a GUI friendly and also secure way that they can remotely connect to the server? They don't have the linux/command line experience.

Thanks for all the help in advance.

---

### Post by pdtpatrick on 2008-11-13
Hi - 

You can install vsftpd server (or pure-ftpd-whichever you prefer) which is pretty straight forward to install. Google it and im sure you will come across a tutorial for it. 

As far as a GUI client - you can FileZilla and connect to the server. Make sure when they connect that they use SSH instead of telnet. Once you install filezilla you can click on file, new site and in here you can change the protocol to use SSH.

Also you might want to becareful if you are putting important papers on a FTP server, never know who might be watching but in any case, make sure it is very lockdown if you plan on putting important papers on there.

Otherwise, you should be set to go and have this running in less than 2hours (if this is your first time).

Have fun! :)

---

