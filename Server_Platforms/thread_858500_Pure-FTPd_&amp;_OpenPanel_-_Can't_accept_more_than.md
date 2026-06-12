---
title: "Pure-FTPd &amp; OpenPanel - Can't accept more than 3 connections as the same user"
date: 2008-07-13
forum: Server Platforms
---

### Post by Wubuntish on 2008-07-13
I've searched on google and IRC with no results. I don't know if it's a bug, so I decided to ask here for help.

I recently installed OpenPanel on a Ubuntu 8.04 Server. Everything worked out of the box with no issues. However, when I try to connect to the server using FTP, I tend to get disconnected after a few minutes. (I use Gnome-VFS and OpenKomodo for working with PHP applications) I had to wait at least 15 minutes before being able to work again.

So, I tried connecting to the server using the FTP terminal program. While logging in, I get the following message:

```
421 I can't accept more than 3 connections as the same user
```

It had to be a configuration problem. So, I look in my /etc/pure-ftpd folder without finding a real configuration file. After a little reading I found out that Pure-FTPd only uses commandline options, and optionally, a wrapper for using configuration files.

In the /etc/pure-ftpd/conf folder, I've got the following files with the corresponding contents:

[LIST]
[*]AltLog => clf:/var/log/pure-ftpd/transfer.log
[*]MinUID => 1000
[*]PerUserLimits => 100 100
[*]MaxClientsNumber => 1000
[*]MaxClientsPerIP => 100
[*]NoAnonymous => yes
[*]PAMAuthentication => yes
[*]PureDB => /etc/pure-ftpd/pureftpd.pdb
[*]UnixAuthentication => no
[/LIST]

When restarting the daemon I get the following:

```
root@*hidden*:/etc/pure-ftpd/conf# /etc/init.d/pure-ftpd restart
Restarting ftp server: Running: /usr/sbin/pure-ftpd -l pam -l puredb:/etc/pure-ftpd/pureftpd.pdb -u 1000 -E -c 1000 -y 100:100 -O clf:/var/log/pure-ftpd/transfer.log -C 100 -B
```

That looks alright to me. However, when I try to connect more than three times, the server still rejects my connection with the exact same message.

Thanks a lot for your time!

---

