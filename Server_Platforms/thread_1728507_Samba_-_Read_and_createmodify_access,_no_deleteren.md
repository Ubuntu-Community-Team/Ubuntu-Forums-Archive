---
title: "Samba - Read and create/modify access, no delete/rename"
date: 2011-04-13
forum: Server Platforms
---

### Post by sdobz on 2011-04-13
I have an Ubuntu 10.10 fileserver with several samba shares set up, when accessing from windows 7 I can create and modify files, but I cannot rename or delete them.

What I am trying to do is have my www directory accessed by samba through the user media. This is to get around the limitation that only one user can be logged into a share at once. I do this by letting media log in through samba, then force-usering to www-data

Here is all of the relevant information I can think of:

```
$ cat /etc/issue
Ubuntu 10.10
$ smbd -V
Version 3.5.4
$ id media
uid=1007(media) gid=1007(media) groups=1007(media),1008(dl)
$ id www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
$ ls -l
drwxr-xr-x  3 www-data www-data 4096 2011-04-12 14:23 www
$ ls -l www
-rw-r--r-- 1 www-data www-data    0 2011-04-11 18:50 index.html
-rw-r--r-- 1 www-data www-data    0 2011-04-13 16:43 New Text Document.txt
$ sudo smbpasswd -e media
Enabled user media.
$ sudo smbpasswd -e www-data
Enabled user www-data.

```

smb.conf
```

[global]
	realm = MYHOSTNAME.MYDOMAIN.NAME
	security = SHARE
	load printers = No
	create mask = 0644
	force unknown acl user = Yes

[www]
	path = /var/www/
	username = media
	valid users = media, www-data
	force user = www-data
	force group = www-data
	read only = No

[media]
	path = /var/data/media
	username = media
	valid users = media
	write list = media

```
(media is another share, and works fine)

The file "New Text Document.txt" was created through samba by right clicking > New > Text Document

When I try to delete it:
[img]http://i.imgur.com/7CSzt.png[/img]

The windows 7 security page:
[img]http://i.imgur.com/ZTiXo.png[/img]
(Everyone and www-data have only read)

I have several other shares, some of them are configured in the same way and exhibit the same errors, and some are configured differently and work just fine.

Have I left anything off?

Now I'm off to figure out why sabnzbdplus is failing to start after the most recent upgrade.

---

