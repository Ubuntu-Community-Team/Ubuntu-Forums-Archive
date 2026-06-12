---
title: "RemoteFSMan-Mounting FTP/FTPS,...etc with GUI"
date: 2008-01-27
forum: The Cafe
---

### Post by PCMan on 2008-01-27
File managers, like PCManFM, doesn't support remote file systems like ftp or samba. However, thanks to the FUSE technology, there exists some powerful programs able to mount remote servers to local directory. Among them, curlftpfs, sshfs, and fusesmb can fulfill the requirement of many users.
Undortunately, the don't have a good GUI frontend, so... Let's make one.

The main window:
[img]http://pcman.sayya.org/remote-fs-man/screenshot.png[/img]

Config dialog:
[img]http://pcman.sayya.org/remote-fs-man/screenshot2.png[/img]

Detailed info: [http://www.gnomefiles.org/app.php/RemoteFSMan](http://www.gnomefiles.org/app.php/RemoteFSMan)

GUI frontend for FUSE-based remote file system
 
RemoteFSMan - Remote File System Manager

This is a user-friendly GUI frontend for curlftpfs and other remote file system using FUSE.

Through this simple user interface, you can easily mount a remote FTP site to your local directory.

Currently only FTP and FTPS are supported, but Samba and SFTP will be added in the future.

The SFTP support is almost completed, but there is a big problem I don't know how to solve. Anyone interested in this little tool please help me.
 
Requirements
This application requires GTK+ version 2.6.x. Other dependencies include:
python-gtk python-glade fuse curlftpfs
 
  Latest Version: 0.1
Initial release as a proof of the concept.
There are many great FUSE-related tools, but they lack a GUI frontend, and make them not user-friendly.

RemoteFSMan tries to help the users using them without knowing too much detail.

The program is still a over-simplified prototype, but in the future it will be able to support samba and sftp based on FUSE technology.

---

### Post by xslumlordx on 2008-10-08
This would be a great tool for me-

I'm a web developer and often need to access many (5-10) different servers simultaneously, and to connect & disconnect quickly FUSE works sort of, but the Nautilus implementation doesn't mount the remote system to a folder so most apps cant browse to it. 

This remote-fs-man looks like it would fit the bill perfectly but it needs completion! 

'afuse' looks like the backend counterpart to this GUI; maybe someone could pull from both of them and have a working package without too much time/trouble...

---

