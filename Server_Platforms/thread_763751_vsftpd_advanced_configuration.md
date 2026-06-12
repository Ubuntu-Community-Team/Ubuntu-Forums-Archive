---
title: "vsftpd advanced configuration"
date: 2008-04-23
forum: Server Platforms
---

### Post by matic123 on 2008-04-23
Hi, 

i have gutsy server running for some time (www+ftp). I have recently installed vsftpd for ftp server. The vsftpd in running fine and it's fully operational. I have created directory structure  in /home/ftp and defined user rights using ACL. All users (=5) are chrooted in that directory except mine for administrative purposes.

My questions are: 
1. can i create another directory (e.g. /home/ftp1) and chroot another 2 users (different from above) in?
2. can i create directory for "guests" accessing only one directory (sort of public)

Thanks, Matic

---

### Post by Fatjoint on 2008-04-23
> **matic123 said:**
> Hi, 

i have gutsy server running for some time (www+ftp). I have recently installed vsftpd for ftp server. The vsftpd in running fine and it's fully operational. I have created directory structure  in /home/ftp and defined user rights using ACL. All users (=5) are chrooted in that directory except mine for administrative purposes.

My questions are: 
1. can i create another directory (e.g. /home/ftp1) and chroot another 2 users (different from above) in?
2. can i create directory for "guests" accessing only one directory (sort of public)

Thanks, Matic

If I remember right, you can chroot them to their home directories, which means if you create a new account, and you don't want them to exist in the normal /home tree, you change their home directory in their user profile.

---

