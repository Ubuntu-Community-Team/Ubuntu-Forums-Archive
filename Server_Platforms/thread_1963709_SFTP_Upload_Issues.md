---
title: "SFTP Upload Issues"
date: 2012-04-22
forum: Server Platforms
---

### Post by danielsgroves on 2012-04-22
Hi,

I have created a new VirtualHost on my server and given ownership of all files to another user, this user has permission 775 on the directory and everything within it.  However, when the user tries upload files more than a few kb the file transfer will not initiate. 

The user can create files, folder and upload small files but larger files such as images will not upload. 

The server is running Ubuntu 10.04 and OpenSSH.  

Does anyone have any ideas as tot he cause and how to solve this?  I can only guess that this is due to a file size limit somewhere, but cannot find any in the ssh_config and sshd_config files, unless I'm blind.  

Thank you in advance for your help,

Daniel Groves

---

### Post by kevinthecomputerguy on 2012-04-23
Is there a disk quota in place, or maybe a small partition that's running out of space.

Can the user SCP without issue ?

If all that checks out, try testing the ram

---

### Post by danielsgroves on 2012-04-23
Hi Kevin,

Thanks for your reply.  I'll check if the user can SCP as soon as they come online.  

Their are no active disk quotas in place, how do you mean to check the RAM?  I cannot physically touch is as I am dealing with a VPS hosted at [prgmr]("http://prgmr.com").  

Dan.

---

### Post by kevinthecomputerguy on 2012-04-23
Never mind on checking the ram then.
Are large http downloads fast, how about plain ftp? any better
-Kevin

---

### Post by danielsgroves on 2012-04-23
Hi Kevin,  

Thank you for your help, after speaking with the account owner a fix has now been found, it seems that a quick reset of their router was all that was required - something I assumed they had already tried.  

Thank you for your time. 

Dan.

---

