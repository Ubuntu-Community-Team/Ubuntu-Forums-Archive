---
title: "ssh AllowGroups wierd problem"
date: 2009-08-13
forum: Server Platforms
---

### Post by cdenley on 2009-08-13
Either this is a pretty serious bug, or I'm doing something very stupid. I had previously used "AllowGroups admin" in /etc/ssh/sshd_config to restrict ssh logins to only admin users. Now, no matter how I change that line, it still allows only admin users. I cannot change this setting.
```

cdenley@www:~$ grep AllowGroups /etc/ssh/sshd_config
AllowGroups sshusers
cdenley@www:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
cdenley@www:~$ id test1
uid=1002(test1) gid=1005(test1) groups=1005(test1),110(admin)
cdenley@www:~$ id test2
uid=1003(test2) gid=1006(test2) groups=1006(test2),1007(sshusers)
cdenley@www:~$ ssh test1@localhost
test1@localhost's password: 
Linux www.mydomain.com 2.6.24-19-server #1 SMP Wed Jun 18 14:44:47 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu Aug 13 13:35:28 2009 from mydomain.com
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

test1@www:~$ exit
logout
Connection to localhost closed.
cdenley@www:~$ ssh test2@localhost
test2@localhost's password: 
Permission denied, please try again.
test2@localhost's password:

```

version 1:4.7p1-8ubuntu1.2
ubuntu 8.04

EDIT:
I tried purging openssh-server, reinstalling, keeping the default config with no AllowGroups option, and it still allows only admin users!

---

### Post by cdenley on 2009-08-13
I figured it out. Even after purging and reinstalling openssh-server several times, it was still running and using the original configuration file. I had to stop it, find the process, kill it, then start it again. It seems to restart fine now, and is finally using the new configuration. I'm not sure if it is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/220272"), because I never received any error message.

---

