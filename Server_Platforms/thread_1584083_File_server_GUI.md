---
title: "File server GUI"
date: 2010-09-28
forum: Server Platforms
---

### Post by zeemer6 on 2010-09-28
I wanted to set up a small file/print server using Ubuntu.

I'm planning on using a spare nano ITX board running C7 processor with 2GB and an 80GB drive for right now.

I've set up desktop and systems and like using KDE.

I've read installing KDE and X Server and have had problems running on 10.04. 

I can run command line but wanted to know if there are there any good GUI programs that are reasonably easy to install on server 10.04?

---

### Post by rcayea on 2010-09-28
May I ask for clarification? GUI to do what?

---

### Post by arrrghhh on 2010-09-28
GUI programs to install Ubuntu Server...

Perhaps you shouldn't be running Ubuntu Server.  Honestly.  No offense - if you're comfortable with the GUI, then use it - grab a copy of Ubuntu-Desktop, and you'll see a friendly GUI for the entire setup.

With that said, if you do go the server route there are some GUI tools that facilitate setting up Ubuntu after the fact - for example you can configure CUPS (print server) with Webmin - web-based interface for configuring Linux basically.

So if you're not comfortable with cli, just go for Ubuntu Desktop.  You can run the exact same services on it, and you don't have to worry about trying to fit a square peg into a round hole by installing X and Gnome and/or KDE on your server.

---

### Post by memilanuk on 2010-09-28
[http://www.turnkeylinux.org/fileserver](http://www.turnkeylinux.org/fileserver)

Downloadable as a VM image or as an ISO suitable for booting and installing from.  Comes with a stripped-down version of Webmin (all the extraneous modules that don't pertain to being a file server are removed) - short-n-sweet and to the point.

HTH,

Monte

---

### Post by CharlesA on 2010-09-28
> **arrrghhh said:**
> GUI programs to install Ubuntu Server...

Perhaps you shouldn't be running Ubuntu Server.  Honestly.  No offense - if you're comfortable with the GUI, then use it - grab a copy of Ubuntu-Desktop, and you'll see a friendly GUI for the entire setup.

With that said, if you do go the server route there are some GUI tools that facilitate setting up Ubuntu after the fact - for example you can configure CUPS (print server) with Webmin - web-based interface for configuring Linux basically.

So if you're not comfortable with cli, just go for Ubuntu Desktop.  You can run the exact same services on it, and you don't have to worry about trying to fit a square peg into a round hole by installing X and Gnome and/or KDE on your server.

+1.

> **memilanuk said:**
> [http://www.turnkeylinux.org/fileserver](http://www.turnkeylinux.org/fileserver)

Downloadable as a VM image or as an ISO suitable for booting and installing from.  Comes with a stripped-down version of Webmin (all the extraneous modules that don't pertain to being a file server are removed) - short-n-sweet and to the point.

HTH,

Monte

That one sounds good as well.

---

