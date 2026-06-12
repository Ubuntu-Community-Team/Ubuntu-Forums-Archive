---
title: "how to best upload files for web page"
date: 2008-04-17
forum: Server Platforms
---

### Post by darinwc on 2008-04-17
I've putzed around with linux before, but now I am working with it in ernest. I installed a ubuntu 7.10 server edition. I have SSN, Apache, and Mysql running. I am having a problem getting Samaba to work in a secure manner though. Share access is working fine but i cant get the users to work.

Question: what is the generally accepted method of uploading files for the web site?  Since I am having trouble with samba would it be better to use FTP or login through SSH and use wget?

Also, while it is interesting learning bash and vi, it seems it would be much easier for me to use webmin or cpanel or something but since this server may eventually go public, im not sure i want to tempt the fates. what do you guys think?

---

### Post by tubezninja on 2008-04-17
I typically use sftp for uploading files to my web server from remote locations.  I can edit my files locally using my text editor of choice, then just sftp in to my web directory and upload what I need.  For quick changes, I've found that nano is a good quick and dirty text editor for making quick changes to files while logged into the shell (I too, can't find my way around vi very well).

As for a GUI, a lot of people here recommend against it.  I have found that I can get by pretty easily with just ssh.  If you really want a gui/web based server admin interface though, you might want to wait for for the next version of ubuntu which comes out just next week.  There's an eBox web-based admin package for it that looks very promising:

[http://packages.ubuntu.com/hardy/ebox](http://packages.ubuntu.com/hardy/ebox)

---

### Post by analoog on 2008-04-17
> **darinwc said:**
> I
Also, while it is interesting learning bash and vi, it seems it would be much easier for me to use webmin or cpanel or something but since this server may eventually go public, im not sure i want to tempt the fates. what do you guys think?

make a test-server or use an virtual machine to find out what you like. Ofcourse bash/vi is are much more powerful tools, you can do practically anything with a (good) shell and a text editor (and root axx haha).

Ofcouse some panels can greatly help you, by making tasks a lot easier or doing things automatically for you.. no-one can decide what fits the best for you..

FTP isn't the best idea since it sends the user/pass in clear text. 
You can also transfer files via ssh. For a client that supports this use gFTP. 
For windows use WinSCP,
Also don't set the ssh on port 22, and don't have weak passwords!

---

### Post by wormser on 2008-04-17
If you are looking for an easy GUI way, then use the Connect to Server feature under Places.  Select ssh as the connection option.  It will create a folder on your desktop to the remote server.

---

