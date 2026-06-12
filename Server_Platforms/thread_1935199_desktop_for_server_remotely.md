---
title: "desktop for server remotely?"
date: 2012-03-03
forum: Server Platforms
---

### Post by jcroyle on 2012-03-03
hey everyone,  iam looking for a way to access my ubuntu server remotely but use the desktop on my computer to view it if possible.  currently i use ssh and ftp but i would like to access the server remotely and be able to view it with my gnome desktop from my laptop if possible is this possible?

---

### Post by volkswagner on 2012-03-03
Please describe what you mean "view it".  

What don't you like about the ssh option?  

Is your server running a desktop environment, or is it command line only?  Do you want to be able to run graphical programs running on your server from you laptop?

---

### Post by jcroyle on 2012-03-03
i would like to be able to navigate the server with nautilus or some other gui file manager if possible i love ssh but it would be nice if i could just cut and paste files and view .html graphically with kompozer or a web browser

---

### Post by volkswagner on 2012-03-03
Depending what version you are running on your workstation you can connect to a graphical file browser session using ssh/sftp/nautilus.

From you workstation open nautilus and choose "connect to server" you will choose ssh as the protocol and enter server info and user info.

This approach works great for drag and drop of remote files and simple opening/edit of files.

---

### Post by codemaniac on 2012-03-03
[https://help.ubuntu.com/community/VNC/Clients](https://help.ubuntu.com/community/VNC/Clients)

---

### Post by spynappels on 2012-03-04
+1 for Volkswagner's suggestion. 
In Unity you can click on the Home folder in the Launcher and then click on File in the top menu bar and select "Connect to Server" Option. You then select SSH as VW said.

---

### Post by jcroyle on 2012-03-05
thanks thats exactly what i was looking for i appreciate all the help

---

