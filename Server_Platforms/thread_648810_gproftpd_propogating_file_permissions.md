---
title: "gproftpd propogating file permissions"
date: 2007-12-24
forum: Server Platforms
---

### Post by sideburnie on 2007-12-24
I've setup gproftpd, and I'm having trouble letting it browse to sub folders of my home directory.  The folders are owned by a root level user, but anonymous read is set for all of them.  No matter what I do, I get a 550 permissions error whenever I try to browse to a sub-folder in my home folder.  

Do I need to specifically add permissions for the subfolders of the home directory into gproftpd?  

Is there any way to propogate all the file permissions that I set in gproftpd to all the subfolders of my home folder?  

ergggg..... frustrated..... haven't had troubles setting up 4 other ftp servers in windows...... sigh....:confused:

---

### Post by freebeer on 2007-12-24
I'm not expert, but maybe I can point you in the right direction...

typically, an ftp service is run under a user or group with "ftp-user" permissions (you're free to call it whatever you want).  So "fred" logs in and is a member of "ftp-user".  The permissions of the root ftp directory should be that of "ftp-user".  Subsequent folder creations should inherit the root folder's permission and/or that of the folder creator (you can control this with the config file and, I believe, the "sticky bit").  

Linux allows you great flexibility, but with that can come greater complexity.

---

