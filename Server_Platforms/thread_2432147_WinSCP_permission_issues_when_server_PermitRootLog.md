---
title: "WinSCP permission issues when server PermitRootLogin NO"
date: 2019-11-27
forum: Server Platforms
---

### Post by aljames2 on 2019-11-27
I can Login to the Ubuntu server from WinSCP using authentication key, however once logged in permissions do not allow access to all storage folders.  I suspect it's because my ssh config file does not permit root login.  Is there a way to switch to root user from within WinSCP after log-in?  I can't imagine that the recommended usage here is PermitRootLogin Yes?  Trying to push files to storage server.  

Linux --> Linux = easy.  However,  getting old files off older windows NTFS disks, having to figure out the WinSCP

---

### Post by TheFu on 2019-11-28
scp permissions are limited to the permissions in the directory for the userid that is used for the connection.  These are normal Unix-style permissions, so you can make them be whatever you want.  However, if you override normal permissions for existing directories, then it is likely those changes will lead to being hacked if any normal network service is involved  like http or ftp.

Any Unix permissions tutorial will explain the file & directory permissions model for Linux.  umask, chmod, chown are the normal tools to manage permissions.

If you have used samba/cifs previously, those tools have a different method of dealing with permissions outside the standard Unix model.

On Ubuntu, permitrootlogin shouldn't be enabled without multiple other conditions like with keys and restricted to specific IPs.

If you show exact permissions for exact files, someone might have specific guidance.  Often, media files need to be readable by a media player program running under a different account, for example.  If you want that software to have delete capabilities, then rw on the directory is necessary for the group that the media center userid runs using.

---

### Post by LHammonds on 2019-11-29
Instead of opening up Linux for systems that are going away, why not go the other way around?

Setup Windows to access its shares (HINT: As administrator, you already have full-drive access thru the C$, D$, E$, etc. shares)

Then use [CIFS to mount the Windows share from Linux](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p631).  You can then transfer the files with all the Linux tools available to you.

LHammonds

---

### Post by aljames2 on 2019-11-29
Thanks for the help.  I can see now how the two methods can work.  I lean to using Linux to pull the data from the windows machine using CIFS and therefore no need to mess with permissions on the Linux side.

---

### Post by aljames2 on 2019-12-16
Thanks again.  I got both methods set up and working.  My problem with WinSCP was my mistake, I guess.  The mountpoint (parent directory) of the storage HDD permission was set to 0700, while all the child directories 0755.  Not sure how the 0700 came to be as I don&#8217;t mess with permissions to force things to work, or not work, in this case.  I used the find command to check all directory permissions in the tree and fixed the one directory.

---

