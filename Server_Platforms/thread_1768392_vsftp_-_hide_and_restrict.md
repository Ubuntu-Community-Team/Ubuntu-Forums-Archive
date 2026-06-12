---
title: "vsftp - hide and restrict"
date: 2011-05-26
forum: Server Platforms
---

### Post by Jonny87 on 2011-05-26
Ok so I've for both of these I've tried looking them up and following the Ubuntu Server guide but still can't get them working. What I'm having trouble with is;

[LIST=1]
[*]Restricting users to there home dir so that they can't view other ppls homes.
[*]Hiding all hidden files (.*) so that they can't be seen when the server is accessed from a MS Windows machine.
[/LIST]
Can any one assist with these, the first (for obvious reasons) is the main priority.

---

### Post by Lars Noodén on 2011-05-27
> **Jonny87 said:**
> 
[LIST=1]
[*]Restricting users to there home dir so that they can't view other ppls homes.
...
[/LIST]
Can any one assist with these, the first (for obvious reasons) is the main priority.


The first step is to drop FTP.  VSFTP is a server for FTP, what you need instead is [openssh-server](http://packages.ubuntu.com/natty/openssh-server) and it will give you SFTP automatically.

From there [chroot](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads) some of the accounts to their respective home directories.  

1. make a group (e.g. sftponly)
2. add the users you want to lock down into that group
3. edit sshd_config to lock down that group so that it's members can only access their own home directories

```

# from /etc/ssh/sshd_config
Subsystem sftp internal-sftp

Match Group sftponly
        ChrootDirectory %h
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

4. restart the openssh-server so that the configuration changes take effect

In all, that should take less than [five minutes](http://ubuntuforums.org/showthread.php?t=1057657).

---

