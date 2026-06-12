---
title: "chmod &amp;chown su and open-ssh"
date: 2011-03-09
forum: Security
---

### Post by ianc1 on 2011-03-09
Hi all

Looking at improving the security on my machine and reading [http://ubuntuforums.org/showthread.php?t=1002167](http://ubuntuforums.org/showthread.php?t=1002167) and [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/).
Both are very similar and suggest to do the following:
```
sudo chown root:admin /bin/su
sudo chmod 04750 /bin/su
```I can't see why this is any better than the standard permissions I have:
```
-rwsr-xr-x 1 root root 31060 2011-02-14 22:12 /bin/su*
```This has been asked in the past with no conclusive answer [http://ubuntuforums.org/showthread.php?t=732395](http://ubuntuforums.org/showthread.php?t=732395).

Secondly I don't SSH to anything, haven't installed open-ssh and therefore do not have a /etc/ssh/sshd_config file.  Am I safe to assume therefore that I don't need to install open-ssh simply to get the file and set "PermitRootLogin no"?  Or does doing so make my machine safer.

I should point out I am the sole user of the PC and as far as I am aware am not permitting anyone to SSH to it.  If I try ssh localhost I get the error "local port 22: Connection refused".

Thanks in advance.

---

### Post by ianc1 on 2011-03-13
After reading a bit more a see that the /etc/ssh/sshd_config file is actually provided by  openssh-server, but I'm still none the wiser.

---

### Post by Lars Noodén on 2011-03-14
> **ianc1 said:**
> After reading a bit more a see that the /etc/ssh/sshd_config file is actually provided by  openssh-server, but I'm still none the wiser.

What are you trying to do or solve?  Try rephrasing your question.

---

### Post by BkkBonanza on 2011-03-14
The permissions on your ls output for su indicates it is executable by **any** user. The chmod command you indicated will make it executable only by root (and admin group), not **any** other user. It's important because su has the sticky bit set and hence when it runs it runs as root even when started by any user. However, it's known to be "safe" - the advice given is just to make it more safe by restricting it to the admin group. 

You can use the **sudo netstat -lntp** command to check what ports are being listened on. If you don't have openssh-server installed then it can't possibly be listening on a port and port 22 should not show up in the output from this command. When the ssh server isn't installed the contents of the sshd_config file are meaningless (as far as I know).

---

