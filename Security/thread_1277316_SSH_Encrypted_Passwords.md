---
title: "SSH Encrypted Passwords"
date: 2009-09-28
forum: Security
---

### Post by bacterozoid on 2009-09-28
This feels like a silly question to ask, but I want to cover my bases. I've installed openssh-server on my Ubuntu box and can SSH into it from any computer with no trouble. I can also edit files with no problems. I'm trying to use a program called MacFUSE on my iMac to mount my Ubuntu machine as an "SSH Filesystem" which should work no problem.

In short, I'm getting "Error -36" on the mac when I try to perform any file operations (copy, save, etc) which has been suggested to me that it means my SSH server doesn't support sending of encrypted passwords. Is this true? Can I verify or change this?

Thanks!

---

### Post by scorp123 on 2009-09-28
> **bacterozoid said:**
> Can I verify or change this?
 And why don't you simply post your sshd_config file? 

```
sudo cat /etc/ssh/sshd_config
```

Then we will see what is configured or not.

---

### Post by cdenley on 2009-09-28
What file operations are you attempting to perform? Are you sure you have the correct permissions?

---

### Post by undecim on 2009-09-29
Can you see the list of files on your ssh file system? If so, that means you are logged onto ssh, and its not a password problem. As the posts above me have stated: 1) Post your /etc/ssh/sshd_config and 2) Make sure you have appropriate file permissions.

Also, try accessing files via sftp from another program or computer (FileZilla does sftp, or if you are on an Ubuntu machine, you can just use the "Connect to Server..." app from the "Places" menu)

---

