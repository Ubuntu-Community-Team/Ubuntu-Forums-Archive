---
title: "Backup"
date: 2010-03-03
forum: Server Platforms
---

### Post by lushinga on 2010-03-03
I'm new on the linux platform and need your help. I'm trying to backup folders from my MS windows xp to the Red hat linux enterprise 5 server that is on the same network with the Pcs. Can any one help with the commands I need to use or procedure that i should follow.

---

### Post by lushinga on 2010-03-03
I'm new on the Red Hat Linux Enterprise 5 and seek your help. I'm trying to back up my folders from the PCs running MS windows xp. I want to back them on the server and these PCs are on the network with the linux server.

---

### Post by richardjh on 2010-03-05
Install and configure Samba on the Linux Server, see this guide here:
[http://centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-configuring.html](http://centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-configuring.html)

Create a Share on a directory (I use /home/shared/backups)

On each Windows XP client, map the Share on the server to a drive (I use Y:)

Use the built in XP Backup utility to backup to the Y: drive at the end of each day.
On the Linux server, use rsnapshot to take snapshot backups of the /home/shared/backups directory to another such as /var/backup so you can recover deleted or lost files.

Alternatively write a script that compresses and copies the /home/shared/backups directory to removable storage and rotate frequently.

---

### Post by richardjh on 2010-03-05
This problem is very similar to the exact same post you made [here]("http://ubuntuforums.org/showthread.php?t=1420598").

---

### Post by cariboo on 2010-03-05
Please don't create multiple threads on the same subject. I have merged your two threads

---

### Post by HermanAB on 2010-03-06
Do yourself a favour - install Cygwin on Windows and use Rsync to make backups of your data.

---

### Post by johnson.d on 2010-03-08
You can probably connect to the Windows XP machine using Samba. This can be done by using the following procedure:

1) Goto Gnome Menu-> Places-> Connect to server
2) Service type -> Windows share
3) Enter the details of the windows server

Now you can connect to the Windows Machine and take backup. For further queries based on Red hat Enterprise Linux you can contact Red hat support.

---

