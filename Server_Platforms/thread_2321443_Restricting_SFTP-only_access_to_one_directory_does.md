---
title: "Restricting SFTP-only access to one directory does not work."
date: 2016-04-22
forum: Server Platforms
---

### Post by stefan_03 on 2016-04-22
Hello,

I would like to restrict the access of one SFTP user to one directory. SSH should not be allowed, only file exchange via SFTP.

I read many articles/instructions like
[https://passingcuriosity.com/2014/openssh-restrict-to-sftp-chroot/](https://passingcuriosity.com/2014/openssh-restrict-to-sftp-chroot/)
[http://stackoverflow.com/questions/23099860/create-a-sftp-user-to-access-only-one-directory](http://stackoverflow.com/questions/23099860/create-a-sftp-user-to-access-only-one-directory)
[http://askubuntu.com/questions/598870/limit-sftp-user-access-to-specified-directory](http://askubuntu.com/questions/598870/limit-sftp-user-access-to-specified-directory)

I created a user userftp, and a group ftp. The user is in the group (I already double-checked that)

None of my attempts worked, and I have an assumption why it is. This is my /etc/ssh/sshd_config file:

```
UsePAM yes

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp


Match Group ftp
    ChrootDirectory %h
    ForceCommand internal-sftp
    AllowTcpForwarding no
    PermitTunnel no
    AllowAgentForwarding no
    X11Forwarding no

```

When I comment out the **ChrootDirectory %h** part, I can log in, but there is no restriction in directories. When this line is active, I cannot log in.

FileZilla:
```
Response:	fzSftp started, protocol_version=2
Command:	open "user@mydomain.com" 22
Command:	Pass: *******
Error:	Connection reset by peer
Error:	Could not connect to server
```

I cannot find anything in **/var/log/syslog** about it. I think the error is in the ChrootDirectory line, but I cannot figure out why.

Can anybody help me? (Ubuntu 14.04 server)


Thanks!

---

### Post by nerdtron on 2016-04-23
What is the default shell that you used for the "userftp"? And did you set proper permission for it's home folder?

This is my notes that I used when I set a sftp chroot environment. Although it is for CentOS, it should also work for Ubuntu since it's just normal user account creation with a few edits.
[http://www.masterkenneth.com/sftp-server-with-chroot-setup-centos-6-rhel-6/](http://www.masterkenneth.com/sftp-server-with-chroot-setup-centos-6-rhel-6/)

---

### Post by stefan_03 on 2016-04-23
Thanks for your reply. No shell, I tried with nautilus and filezilla. 
I don't think it's a permission problem. It's set to 755, owner is the userftp in group ftp. It wouldn't work without the comment before the Chroot command either, if there was a permission problem. I don't even know why I have to use that command. I just want to restrict the user on one single directory.

Thanks also for the link!

---

