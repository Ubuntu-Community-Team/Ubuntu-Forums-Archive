---
title: "Setup a file sharing server in Ubuntu (Server) using VMware"
date: 2009-01-14
forum: Server Platforms
---

### Post by Krydox on 2009-01-14
Hi, I'm trying to setup a file sharing server using Ubuntu or Ubuntu Server edition and setting up 1 client for it, also Ubuntu. This all in a virtual network, VMware.

First of all I would like to know: Is this even possible in a virtual network?
And what should OS should I use, I realize that I probably need to use Samba, but I'm not familiar with that, so i'm wondering if the Server edition is even necessary.

---

### Post by spiderbatdad on 2009-01-14
yes this is possible and not difficult, though of course if ths is your first attempt, there is will be a learning curve...don't be in a hurry, is my best advice.
Ubuntu is an awesome OS and is ideal for what you are interested in doing. You can use a number of tools for file sharing. Openssh-server is a great way to access your server machine and implement scp and sftp...you will also find a GUI "connect to server" on your client machine under the Places menu. There you can literally mount the server file system in a directory on your desktop. Apache is another great way to host an index of directories and files for easy access via a web browser. There are simple php applications for uploading to the server remotely. Some links to help you get started.

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/7.10/server/C/openssh-server.html](https://help.ubuntu.com/7.10/server/C/openssh-server.html)

---

