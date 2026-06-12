---
title: "Looking for advice setting up safe ftp server"
date: 2008-07-31
forum: Server Platforms
---

### Post by msmarc on 2008-07-31
I've installed ubuntu hardy server edition and wanted some advice on how to set up an ftp server thats safe and reliable.

I wanted the user names to be setup through mysql following this guide:
[http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04](http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04)

I also found a guide that taught how to mount an ftp server as a separate filesystem and was possibly interested in doing this. What would be the benefits or negatives of this type of setup?

My main concern is how to setup the groups and users. Before I screwed up the permissions in my var folder.  I want to separate groups of ftp users that would start in separate directories: musictransfer and filetransfer(would be jailed in). I also want one user (myself) to be able to navigate and have permissions in both the above directories as well as the /var/www directory.

I also eventually wanted to set up ftp for the /var/www folder so I could upload files to my apache server. Here I would want separate directories that could be accessed by people in another group called "www". This would be separate from the other stuff as it would be ftp for websites and not general file transfer.

Whats the best way to setup up the users and groups to accomplish this? Wheres a safe location to set everything up? the home folder? Any advice and help greatly appreciated.

---

