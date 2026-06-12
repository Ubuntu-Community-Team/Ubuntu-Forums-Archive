---
title: "how to refuse accessing parent directory in FTP client program?"
date: 2010-02-18
forum: Server Platforms
---

### Post by programming.name on 2010-02-18
Hi, I am runnung ubuntu  9.10 desktop edition as a server. I am using a FTP client program 

to upload some files(index.html, background.png, etc) and everything is fine with that. And 

currently all my files are in /home/myname/ folder. What I want is  whenever I log in with 

my ubuntu account in the FTP client program, I can actually see the list or contents of the 

very root  directory. In other word, I can see every folder like /bin, /boot, /etc, /root, so 

on in the FTP software and I can download it. I don't want to allow to access the parent(or 

root) directory. Is there any possible way to set up the sutff?

Thanks in advance.

---

### Post by bluefrog on 2010-02-18
use sftp and restrict it.

edit /etc/ssh/sshd_config
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
UsePAM yes
Match User user (can use Group group-name if you wish)
ChrootDirectory %h
ForceCommand internal-sftp

Users listed there will be able to sftp only and will be chrooted to their home

---

### Post by mbehamin on 2010-02-18
i think the best way for you is using file permission. just remove read permission from the upper directory from others.
i haven't tested yet but it should be works

---

