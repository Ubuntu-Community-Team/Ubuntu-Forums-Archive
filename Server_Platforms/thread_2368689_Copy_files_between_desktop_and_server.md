---
title: "Copy files between desktop and server"
date: 2017-08-14
forum: Server Platforms
---

### Post by ScorpioTiger on 2017-08-14
I have Ubuntu 16.04 installed on my laptop.
I have a VPS running Ubuntu 14.04.
I have install SSHFS and created a connection that allows me to browse the remote file system on my laptop using Nautilus.
I can open a new local Nautilus window from the terminal using gksud nautilus.

What I don't seem to be able to do is copy files from the server to my laptop; I get "Error opening file: Permission denied". I can open the remote file in a text editor, so permissions to the server don't seem to be the issue.

Why is it that as a sudo user on my local machine, I cannot copy this file to my laptop? Ultimately I will be connecting to multiple remote servers and doing deployments from my local machine (which will serve as a development machine).

---

### Post by wildmanne39 on 2017-08-14
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2017-08-15
Don't use sudo.  sshfs permissions are provided by the userid who created the sshfs mount, not root.  Local root and remote root don't work. They are different accounts, completely.

In general, it is a bad, terrible, idea to use any GUI program with sudo.  It just means that an good understanding of file and directory permissions is lacking.

If you want to copy files between local and remote systems, use scp, sftp, or rsync.  These all honor use ssh and honor the ~/.ssh/config file settings.  If you need a GUI, almost any Linux-based file manager will use either the ssh:// or sftp:// URLs to connect to a remote system.   I tend to use rsync directly, so can't say which GUI file managers work or don't with those, just know that is almost always works.

There is no need to use sshfs or filezilla.  Just use caja, thunar, nautilus with ssh:// in the URL.

---

### Post by BloodyIron on 2017-08-15
One way that you can do it is to use filezilla and connect via SSH and copy to-and-fro as the user you connected with. It's not quite as convenient as nautilus, but I use it all the time!

Hope this works for you :^)

---

