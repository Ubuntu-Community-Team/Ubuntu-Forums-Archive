---
title: "FTP program ?"
date: 2006-07-07
forum: Server Platforms
---

### Post by ThaDoctor99 on 2006-07-07
I need a FTP program so I can upload to my website.
I just dont know where to look for it yet, can any one hlep me on this matter ?
:-)


greetings Tobias

---

### Post by kewldude606 on 2006-07-07
Are you looking for a client or a server?  A client runs on your computer and lets initiate uploads and downloads files from a server.

It sounds like you want a client.  Here's a guide for using Nautilus, the default file manager for Ubuntu, as an FTP client: [http://ensode.net/ftp_gnome_nautilus.html](http://ensode.net/ftp_gnome_nautilus.html)

---

### Post by Indras on 2006-07-07
> **ThaDoctor99 said:**
> I need a FTP program so I can upload to my website.
I just dont know where to look for it yet, can any one hlep me on this matter ?
:-)


greetings Tobias

There's actually a command-line ftp program already built into nearly every Linux/Unix system just called "ftp."  From command line, type ftp and hit enter, and you'll get a prompt that looks like this:

```
ftp>
```

From the ftp prompt, you can use all sorts of basic commands.  To open a connection to an ftp server, type: ```
open ftp.servername.com
```

The server will then ask you for your username and password and log you in, from there you can use "cd" to change to a different directory, "pwd" to get your current working directory (server-side), "lcd" to change your local directory, and "get" and "put" to download and upload files between the server and your local directory.  At any time at the ftp prompt, you can type "help" to get a list of commands you can use and "help <command>" to tell you what each command does.

Now, if text-mode isn't your thing, odds are you'll have a much easier time with gFTP.  Go to Applications->Add/Remove->Internet and scroll down and click the check box by gFTP and hit Apply.  It will download and install gFTP (if it isn't already) and once it is done, you can find it under Applications->Internet->gFTP.

gFTP has an interface very similar to CuteFTP (which I used heavily in my Windows 95/98 days).  You shouldn't have any trouble navigating around in it.

---

### Post by ThaDoctor99 on 2006-07-07
I think the build in ftp will be good for sometime, until I run into something which might be hard to do this way.
:-)

---

### Post by Aurdal on 2006-07-08
sudo apt-get install gftp

---

### Post by ThaDoctor99 on 2007-03-21
Actual I like emacs + ftp 

in that way I can upload stuff to my website within the text editor, I am not very good at emacs yet but I really like that editor, it way to cool it have got everything for a whole mans life....

Greetings, and thanks for all the help.

---

### Post by stokedfish on 2007-03-21
sudo apt-get install kftpgrabber 

[http://www.kftp.org/](http://www.kftp.org/)   ;)

---

### Post by ThaDoctor99 on 2007-03-22
I like the text based ftp client way better....

---

### Post by random_mike on 2007-03-22
Firefox with "FireFTP" plugin. 

[http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

---

