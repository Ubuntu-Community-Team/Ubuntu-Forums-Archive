---
title: "ssh question 2"
date: 2013-10-03
forum: Server Platforms
---

### Post by remo2 on 2013-10-03
Which command to start the X tunneling sell: with?
When writing prompt on the remote machine (X-tunneling after) nautilus, what folder is displayed?
Can that window to browse folders on the local machine?
If you start locally another nautilus program, so you can copy the folders from one window to another?
Where's the plane X-tunneling launched the Nautilus program is run and where the plane window is displayed?

---

### Post by Lars Noodén on 2013-10-03
When you forward X you connect with **-X**.  It should connect to your home directory, the one on the remote machine.  Try [pwd](http://manpages.ubuntu.com/manpages/raring/en/man1/pwd.1posix.html) once you have connected.

```

ssh -X user@someserver.example.org

```

There you can run programs on the remote machine, but the display will be on your local machine.  So you could run Nautilus on the remote machine and manipulate files there.  But you cannot move files between the remote machine and the local machine that way.  

No graphical programs on the remote machine access your local machine, but there two easy ways to transfer files.  To transfer files, you could run FileZilla, but you could also use Nautilus.  If you start Nautilus locally on your machine, press ctrl-L and then enter the URI for the remote server:  **sftp://user@server.example.org/**

---

### Post by JnPson on 2013-10-03
You could also use Remmina to create a SFTP-Secure File Transfer. (depending on if you are on linux or windows) From there you could connect to download and upload files to your server with any big hazel.

---

