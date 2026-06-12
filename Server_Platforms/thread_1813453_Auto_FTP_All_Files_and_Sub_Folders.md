---
title: "Auto FTP All Files and Sub Folders"
date: 2011-07-27
forum: Server Platforms
---

### Post by techanalyst on 2011-07-27
Ive been trying to figure out a method to upload (copy) all files and sub folders under that folder to my content delivery network, basically run it every 30 minutes.

Whats the best way to do it?  I tested a few that I was reading about, one just copied files nd not sub folders, another moved all files.

---

### Post by HermanAB on 2011-07-28
The best way?  Rsync over ssh is the best way.

$ rsync -e ssh fromyadayada user@server:/toyadayada

Read the man page.  It is a good one.

---

### Post by techanalyst on 2011-07-28
One server I have root access the other is just an ftp server, nothing else

Ive attempted about 20 different instructions sets, im getting login failures, files will all be physically moved etc, im asking for advice so i cant stop breaking everything with random advice I find on the net

---

### Post by papibe on 2011-07-29
Let's start reviewing the software (packages) you need installed for rsync over ssh can work.

On the client side (the computer on which you want to run the command itself). You need the ssh client. Post the result of this command:
```
$ dpkg -l openssh-client
```
The server, or the machine in which the files will be copied. Here you need the server side of ssh. Post the result of this command:
```
$ dpkg -l openssh-server 
```
Regards.

---

